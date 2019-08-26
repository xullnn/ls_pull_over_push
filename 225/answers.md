How to invoke a method in the form of function invocation?

- In Js, since a method is just a function as the value of an object's property, also functions are first-class value(things can be assigned and passed), so we can retrieve a method and assign it to a global variable, and invoke it as if it were a function.

How to define `this` in Javascript?

- `this` refers to the current execution context object during the evaluating of an expression or during the executing of a function.

```js
var a = 'Hello';
console.log(this.a); // logs Hello.

var b = this.a;
b; // 'Hello'
```

What's the moment when Javascript assigns a context to an expression/statement?

- When evaluating an expression/statement.
- "Every time a JavaScript function is being invoked, it has access to an object called the execution context of that function."

> In most cases, the value of `this` is determined by how a function is called (runtime binding). It can't be set by assignment during execution, and it may be different each time the function is called.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this

What's the meaning of "functions as Object factories"? How to do this in Javascript?

- "functions as Object factories" refers to the behavior that
  - define a function whose return value is an object
  - such functions can be used as template(factory) to create predefined objects

What is the implicit context when you run Javascript in browser? what about in `node` console?

- In browsers, the implicit context object is `window`; in node console, it's `global` object.
```js
window = {
  // you are actually writing code in this previous defined context
}
```

After we declare a function at the top level (e.g `function abc() {}`), can we delete it by `delete abc`? Why?

- No. According to [Mozilla doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/delete#Description):
  - Any property declared with `var` cannot be deleted from the global scope or from a function's scope.
    - As such, `delete` cannot delete any functions in the global scope (whether this is part from a function definition or a function expression).
    - Functions which are part of an object (apart from the global scope) can be deleted with delete.

What's the difference between `call` and `apply`?

- Syntax difference on the second argument they accept.

What's the basic difference between function execution context(`this`) and lexical scope in JavaScript?

- lexical scope is defined by the structure of the source code, which means the time of writing code.
- execution context `this` won't be determine until the time of executing the code.

When invoking a function, how to convert a passed in array to an argument list?

```js
function abc(a, b, c) {
  return a + b + c;
}

let numbers = [1,2,3];

abc(numbers) // '1,2,3undefinedundefined'
// how to fix this
```

- `abc(...numbers)`

What's the return value of a call to `Function.prototype.bind()`?

- a new function with permanently bound execution context.

What are the 3 ways to specify context for a function execution? What's the difference?

- `apply` / `call`: specify context object explicitly during function invocation
- `bind`: bind a permanent context object to a new copy of the original function
- assigning function to another object
  - retrieve a function object and assign it to the context object
  - then execute the function(actually became method) from the new object

The differences among these ways depends on the specific use case.
  - for `apply` / `call` and 'assign property', we treat the function as a more abstract entity, or say a general purpose function. When we want to use it, we provide the execution context and pass in arguments at the last moment.
  - for `bind` we make a function specialize for a single purpose by permanently binding it to an execution context, which can not be changed after the binding.

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

- the word `this` inside nested function definition refers to global object, not the first level wrapper function.

What can be called 'explicit execution'?

- when using `apply` and `call` to invoke a function while providing a context object.

What is a high-order function? what is a first-class function?

- A high-oder function is a function either accepts functions as arguments or returns a function object, or both.
- first-class function: when we say "first-class something", we mean that the "something" is a value that can be passed, assigned, referenced etc. In other words, we treat it as other normal values in that language.
  - the concept of high-order function is based on the "first-class" concept.

https://stackoverflow.com/questions/10141124/any-difference-between-first-class-function-and-high-order-function

What's IIFE? When we need it?

- IIFE refers to "Immediately Invoked Function Expression". To put it another way, it's a function expression which is executed immediately.

Why IIFE:
- IIFE has a high quality of independence
  - instead of declare a function, it wraps function in an expression -> the expression returns the function right away
    - whether or not we give a name to the function(inside the expression), function expression just return a function, without delcaring a variable(name) to reference this function. This means it will never collide with existing reference names in other scope, which makes it a safe operation.
  - function definition creates closure -> which can provide useful private data for certain operations
  - execute the returned function immediately "consume" the function almost at the same time as the function is created. After that execution, the function is gone.
- All these features make it a useful technique when we want to perform some tasks in the middle of lines of code without affecting the original code base.

How will you describe the relationships among `this`, closure, IIFE?

- `this` is the execution context during the invoking of a function or evaluating of an expression
- "closure" is a private scope created by a function definition
- IIFE is a technique that utilize `this`, 'closure' and some other features of Js

What is a constructor function?

- in Js a constructor is a function which is used to return an object which has the `constructor` property referencing back to the function
- in essence, a constructor is the function used to instantiate an instance object of a 'class' -- from the perspective of classical OOP -- and the defacto 'class' is held by the constructor's  `prototype` property.

What would be the return value if we perpend operator `new` to a function name?

- an instance of that function if there is no `return` statement inside the function to return another object.

`prototype` property name can be called on which of these callers?

- `Object`
- `aFunction` created by `aFunction = function() {}`
- `obj` after `obj = {}`

- except for the last one. The `prototype` property can't be called directly on a normal object.
- normally `prototype` only can be called on 'function' types

```js
typeof Object // 'function'
aFunction = function() {} // [Function: aFunction]
typeof aFunction  // 'function'
```

What is the end(at the top) of a prototype chain? How to improve this?

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype

- it's `Object.prototype`
  - if we call `Object.getPrototypeOf(Object.prototype)` it returns `null`

What does the code below demonstrate?

```js
var obj = { a: 1 }; // undefined
obj.prototype; // undefined
function Person(){}; // undefined
Person.prototype; // Person {}
Object.prototype; // {}
```

- The `prototype` property can't be called directly on a normal object.

What's the result of last expression, why?

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
console.log(x.constructor === F); // 6 expect to return true

// ?.
console.log(Object.getPrototypeOf(Object) === Object.prototype)
```

- The last expression returns `false` because when we call `Object.getPrototypeOf(obj)`, we are asking what the `obj` inherits from.
- `Object` has a type of 'function', more specifically, a constructor function. The usual way of using `Object.getPrototypeOf()` is to provide it with an object, then it returns the prototype(conceputally class) object.
- consider this example:
```js
var F = function() {};
var x = new F();
console.log(Object.getPrototypeOf(x) === F.prototype); // 4 expect to return true
```

Can a behavior be added to an instance by adding it to the constructor function's `prototype` after the instance has been created beforehand?

```js
function Abc() {
  this.a = function() { console.log('I am a.') };
};

var x = new Abc();
x.a() // logs 'I am a.'

Abc.prototype.b = function() { console.log('I am b.') };
x.b() // ??? Does this work
```

- yes. When trying to access a property from an instance object, if the property is not found on the object, js will continue searching up to the prototypal chain, until reach the `Object.prototype` object, which is on the top of the inheritance chain.

What is "scope-safe constructors"?

- In javascript, a scope-safe constructor is a constructor which can be used with or without keyword `new`
- One way to accomplish this is to use conditionals and recursion to force a call with `new` keyword
```js
function Person(name) {
  if (!(this instanceof Person)) {
    return new Person(name);
  }

  this.name = name;
}
```

- The conditional force instances are created by using the standard way, which uses the `new` keyword.
- The reason this is called 'scope-safe' is because by forcing objects(instances) created by the standard syntax, it prevent the keyword `this` inside the constructor function from referencing the global object, then causing undesirable results.

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

- case 1: when a function is called without `new`, the keyword `this` referening the global object.
- case 2: being called with `new`, the function is now treated as a constructor, so the `this` inside it is referencing the newly created object.

Insert an implicit step not shown in the code and let it become the reason of why `'Steve'` is not eligible for GC clearer. Then explain why?

```js
function makeHello(name) {
  return function() {
    console.log("Hello, " + name + "!");
  };
}

var helloSteve = makeHello("Steve");
```

- answer
```js
function makeHello(name) {
  // var name = 'Steve'
  return function() {
    console.log("Hello, " + name + "!");
  };
}
```

- although the step `// var name = 'Steve'` is not explicitly written out, there is a implicit step like this.
  - when defining a function with some parameters, the names of the parameters will be declared as function scope variables then initialized with the passed in arguments respectively.
- in this case, `name` becomes the function scope variable which is referenced by the closure of `makeHello`
- further more, `makeHello` returns a function which include the `name` variable inside the closure. So after `makeHello` returned, the closure have to persist with the returned function, so the `name` is still accessible.

What's the difference between the code below?

```js
// 1
function Man() {
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

- in case 1, `type` and `walk` are both defined for every instance, this means every newly created (by `new Man()`) instance has there own copy of `type` and `walk` value. Because `Man` function is funcitoning as a constructor which is used to instantiate new object. So every time new instance gets created, `type` and `walk` write to the new instance.
  - if we create many instance of `Man`, there will be much duplication of `type`(String type) and `walk`(function).
- in case 2, `type` is defined on `Man.prototype` which is also the 'prototype' of every instance
  - so this `type` will become a state shared across all instances, means there is only one copy of the value, if the value of `Man.prototype.type` changed, this will reflect on all instances either.
  - `Man.walk` is defined as a function.
    - First `Man` in fact is a function, now we add a property `walk` to it, which is a function
    - a constructor's custom property is not accessible to its instances, so if we want to invoke this `walk` function, we have to do `Man.walk()`

What is the return value of the code below?

```js
function F() {};
F.prototype.constructor === F; //?
```

- it retursn `true`. This `constructor` property is actually more useful for instance of `F`
```js
function F() {};
F.prototype.constructor === F; // true

(new F()).constructor === F; // alse  true
```

What's the return value of the code below, why?

```js
var a = {};
var b = Object.create(a);
var c = Object.create(b);

a.isPrototypeOf(c)
Object.getPrototypeOf(c) === a
```

- `a.isPrototypeOf(c)` returns `true`. `isPrototypeOf` checks if `a` appears **anywhere** at the prototypal chain of `c`
- `Object.getPrototypeOf(c) === a` returns `false`. `Object.getPrototypeOf()` returns the direct prototype object of an object, in this case, it's `b`

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
person.age // 12
```

- insert this

```js
Object.defineProperty(person, 'age', {
  enumerable: false,
  configurable: false,
})
```
- `Object.defineProperty` alter's attributes of an object's property, you can seen it as a method to change the properties of a property.

How to check if a value(or object) has access to a certain property or method? Further more, how to determine if the the property or method is defined on the object itself?

- if we want check if an object has access to a certain property or method, we can user [`in` operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/in)
```js
'toString' in []; // true
[1,2,3].toString(); // '1,2,3'

'split' in []; // false
[1,2,3].split();
// Thrown:
// TypeError: [1,2,3].split is not a function

'split' in String.prototype; // true
'hello'.split(''); // [ 'h', 'e', 'l', 'l', 'o' ]
```
- if we want to determine if the the property or method is defined on the object itself, we can use:
  - `Object.getOwnPropertyNames(instnace)`
  - `instance.hasOwnProperty('property name')`

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
- 1) what is `sub1` and `sub2`'s `constructor` property;
  - `sub1`'s constructor is `superType` -- if we check this right after the creation of `sub1` -- since its the original constructor `subType`'s `prototype` is changed to an instance of `superType` which has `constructor` property referencing to `superType`
  - but if we finish executing `subType.prototype.constructor = subType;`, both `sub1` and`sub2`'s constructor are `subType`
- 2) what is the value of `sub1` and `sub2`'s `property1` property;
  - `subType.prototype` now is an instance of `superType`, so it has access to `property1`. Since `sub1` ans `sub2` is instance of `subType` it can search up to `subType.prototype` to find the `property1` there too. But in this case, we haven't passed argument during instantiation, so the returned value would be `undefined`
- 3) what's the purpose of doing this: `subType.prototype.constructor = subType;`
  - if we substitute a constructor's `prototype` object, we need to change the new prototype's constructor referening back to the current constructor, so all the instances can get the rigth type(reflected by constructor name) of them.

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

- in previous case
  - `sub1` and `sub2` are both instance of `subType`
  - `subType`(technically `subType.prototype` object) is subclass of `superType`(technically `superType.prototype` object)

```js
Object.getPrototypeOf(sub1) // subType { property1: undefined, constructor: [Function: subType] }
sub1 instanceof subType; // true
Object.getPrototypeOf(subType.prototype); //superType {}
subType.prototype instanceof superType; //true
```

- in this case, although we use a different way to set the `prototype` object of `subType`, but the result is the same:

```js
sub1 instanceof subType; // true
Object.getPrototypeOf(sub1); //subType { constructor: [Function: subType] }
Object.getPrototypeOf(subType.prototype); // superType {}
```
