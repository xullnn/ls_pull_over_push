What's the difference between "method invocation" and "function invocation"?

How to invoke a method in the form of function invocation?

How to define `this` in Javascript?

What's the moment when Javascript assigns a context to an expression/statement?

What's the meaning of "functions as Object factories"? How to do this in Javascript?

What is the implicit context when you run Javascript in browser? what about in `node` console?

```js
window = {
  // you are actually writing code in this previous defined context
}
```

Explain why expression like `a = 1` executed at the top level will create a global scope variable?

After we declare a function at the top level (e.g `function abc() {}`), can we delete it by `delete abc`? Why?

"Every time a JavaScript function is invoked, it has access to an object called the execution context of that function. " （像不像一个哲学追问？）

What's the difference between `call` and `apply`?

What's the basic difference between function execution context(`this`) and lexical scope in JavaScript?

When invoking a function, how to convert a passed in array to an argument list?

```js
function abc(a, b, c) {
  return a + b + c;
}

let numbers = [1,2,3];

abc(numbers) // '1,2,3undefinedundefined'
// how to fix this
```

What's the return value of a call to `Function.prototype.bind()`?

What are the 3 ways to specify context for a function execution? What's the difference?

- apply / call
- bind
- assign property


- `this` is dynamic
- `var self = this`, `self` is static

What this code snippet demonstrates?

```js
var a = 0;
var foo = {
  a: 0,
  incrementA: function() {
    function increment() {
      this.a += 1;
    }

    increment();
  }
};

foo.incrementA();
foo.incrementA();
foo.incrementA();

console.log(foo.a); // 0
console.log(a); // 3
```

What can be called 'explicit execution'?

What is a high-order function? what is a first-class function?

https://stackoverflow.com/questions/10141124/any-difference-between-first-class-function-and-high-order-function

What's IIFE? When we need it?

How will you describe the relationships among `this`, closure, IIFE?

What is a constructor function?

What would be the return value if we perpend operator `new` to a function name?

`prototype` can be called on which of these callers?
- `Object`
- `aFunction` after `aFunction = function() {}`
- `obj` after `obj = {}`

What is the end(at the top) of a prototype chain? How to improve this?

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype

What does the code below demonstrate?

```js
> var obj = { a: 1 };
undefined
> obj.prototype
undefined
> function Person(){};
undefined
> Person.prototype
Person {}
> Object.prototype
{}
```

What's the result of running the code below, why?

```js

// use Object.create()
var a = new Object();
var b = Object.create(a);
console.log(b.__proto__ === Object.getPrototypeOf(b)); // 1 expect to return true
console.log(a.__proto__ === Object.prototype); // 2  expect to return true
console.log(Object.getPrototypeOf(a) === Object.prototype); // 3  expect to return true

// --- use constructor function
var F = function() {};
var x = new F(); // returns a new object which has F.prototype as its prototype
console.log(Object.getPrototypeOf(x) === F.prototype); // 4 expect to return true
console.log(Object.getPrototypeOf(F.prototype) === Object.prototype) // 5 expect to return true
console.log(x.constructor === F); // 6 expect to true

// about Object
console.log(Object.getPrototypeOf(Object) === Object.prototyp)
console.log(Object.getPrototypeOf(Object) === Object.__proto__)
```

Can a behavior be added to an instance by adding it to the constructor Function's `prototype` after the instance has been created beforehand?

```js
function Abc() {
  this.a = function() { console.log('I am a.') };
};

var x = new Abc();
x.a() // logs 'I am a.'

Abc.prototype.b = function() { console.log('I am b.') };
x.b() // ??? Does this work?
```

What is "scope-safe constructors"?

What's the difference of `this` between these two scenarios below? Why?

```js
function aFunc() {
  this.name = 'abc';
  console.log(this);
}

// 1
aFunc();

// 2
new aFunc();
```

Explain the basic idea of the code below and how it will be used(after learning all the related concepts including function execution context and OOP, it should be not too hard to understand how the code works.)?

hint:
- identify the inheritance relationship in this case
- what does `this` mean in this case?
- what will be the caller of `bind()`?
- what args bind excepts?
- what's the return value of calling `bind()`

https://launchschool.com/lessons/c9200ad2/assignments/bb359c53

```js
Function.prototype.bind = function () {
  var fn = this;
  var args = Array.prototype.slice.call(arguments);
  var context = args.shift();

  return function () {
    return fn.apply(context, args.concat(Array.prototype.slice.call(arguments)));
  };
};
```

Insert an implicit step not shown in the code to make the reason of why `'Steve'` is not eligible for GC clearer. Then explain why?

```js
function makeHello(name) {
  // var name = 'Steve'
  return function() {
    console.log("Hello, " + name + "!");
  };
}

var helloSteve = makeHello("Steve");
```

What's the difference between the code below?

```js
// 1
function Man() {
  // this = Object.create(Man.prototype)
  // or
  // this = {}; this.__proto__ = Man.prototype;

  this.type = 'homo';
  this.walk = function() { console.log('walk') };
}

var bob = new Man();

// 2
function Man() { };
Man.prototype.type = 'homo';
Man.walk = function() { console.log('walk') };

var joe = new Man();
```

(following the previous question)How these two implementation can influence the inheritance chain?

hint:
  - if we want to set `Man` in the middle of an inheritance chain
  - `Man` in upstream
  - `Man` in downstream

What is the return value of the code below?

```js
function F() {};
F.prototype.constructor === F; //?
```

What's the return value of the code below, why?

```js
var a = {};
var b = Object.create(a);
var c = Object.create(b);

a.isPrototypeOf(c) // ?
Object.getPrototypeOf(c) === a // ?
```

Insert some code at the specified position to achieve the wanted result?

```js
var person = { name: 'Bob', age: 12 };
Object.keys(person) // [ 'name', 'age' ]

for(let proper in person) { console.log(`${proper}: ${person[proper]}`) };
// name: Bob
// age: 12
// undefined

// Insert code here -----------------------------------------

// Insert code here -----------------------------------------

Object.keys(person); // [ 'name' ]
for(let proper in person) { console.log(`${proper}: ${person[proper]}`) };
// name: Bob
// undefined

delete person.age; // false
```

How to check if a value(or object) has access to a certain property or method? Further more, how to determine if the the property or method is defined on the object itself?

`toString` in {};
`getOwnPropertyNames()`
`hasOwnProperty()`

Given the code below, answer 1) what is `sub1` and `sub2`'s `constructor`; 2) what is the value of `sub1` and `sub2`'s `property1` property; 3) what's the meaning of doing this: `subType.prototype.constructor = subType;`?

```js
function superType(a) {
  this.property1 = a;
}

function subType() {
};

subType.prototype = new superType();

sub1 = new subType();

subType.prototype.constructor = subType;

sub2 = new subType();
```

Describe the inheritance chain in the previous question, and what about this one?

```js
function superType(a) {
  this.property1 = a;
}

function subType() {
};

subType.prototype = Object.create(superType.prototype, {
  constructor: {
    value: subType,
    configurable: true,
    enumerable: true,
    writable: true,
  }
});

sub1 = new subType();

sub2 = new subType();
```
