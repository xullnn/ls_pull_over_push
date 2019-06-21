What is Node.js?

answer:

- Node.js is a JavaScript **runtime** built on Chrome's V8 JavaScript engine.
- Runtime describes software/instructions that are executed while your program is running, especially those instructions that you did not write explicitly, but are necessary for the proper execution of your code.

https://nodejs.org/en/
https://stackoverflow.com/questions/3900549/what-is-runtime

What's the difference between static and instance method?

answer:

In js, static scoping is also called lexical scoping. It uses the structure of the source code to determine the variable's scope. To put it another way: the source code defines the scope.

> At any point in a JavaScript program, there is a hierarchy of scopes from the local scope of the code up to the program's global scope. When JavaScript tries to find a variable, it searches this hierarchy from the bottom to the top. It stops and returns the first variable it finds with a matching name. This means that variables in a lower scope can shadow, or hide, a variable with the same name in a higher scope.

Order these operators from the highest precedence to the lowest?

answer:

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence

- ===, !== - Equality
- || - Logical OR
- && - Logical AND
- <=, <, >, >= - Comparison
- comparison > equality > logical `&&` > logical `||`

What does prototype mean?

answer:

JavaScript has the feature of prototype-based. This type of style allows the creation of an object without first defining its class.

>  Classes are not explicitly defined, but rather derived by adding properties and methods to an instance of another class or, less frequently, adding them to an empty object.

https://developer.mozilla.org/en-US/docs/Glossary/Prototype-based_programming

How to merge two or more objects into one? What's the side effect?

answer:

Use `Object.assign(obj1, obj2, objn)` method. This will merge all objects properties and values into the first obj1, which is also the side effect -- it mutate the first argument object.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign

How to merge multiple objects into one without mutating any of the original ones?

answer:

Use `Object.assign({}, obj1, obj2)`. By doing this(pass in an empty object as the first argument) we extract all properties and values into one object and don't have to mutate any existing objects.

How many ways are there in JavaScript to create a function? How to differentiate "create a function" and "declare a function"?

answer:

- function declaration: `function hi() {}`
- named function expression: `let hi = function hello() { console.log(typeof hello) }`
- function expression: `let hi = function() {}`

Only when `function` is the leading words we can call that a function declaration, otherwise it's not. This means we have many ways to 'create' a function but only one way to 'declare' a function.

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

Describe how `String.prototype.slice()` handles the arguments?

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
  - therefor `-1` pointing to the `length - 1` char, which is the last char in the string(notice how this differs from positive indexes which the starting index is `0`)
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

What's the difference between `substr()` and `substring()` methods?

answer:

- `substring()` is similar to `slice`. It return new strings based on start and ending index.
- `substr()` doesn't use the second argument as index. It's the number of chars to return.
- What's in common is if the second argument is omitted, they both return the rest of the string.
