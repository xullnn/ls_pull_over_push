What is Node.js?

answer:

- Node.js is a JavaScript **runtime** built on Chrome's V8 JavaScript engine.
- Runtime describes software/instructions that are executed while your program is running, especially those instructions that you did not write explicitly, but are necessary for the proper execution of your code.

https://nodejs.org/en/

https://stackoverflow.com/questions/3900549/what-is-runtime

What's the difference between static and instance method?

answer:

A method is a function which is a property of an object. There are two kind of methods: **Instance Methods** which are built-in tasks performed by an object instance, or **Static Methods** which are tasks that are called directly on an object constructor.

What's static scoping?

answer:

In js, static scoping is also called lexical scoping. It uses the structure of the source code to determine the variable's scope. To put it another way: the source code defines the scope.

> At any point in a JavaScript program, there is a hierarchy of scopes from the local scope of the code up to the program's global scope. When JavaScript tries to find a variable, it searches this hierarchy from the bottom to the top. It stops and returns the first variable it finds with a matching name. This means that variables in a lower scope can shadow, or hide, a variable with the same name in a higher scope.

What are the 5 primitive types in Javascript?

answer:

- String
- Number
- undefined
- Boolean
- null

There are also `BigInt` and `Symbol`.

https://developer.mozilla.org/en-US/docs/Glossary/Primitive

What're the only one compound data type in Javascript?

answer:

- Object

How to escape quotes in String in Javascript?

answer:

- single quotations inside double quotation string don't have to escape.
- in other situations use back slash when needed.

What's the syntax to use JS's string interpretation(template literals)?

answer:

- backticks. For example ``The number is ${num}.``

What function can return the string representation of an object's data type in JS?

answer:

- `typeof`

What is implicit type coercion and explicit type coercion?

answer:

- when performing certain types of operation -- often comparisons, arithmetic operations etc. -- js will implicitly convert some value to another type, even though you didn't tend to do this. This is called implicit coercion.

What's the difference between `Number()` and `parseInt()`?

answer:

- `Number()` can convert various types of value into different types of number
  ```js
  > Number('3')
  3
  > Number('1.23')
  1.23
  > Number(true)
  1
  > Number(false)
  0
  > Number(null)
  0
  > Number(undefined)
  NaN
  ```
- `parseInt()` only return integers or `NaN`
  ```js
  > parseInt('1.23')
  1
  > parseInt(null)
  NaN
  ```

What's the difference between statement and expression, how to discriminate them?

answer:

Unlike expressions, statements in JavaScript don't necessarily resolve to a value. Statements generally control the execution of the program. Statements always return `undefined` and expressions often but not always return a 'meaningful value'(other than `undefined`).

https://www.quora.com/Whats-the-difference-between-a-statement-and-an-expression-in-Python-Why-is-print-%E2%80%98hi%E2%80%99-a-statement-while-other-functions-are-expressions

What is variable declaration and initialization?

answer:

- A variable declaration is a statement that asks the JavaScript engine to reserve space for a variable with a particular name.
- Assigning a value to a variable for the first time is called variable initialization.

What's block scope to a variable in Javascript and which keywords create block scope variables?

answer:

- "block scope" is the scope local to a block(between a pair of curly braces`{ }`) if there is
  - if there isn't it's local to current scope
- variable declarations start with `let`, `const` fall into this category.

> `let` allows you to declare variables that are limited in scope to the block, statement, or expression on which it is used. This is unlike the `var` keyword, which defines a variable globally, or locally to an entire function regardless of block scope.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let

```
> { let x = 1 }
undefined
> x
Thrown:
ReferenceError: x is not defined

> { var a = 2};
undefined
> a
2
```

What's the return value of the last line:

```js
let A = 1;
{ A = 2 };
{ A = 3; { A = 4 }; }
A
```

answer:

- `4`
- variable `A` is first declared in global scope, although we use `let` which limits the scope to a block(if any), but since there's not a block, `A` is local to the current scope -- global scope
- since inner scope can access outer scope, so all the reassignments can change the value of `A`

What's the return value of the last line?

```js
function say(words) {
  console.log('Hi! ' + words);
}

say("Nihao")
```

answer:

- `undefined`!

What're the two factors which can determine the scope of a variable?

answer:

- what key word is used to declare the variable
- where you declare the variable

what's the difference between function and method?

answer:

- if there's a preceding caller then it's a method
- otherwise it's a function

What a function/method can mutate?

answer:

- a function can mutate passed in arguments
- a method can mutate the caller or passed in arguments

What're the syntaxes of writing function declarations, function expressions, and arrow functions?

answer:

> A Function Expression defines a function as a part of a larger expression syntax (typically a variable assignment ). Functions defined via Functions Expressions can be named or anonymous.

- function declaration must start with key word `function`
  - `function hi() {}`
- function expression is a function declaration as part of a larger expression
  - `let a = function b() {}` or `let a = function() {}` or simply `(function hi() {})`
- arrow function is a way to write anonymous functions, it's often used during method invocations(being passed in as one of the argument)
  - `[1,2,3].forEach(e => console.log(e))`
- another form of using arrow functions
```js
> let a = e => console.log(e);
undefined
> a('hello')
hello
undefined
```

If we assign a value to a variable name without declaring that variable, what the scope of the variable will be?

answer:

- It will be at the global variable.

What is non-strict equality operator and non-strict inequality operator? How they work?

answer:

- non-strict equality and inequality are `==` and `!=`(differ from strict ones `===` and `!==`)
- they are used to perform comparison operation, non-strict means they don't require the operands to be the same type(e.g `String` to `String`, `Number` to `Number`). If the operands are not the same type, non-strict comparison operators will first try converting them into the same type, then perform the comparison.

What're the main 3 logical operators in Javascript?

answer:

- or `||`
- and `&&`
- not `!`

What's the return value of `!!'!'`?

answer:

- `true`

Which values are evaluated to false in Javascript?

- `false`
- `null`
- `undefined`
- empty string `''`
- the Number `0`
- the Number `NaN`

How will Javascript handle the situations that when non-boolean values are used in a logical expression? For example `'' && 0`, or `6 || 7`?

answer:

- logical operator not necessarily returns boolean value.
- when using `||`
  - if the first value evaluates to true, returns the first value (e.g `1 || false` return `1`)
  - if the first value evaluates to false, returns the second value (e.g `false || 1` returns `1`)
- when using `&&`
  - if the first value evaluates to true, returns the second value (e.g `1 && ''` returns `''`)
  - if the first value evaluates to false, returns the first value (e.g `'' && 1` returns `''`)

Order these operators from the highest precedence to the lowest?

- ===, !== - Equality
- || - Logical OR
- && - Logical AND
- <=, <, >, >= - Comparison

answer:

- comparison > equality > logical `&&` > logical `||`

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence

What's ternary operator and what's the syntax?

answer:

- a shorthand syntax which contains dense logical meaning.
- there are 3 parts in the expression which are divided by a `?` and a `:`
  - part 1: serve as a if condition
  - `?` signifies the end of if condition
  - part 2: what to do if the part1 if condition is true
  - `:` signifies the beginning of a `else` clause
  - part 3: what to do if `else` clause is triggered(or say if condition is false)
- for part2 and part3, if they only contain a single expression, the `return` key word can be omitted.

example: `a > b ? 'greater' : 'less'`

What's the syntax of switch statement in Javascript?

answer:

```js
switch (match_criterion) {
  case case_1:
  case case_2:
  default:
}
```

- `match_criterion` will be compared with each case condition one by one.
- once a case is matched, it will execute the code inside the clause
- if there is no `break` or `return` in the matched case, all the following cases will be executed once. This is called "fall through".

What's "fall through" in `switch` statement?

- answered above

When using loop, what's the difference between `while` and `do/while` syntax?

answer:

- `while` will first check if the loop condition is matched before each iteration, then determine whether to execute the loop
- `do/while` places the `while()` condition at the end of the loop, so it will always execute the loop at least one time before it check the loop condition.

What're the 3 components in a `for` loop's argument list?

answer:

- (initialExpression, condition, and incrementExpression).

Can we omit one or more components of `for` loop's arguments? If we can, what's the syntax?

answer:

- yes we can. Just use semi-colon to end a part.

What does `continue` do in a loop? What is it similar to in Ruby?

answer:

- skip the rest of the code for current iteration
- it's like `next` in Ruby

What's the return value of the code below, why?

```js
let numbers = [ 1, 4, 6, 8 ];
numbers.map(number => {if (number > 4) return number * number})
```

answer:

- `[ undefined, undefined, 36, 64 ]`
- this is due to how `map()` works. Always remember `map` uses the return value of the block to transform every element. It always returns the same number of elements to the caller.

What's the return value of the code below, why?

```js
// 1
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 1, 2]
numbers.filter((number) => number > 6);

//2
numbers.filter(function(number) { number > 6 })
```

answer:

- 1: returns `[7, 8, 9, 10]` . When using arrow function syntax, we can omit `return` if there's only one expression inside the block
- 2: returns `[]`, syntax makes the difference, the comparisons are performed but the comparison results are not returned since we use simple anonymous function syntax that will not automatically return comparison value.

What's the difference between `forEach`, `map`, `filter`?

answer:

- `forEach` returns `undefined`
- `map` returns transformed array which has the same number of elements with the caller array
- `filter` returns array which contains selected elements from the caller.

What's the return value of `Array.prototype.push()`?

answer:

- the new length of the caller array after pushing.

How Javascript handles non-positive integer indexes?

```js
> arr = [3, 4, 5];
[ 3, 4, 5 ]
> arr[3.14] = 'PI';
'PI'
> arr
[ 3, 4, 5, '3.14': 'PI' ]
> arr.length
3
> arr[-1] = 'Negative'
'Negative'
> arr
[ 3, 4, 5, '3.14': 'PI', '-1': 'Negative' ]
> arr.length
3
```

answer:

- Inserting with non-positive integers won't add new **element** to the array.
- Instead, this will add properties to the array object
- properties will not contribute to the length of the array

How Javascript handles operations which insert values by using an out-of-range index(e.g `arr[1999] = 0`, that `arr`'s original length was 5)?

answer:

- it changes the length of the array, this is done by adding "empty items" into the gaps
- and the length will become `n+1` where `n` is the index you've inserted element.

What's the return value of the code below, why?

```js
let x = [1, 2]
let arr = [3, 4, x, 5]

arr
[ 3, 4, [ 1, 2 ], 5 ]

arr.includes(x)
// ?
arr.includes([1, 2])
// ?
```

answer:

- first one returns `true`, the second returns `false`
- in the second situation the passed in `[1,2]` is not the same object that `x` is pointing to, though they contain the same numbers.

How to access an object's value in Javascript?

answer:

- use bracket notation or dot notation
```js
someObj['name'];
someObj.name;
```

How to remove a key-value pair from a Javascript object?

answer:

- use `delete obj['property']` or `delete obj.property`
- notice when the key is number(in string form), dot notation is illegal
- when handling array object, methods mentioned above will leave an empty 'slot' in the array
  - one way to avoid this is to use `arr.splice(start, deleteAmount)`

Which of those are primitive types and which are objects?

- simple objects
- Arrays
- strings
- numbers
- Date objects
- booleans
- null
- undefined
- functions

answer:
- primitives
  - strings
  - numbers
  - booleans
  - null
  - undefined
- objects
  - Arrays
  - Date objects
  - functions

What's the most obvious difference between primitive types and object types in Javascript?

answer:

- primitives are immutable
- objects are mutable

What does prototype mean?

answer:

JavaScript is a prototype-based language. This feature allows the creation of an object without first defining its class.

>  Classes are not explicitly defined, but rather derived by adding properties and methods to an instance of another class or, less frequently, adding them to an empty object.

https://developer.mozilla.org/en-US/docs/Glossary/Prototype-based_programming

How to use `Object.create()` method to create a new object which inherits from another object? What's the difference about the new "child" object?

answer:

- if we have an existing object `obj1`, we can create a child of it by `let child = Object.create(obj1);`
- the child object can access the properties of the parent(in this case `obj1`)

How to iterate through a simple object in Javascript?

answer:

- use `for...in` syntax
- `for(property in object) {}`. `property` denotes each property name of the object
  - inside the block we can access the corresponding keys by passing key name to the object `object[property]`

What method can be used to return an object's property names?

answer:

- `Object.keys(object)`

What method can be used to return an object's property values?

answer:

- `Object.values(object)`

What's the return value of `Object.entries(anObject)`?

answer:

- two dimensional array where each sub array contains the key and the value.

How to merge two or more objects into one? What's the side effect?

answer:

Use `Object.assign(obj1, obj2, objn)` method. This will merge all objects properties and values into the first `obj1`, which is also the side effect -- it mutates the first argument object.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign

What values can be assigned as key to a Javascript object?

answer:

- strings.
- But sometimes js allow a convenient syntax like `let object = { 1: 'a', b: c }`
  - when creating the object, the keys are not string-like but they are.

How to use a regex to determine if a string contains certain pattern and return a boolean value?

answer:

- `RegExp.prototype.test(str)` for example `/bc/.test('abcd')` returns `true`.

How to perform a global pattern match in Javascript and return all matched substrings as an array?

answer:

- use match while add global match flag `g` to the regex.
```js
'I am a programmer.'.match(/a/g) // returns [ 'a', 'a', 'a' ]
```

What is the meaning of the second argument in this expression `parseInt('123', 10);`?

answer:

- the second argument indicates the base of the conversion from string to integer.
  - `10` means decimal: `parseInt('101', 10);` returns `101`
  - `2` means binary: `parseInt('101', 2);` returns `5`

What's the difference between `sth.toString()` and `String(sth)`?

```js
> String(null);
'null'
> String(undefined);
'undefined'
> null.toString
Thrown:
TypeError: Cannot read property 'toString' of null
```

answer:

- `String()` almost can convert any legal value to a string of some form(though some will be unexpected )
```js
> obj
{ '1': 'a', '2': 'b' }
> String(obj)
'[object Object]'
```

- `toString()` has a more strict requirement on the caller.

```js
> true.toString()
'true'
> 100.toString()
Thrown:
100.toString()
^^^^
SyntaxError: Invalid or unexpected token
> obj.toString()
'[object Object]'
```

How to determine whether a primitive value or an object would be evaluated to `true` or `false`?

answer:

- use double exclamation `!!`
- or `Boolean()`

What's the meaning of `NaN`?

answer:

- it can be understood as a value caused by 'illegal mathematical operation'

> NaN is a special value in JavaScript that represents an illegal operation on numbers. NaN stands for "Not a Number".?

How to check if a variable is pointing to `NaN`? What if we pass in a string?

answer:

- `isNaN(sth)`
- passing a string will return `true`.

In a `for` loop, what's the execution order of 1 initializer, 2 condition, 3 increment expression, 4 loop body -- in each iteration?

answer:

- initializer
- condition
- loop body
- increment expression

How to type a very long single-line string across multiple lines without breaking the string into many lines?

answer:

- insert back slash `/` when it needs to break a line, but don't append any extra char after the `\` such as white space

```js
'This is a \
multiple line \
string.'
```

If the internal of a function doesn't contain `return`, what would be the return value of that function?

answer:

- `undefined`

What will happen if we pass fewer arguments to a function than it's required? What about passing extra arguments?

answer:

- Js functions have a loose requirement on the number of arguments passed in
  - if we pass in extra arguments they will be ignored
  - if we pass insufficient arguments, the corresponding parameters will be assigned with `undefined`

Simply describe what is nested function in JavaScript?

answer:

- defining a function inside another function definition
```js
function one() {
  console.log('Inside function one');

  function two() {
    console.log('Function two');
  }

  two();
}
```

How to understand "a function declaration not only creates a function, but also creates a variable"?

answer:

- when declaring a function we also declare a same name variable as the function  
  - then we can pass this variable(which is referencing the function object) to other variables
  - then we can append parentheses `()` to invoke the function

How to create an anonymous function and assign it to a variable?

answer:

- `let variable = function(a) { console.log(a) }`
- `let variable = x => console.log(x)`

How to differentiate a function declaration and a function expression?

answer:

- see if the statement starts with `function`. If it is, then it's a function declaration
- otherwise it's a function expression

What is hoisting(behavior; precedence)?

answer:

- hoisting is a mechanism that will first perform function declaration and variable declaration before all other operations in a file
- function declarations are firstly hoisted and the whole declaration will be hoisted
- variable declarations(only declaration) are then hoisted but no assignment will be hoisted
- note hoisting won't make too much sense in node console

what's the scope of a variable which is declared inside a `for` loop's argument list? What if the `for` loop is at global scope? How about inside a function body?

https://stackoverflow.com/questions/18465211/javascript-loop-variable-scope

```js
// global level
for(var i = 1; i < 5; i += 1) {};
console.log(i); // error or other?

// inside function
function hello() {
  for(var i = 1; i < 5; i += 1) {};
  console.log(i);
}

hello()

console.log(i); // would this raise error?
```

answer:

- the first important fact is that in both cases we use `var` to declare variables
  - `var` doesn't limit variable to block scope, it's only local within function declaration, or it will be at global scope
> The scope of a variable declared with var is its current execution context, which is either the enclosing function or, for variables declared outside any function, global.

- when declare variable by using `var` with a `for` loop at the global scope, the variable's scope will not be limited to the code block. Instead, it will be at the global scope.
- so the first case `i` is accessible

> Variables declared with var are not local to the loop, i.e. they are in the same scope the for loop is in.

- In the second case the `for` loop is inside a function declaration so the scope will be limited within the scope of the function declaration body.
- therefor the `i` in the second case is not accessible, a reference error will be raised

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for#Parameters

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var

Does the output of the two snippets of code be the same? Why?

snippet 1:

```js
a = 1;

function hello() {
  a = 2;
}

hello();

console.log(a);
```

snippet 2:

```js
a = 1;

function hello() {
  var a = 'x'
  a = 2;
}

hello();

console.log(a);
```

answer:

- NO.
- in the first case `a` is `2`
  - `a` is at the global scope so inside the function it it also accessible
- in the second case `a` is `1`
  - `a` is also first at the global scope
  - but inside the function we declare(by using `var`) a new same name variable `a`
    - so inside the function the new `a` shadows the global `a`
    - as a result, any operation on this new `a` has nothing to do with the global `a`
  - so when we back to global scope, `a` is still `1`

How many ways are there in JavaScript to create a function? How to differentiate "create a function" and "declare a function"?

answer:

- function declaration: `function hi() {}`
- named function expression: `let hi = function hello() { console.log(typeof hello) }`
- function expression: `let hi = function() {}`

Only when `function` is the leading words we can call that a function declaration, otherwise it's not. This means we have many ways to 'create' a function but only one way to 'declare' a function.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions#Constructor_vs._declaration_vs._expression

What's the return value of the two expression below:

- `false && true === false`
- `true && false === false`

answer:

- `false && true === false` returns `false`
- `true && false === false` returns `true`
- `===` has a higher precedence to logical operator `||` and `&&`(but `!` is higher than `===`)

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence

How to determine if a given object is an array?

answer:

- `Array.isArray()`

Objects are containers for two things, they are?

answer:

- states and behaviors

How to merge multiple objects into one without mutating any of the original ones?

answer:

Use `Object.assign({}, obj1, obj2)`. By doing this(pass in an empty object as the first argument) we collect all properties and values into one object and don't have to mutate any existing objects.

How to accomplish this, why?

```js
shuxue.PI
3.141592653589793
shuxue.floor(6.004)
6
shuxue.parent
'Math'
```

answer:

- the key is find a way to let a new object inherit from the `Math` object
```js
let shuxue = Object.create(Math)
shuxue['parent'] = 'Math'
```

In what case `Object.keys(arr).length` and `arr.length` can be different?

answer:

- if we assign some value to non-positive indexes, even other types on an array, we add some properties(not elements) to the array. Under this circumstance, the number of keys and the number of elements may differ.

```js
let arr = [1, 2, 3];
arr[true] = 4;
arr.length;
Object.keys(arr).length;
```

Inspect the code below, what is the value of `counter` and `arr.length`, Why?

```js
> var arr = [1, 2, 3]
undefined
> var counter = 0;
undefined
> arr[5] = 0;
0
> arr.forEach((e) => counter += 1);
undefined
```

answer:

- `counter` is `4`
- `arr.length` is `6`

If an array is lengthened by assigning a value more than its length, then one or more `empty items` will fill the gap. This does change the `length` of the array, but when performing iteration by using methods like `forEach`, these `empty items` will be ignored.

But in another situation which we insert `undefined` value into an array, it will just be treated as normal element.

```js
> var array = [1,2,3,undefined,4,5]
undefined
> let counter = 0;
undefined
> array.forEach(e => counter += 1)
undefined
> counter
6
```

Though in the first case when we access the `empty items` it returns `undefined` too, but actually they are not the same thing.

What is pure function and what are the two main characteristics of it?

answer:

A pure function is a function that:
- has no side effect
- always returns the same value for the same input(s)

What is the return value of the following expressions, why?

```js
function sayHi() {
  return 'Hi';
}

// 1
sayHi;

// 2
sayHi();

// 3
typeof sayHi;
typeof sayHi();
```

answer:

- 1: returns `Function` object which the variable `sayHi` is referencing to
- 2: returns `'Hi'`
- 3:
  - `function`
  - `'string'`

What's the difference between the following methods defining function?

https://stackoverflow.com/questions/336859/var-functionname-function-vs-function-functionname

```js
// method 1:
function sayHi() {
  return 'Hi';
}

// method 2:
var sayHi = function sayHello() {
  return 'Hi';
}
```

answer:

- First one is a function declaration, the second is a function expression
- In second case, `sayHello` can only be referenced inside the function declaration body

What's arrow function's "implicit returns" property?

answer:

We can omit `return` and curly braces in **arrow functions** when the function body contains only one expression. If it contains two or more expressions, you must explicitly return the return value if you need it, and you must also use curly braces.

Use code example to demonstrate this quotation?

> Lexical Scoping defines how variable names are resolved in nested functions: inner functions contain the scope of parent functions even if the parent function has returned.

```js
var number = 0;

function one() {
  let number = 999;
  function two() {
    return number;
  }

  return two;
}

one()()
// returns 999
```

https://stackoverflow.com/questions/1047454/what-is-lexical-scope

Describe how `String.prototype.slice()` handles the arguments? What is the general principle behind?

- exclude/include start/ending index
- two positive
- one positive
- one positive one negative
- one negative
- two negative

answer:

- exclude/include start/ending index: include the starting index but exclude the ending index
- two positive: return new string from `start` to `end`
- one positive: return the rest of the string from the `start`
- one negative
  - negative indexes will be converted to positive indexes by the formula `length + n` n is the **negative** index
  - therefor `-1` pointing to the `length - 1` char, which is the last char in the string(notice how this differs from positive indexes where the starting index is `0`)
  - so a negative index `-n` will return the last `n` chars of the string
- two negative
  - first covert them into positive ones and think again
    - if `start` is less than the `end`, just follow the rules
    - if `start` is greater than the `end`(after conversion), then return an empty string. Here is an example:
    ```js
    > 'I am a programmer.'.slice(-1, -10) // will actually treated as (17, 8). This doesn't make sense
    ''
    ```
- one positive one negative
  - again, first convert the negative one to positive, then follow the rules

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice

How to import an external `js` file into html page? How to embed `js` code directly into html page?

answer:

- to import an external `js` file into html page, add a `<script>` tag pair to html `body` and add a `src` attribute to opening `script` tag, and set the value to the file path.
- to embed `js` code directly into html page also need to add a `<script>` tag pair, then directly write code between the two tags.

Describe the scope of variable declared by `var` keyword?

answer:

- local to a function scope or at the global scope

What's the difference between different variable declarations `var`, `let`, `const` and the scenario like `x = 1` without declaring `x` in advance?

answer:

- `var` declared variable is local to function scope or at the global scope
- `let` and `const` declared variable:
  - when declared at the global scope, they are local to global scope(means they are at the global scope)
  - when declared inside a function body but outside of any block, they have function scope
  - when declared inside a block, they are only local to the block

What is first-class value?

answer:

- a first-class value or first-class object is an entity that can be operated(e.g pass to variables) like any other entities in the language.

https://www.computerhope.com/jargon/f/firstclass-object.htm

What's the main difference between imperative and declarative style programming?

answer:

- imperative
  - concerns programming in a relatively low level
  - focuses on the steps or mechanics of solving the problem. Each line of code has a purpose, but that purpose comes from understanding the developer's implementation.

- declarative
  - concerns programming in a relatively high level
  - encapsulate implementation details into high level function/methods. Approach problems at a high level, thinking process are more close to human thoughts.

> The higher the level of abstraction that you work with, the more declarative your code is. Declarative programming frees programmers to think on a higher level that's more natural for humans. We focus on writing a good description of the problem to solve, and the computer takes care of the rest. In comparison, imperative programming often means that you must imagine yourself as the computer

What's the difference between `substr()` and `substring()` methods?

answer:

- `substring()` is similar to `slice`. It return new strings based on start and ending index.
- `substr()` doesn't use the second argument as index. It's the number of chars to return.
- What's in common is if the second argument is omitted, they both return the rest of the string.

How to sort an array of Numbers by using `Array.prototype.sort()` method?

answer:

- `Array.prototype.sort()` compares elements after converting them to `String`. So we need to pass in another comparing function to indicate how we want to compare the elements.

```js
function compareNum(a, b) {
  if (a > b) {
    return 1;
  } else if (a < b) {
    return -1;
  } else {
    return 0;
  }
}

[7,1,2,6,0].sort(compareNum)
```

What's the possible return values of `Date.prototype.getDay()` and `Date.prototype.getMonth()`, when using these methods, what need to be noted?

answer:

- `Date.prototype.getDay()`'s return values are from `0` to `6`. `0` denotes Sunday.
- `Date.prototype.getMonth()`'s return values are from `0` to `11`. `0` denotes January.

What's the output of the code below?

```js
//1
() => console.log('a');

//2
(() => console.log('a'))();
```
