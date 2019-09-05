
How to invoke a method in the form of function invocation?

How to define `this` in Javascript?

What's the moment when Javascript assigns a context to an expression/statement?

What's the meaning of "functions as Object factories"? How to do this in Javascript?

What is the implicit context when you run Javascript in browser? what about in `node` console?

After we declare a function at the top level (e.g `function abc() {}`), can we delete it by `delete abc`? Why?

What's the difference between `call` and `apply`?

What's the basic difference between function execution context(`this`) and lexical scope in JavaScript?

When invoking a function, how to convert a passed in array to an argument list?

What's the return value of a call to `Function.prototype.bind()`?

What are the 3 ways to specify context for a function execution? What's the difference?

What this code snippet demonstrates?

What can be called 'explicit execution'?

What is a high-order function? what is a first-class function?

What's IIFE? When we need it?

How will you describe the relationships among `this`, closure, IIFE?

What is a constructor function?

What would be the return value if we perpend operator `new` to a function name?

`prototype` property name can be called on which of these callers?

What is the end(at the top) of a prototype chain? How to improve this?

What does the code below demonstrate?

What's the result of last expression, why?

Can a behavior be added to an instance by adding it to the constructor function's `prototype` after the instance has been created beforehand?

What is "scope-safe constructors"?

What's the difference of `this` between these two scenarios below? Why?

Insert an implicit step not shown in the code and let it become the reason of why `'Steve'` is not eligible for GC clearer. Then explain why?

What's the difference between the code below?

What is the return value of the code below?

F.prototype.constructor === F; //?

What's the return value of the code below, why?

Insert some code at the specified position to achieve the wanted result?

How to check if a value(or object) has access to a certain property or method? Further more, how to determine if the the property or method is defined on the object itself?

Given the code below, answer 1) what is `sub1` and `sub2`'s `constructor`; 2) what is the value of `sub1` and `sub2`'s `property1` property; 3) what's the meaning of doing this: `subType.prototype.constructor = subType;`?

Describe the inheritance chain in the previous question, and what about this one?

updates:

What can be the cause of context loss?

What's the 3 typical ways to fix context loss caused by function nesting? Write out solution for each way?

```js
var obj = {
  a: 'Hello',
  b: 'World',

  outerFunc: function() {
    function nestedFunc() {
      return (this.a + ' ' + this.b);
    };

    return nestedFunc();
  },
};

obj.outerFunc() // returns 'undefined undefined'
```

What the cause of context loss in the code below? How to fix?

```js
var myAccount = {
  accountsNames: ['account1', 'account2', 'account3'],
  account1: 100,
  account2: 200,
  account3: 150,

  calculateTotal: function() {
    let total = 0;
    this.accountsNames.forEach(function(account) {
      total += this[account];
    })
    return total;
  },
};

myAccount.calculateTotal(); // returns NaN
```

*Notice in this case if we use [arrow function], context will not lose*

```js
// this.accountsNames.forEach(accout => total += this[accout])
```
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#No_separate_this
