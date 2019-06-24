What is Node.js?

What's the difference between static and instance method?

What's static scoping?

What are the 5 primitive types in Javascript?

What're the only one compound data type in Javascript?

How to escape quotes in String in Javascript?

What's the syntax to use JS' string interpretation(template literals)?

What function can return the string representation of an object's data type in JS?

What is implicit type coercion and explicit type coercion?

What's the difference between `Number()` and `parseInt()`?

What's the difference between statement and expression, how to discriminate them?

https://www.quora.com/Whats-the-difference-between-a-statement-and-an-expression-in-Python-Why-is-print-%E2%80%98hi%E2%80%99-a-statement-while-other-functions-are-expressions

Statements always evaluate as undefined. They differ from expressions in that you cannot use a statement as part of another expression.

Unlike expressions, statements in JavaScript don't necessarily resolve to a value. Statements generally control the execution of the program.

What is variable declaration and initialization?

A variable declaration is a statement that asks the JavaScript engine to reserve space for a variable with a particular name.

Assigning a value to a variable for the first time is called variable initialization.

What's block scope to a variable in Javascript and which keywords create block scope variables?

`let` allows you to declare variables that are limited in scope to the block, statement, or expression on which it is used. This is unlike the `var` keyword, which defines a variable globally, or locally to an entire function regardless of block scope.

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
>
```


What's the return value of the last line:

```js
let A = 1;
{ A = 2 };
{ A = 3; { A = 4 }; }
A
```

What's the return value of the last line?

```js
function say(words) {
  console.log('Hi! ' + words);
}

say("Nihao")
```

What're the two factors which can determine the scope of a variable?

what's the difference between function and method?

What a function/method can mutate?
- a function can mutate passed in arguments
- a method can mutate the caller or passed in arguments

What're the syntaxes of writing function declarations, function expressions, and arrow functions?

A Function Expression defines a function as a part of a larger expression syntax (typically a variable assignment ). Functions defined via Functions Expressions can be named or anonymous.

If we assign a value to a variable name without declaring that variable, what the scope of the variable will be?

What is non-strict equality operator and non-strict inequality operator? How they work?

What're the main 3 logical operators in Javascript?

What's the return value of `!!'!'`?

Which values are evaluated to false in Javascript?

How will Javascript handle the situations that we use non-boolean values in a logical expression? For example `'' && 0`, or `6 || 7`?

Order these operators from the highest precedence to the lowest:

- ==, != - Equality
- || - Logical OR
- && - Logical AND
- <=, <, >, >= - Comparison

What's ternary operator and what's the syntax?

What's the syntax of switch statement in Javascript?

What's "fall through" in `switch` statement?

hint: be careful about `break`

When using loop, what's the difference between `while` and `do/while` syntax?

What're the 3 components in a `for` loop's argument list?

(initialExpression, condition, and incrementExpression).

Can we omit one or more components of `for` loop's arguments? If we can, what's the syntax?

What does `continue` do in a loop? What is it similar to in Ruby?

What's the return value of the code below, why?

```js
let numbers = [ 1, 4, 6, 8 ];
numbers.map(number => {if (number > 4) return number * number})
```

What's the return value of the code below, why?

```js
// 1
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 1, 2]
numbers.filter((number) => number > 6);

//2
numbers.filter(function(number) { number > 6 })
```

What's the difference between `forEach`, `map`, `filter`?

What's the return value of `Array.prototype.push()`?

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

How Javascript handles operations which insert values by using an out-of-range index(e.g `arr[1999] = 0`, that `arr`'s original length was 5)?

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

How to access an object's value in Javascript?

How to remove a key-value pair from a Javascript object?

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

What's the most obvious difference between primitive types and object types in Javascript?

What does prototype mean?

How to use `Object.create()` method to create a new object which inherits from another object? What's the difference about the new "child" object?

How to iterate through a simple object in Javascript?

What method can be used to return an object's property names?

What method can be used to return an object's property values?

What's the return value of `Object.entries(anObject)`?

How to merge two or more objects into one? What's the side effect?

What values can be assigned as key to a Javascript object?

How to use a regex to determine if a string contains certain pattern and return a boolean value?

How to perform a global pattern match in Javascript and return all matched substrings as an array?

What is the meaning of the second argument in this expression `parseInt('123', 10);`?

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

How to determine whether a primitive value or an object would be evaluated to `true` or `false`?

What's the meaning of `NaN`?

NaN is a special value in JavaScript that represents an illegal operation on numbers.NaN stands for "Not a Number".?

How to check if a variable is pointing to `NaN`? What if we pass in a string?

In a `for` loop, what's the execution order of 1 initializer, 2 condition, 3 increment expression, 4 loop body -- in single iteration?

How to type a very long single-line string across multiple lines  without breaking the string into many lines?

https://launchschool.com/exercises/b39951cf

If the internal of a function doesn't contain `return`, what would be the return value of that function?

What will happen if we pass fewer arguments to a function than it's required? What about passing extra arguments?

Simply describe what is nested function in JavaScript?

How to understand "a function declaration not only creates a function, but also creates a variable"?

How to create an anonymous function and assign it to a variable?

How to differentiate a function declaration and a function expression?

What is hoisting(behavior; precedence)?

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

How many ways are there in JavaScript to create a function? How to differentiate "create a function" and "declare a function"?

hint: define from the top level

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions#Constructor_vs._declaration_vs._expression

What's the return value of the two expression below:

- `false && true === false`
- `true && false === false`

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence

How to determine if a given object is an array?

Objects are containers for two things, they are?

How to merge multiple objects into one without mutating any of the original ones?

How to accomplish this, why?

```js
shuxue.PI
3.141592653589793
shuxue.floor(6.004)
6
shuxue.parent
'Math'
```

In what case `Object.keys(arr).length` and `arr.length` can be different?

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

What is pure function and what are the two main characteristics of it?

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

What's the third way to define a function?

```js
let greetPeople = () => console.log('Good Morning!');
greetPeople();
```

What's arrow function's "implicit returns" property?

We can omit it in arrow functions when the function body contains one expression. If it contains two or more expressions or statements, you must explicitly return the return value if you need it, and you must also use curly braces.

Use code example to demonstrate?

https://stackoverflow.com/questions/1047454/what-is-lexical-scope

> Lexical Scoping defines how variable names are resolved in nested functions: inner functions contain the scope of parent functions even if the parent function has returned.

Describe how `String.prototype.slice()` handles the arguments? What is the general principle behind?

- exclude/include start/ending index
- two positive
- one positive
- one positive one negative
- one negative
- two negative

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice

How to import an external `js` file into html page? How to embed `js` code directly into html page?

Describe the scope of variable declared by `var` keyword?

What's the difference between different variable declarations `var`, `let`, `const` and the scenario like `x = 1` without declaring `x` in advance?

What is first-class value?
https://www.computerhope.com/jargon/f/firstclass-object.htm

What's the main difference between imperative and declarative style programming?

it focuses on the steps or mechanics of solving the problem. Each line of code has a purpose, but that purpose comes from understanding the developer's implementation.

By moving the "how to do something" and focusing on "what we need to do," we raise the abstraction level of the program.

Filter Abstraction that Truly Reflects the Purpose. Omit some secondary implementation details and let us focus on the main task.

The higher the level of abstraction that you work with, the more declarative your code is. Declarative programming frees programmers to think on a higher level that's more natural for humans. We focus on writing a good description of the problem to solve, and the computer takes care of the rest. In comparison, imperative programming often means that you must imagine yourself as the computer

What's the difference between `substr()` and `substring()` methods?

How to sort an array of Numbers by using `Array.prototype.sort()` method?

What's the possible return value of `Date.prototype.getDay()` and `Date.prototype.getMonth()`, when use these methods what need to be noted?
