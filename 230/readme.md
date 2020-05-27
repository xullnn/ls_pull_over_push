what's the relationship between javascript and DOM?

> The DOM is not a programming language, but without it, the JavaScript language wouldn't have any model or notion of web pages, HTML documents, XML documents, and their component parts (e.g. elements).

---

Can an instance of DOM only be used by JavaScript?

---

What's the relationship between DOM and nodes?

---

Under the context of DOM, which one is the superset between "Nodes" and "Elements", and why?

---

What is the top-most node in a DOM?

---

What are the two ways to know the type of a node?

---

Do these two lines return a static or live collection?

---

What type of selector `querySelector()` and `querySelectorAll()` are?

---

What can be called "sequential code"?

---

Locate `'load'` and `'DOMContentLoaded'` event at the right place where they are fired. Which one is more useful, why?

- html code received from server
  - 1
- html and JavaScript evaluated
  - 2
- DOM constructed from parsed html
  - 3
- page displayed on screen
  - 4
- embedded assets are loaded
  - 5

---

What's is event listener in JavaScript?

---

What's the difference between `target` and `currentTarget` properties of an `Event` object?

---

For any event triggered on a webpage, what are the default starting and ending object of the event dispatching path?

---

Will the dispatching of an event be stopped after the event is triggered once in the bubbling phase?

---

Can we add multiple same type event listeners to the same DOM object? If so what would happen?

---

Which one comes into play first? And why?
- the third argument of `obj.addEventListener()`
- `event.stopPropagation()`

---

When handling `XMLHttpRequest` object, what's the difference between `load` and `loadend` events?

---

What's the difference when using `Content-Type` header in HTTP request or response?

---

What is the request header that a client advises the server to respond(in regard to data type of the response )?

https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept

---

What's the difference between `encodeURI()` and `encodeURIComponent()`?

---

what is the full name of 'CORS'? What does it do?

https://en.wikipedia.org/wiki/Same-origin_policy

https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

---

Is the `'Access-Control-Allow-Origin'` set on the server side or on the client side?

https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin

---

What `event` will be fired when the value of an `<input>`, `<select>`, or `<textarea>` element has been changed?

---

In the console of a web page which has `jQuery` loaded, what is the return value of `typeof $`?

---

How to check whether an object is jQuery wrapped?

---

Many jQuery methods act as both getter and setter method such as `css()` and `width()`. What's the difference between the return values of `$jqueryObj.css('font-size')` and `$jqueryObj.css('font-size', '15px')`?

---

In a jQuery collection such as a collection returned by `$('li')`, what's the keyword `this` is referring to when we traverse the collection by `each()` method?

---

What are the meanings of the application of regex in below syntaxes? And what are the return values?

```js
$("a[href*=abc]")
$("a[href^=abc]")
$("a[href$=abc]")
$("a[href!=abc]")
```

https://stackoverflow.com/questions/190253/jquery-selector-regular-expressions

---

Is there any difference between these two code snippets below? How jQuery handle situations when multiple methods are added to the same element?

```js
// 1
$p.slideUp(250).fadeIn(500);

// 2
$p.slideUp(250);
$p.fadeIn(500);
```

---

What's the difference between `stop()` and `finish()` methods?

https://api.jquery.com/stop/

https://api.jquery.com/finish/

https://api.jquery.com/jquery.fx.off/

---

What's the difference between `attributes` and `properties` when talking about an html page?

---


What's the difference between jQuery's `data()` and `attr()` method when attaching data to a DOM element?

https://api.jquery.com/data/#data-key-value

> Using the `data()` method to update data does not affect attributes in the DOM. To set a `data-*` attribute value, use `attr`.

https://api.jquery.com/attr/

---

What's the native Web API to access information in relating to `data-` attributes?

---

What is 'namespace' of an event in jQuery? How to use it?

---

How many times will the callback be invoked if we click on the anchor multiple times?

```js
$('#the_link').on('click', function(event) {
  event.preventDefault();
  console.log('Callback invoked.');
  $(this).off('click'); // or $(this).off(event)
})
```

---

Describe what the code does?

```js
var descriptor = {
  click: function(e) {
    e.preventDefault();
    console.log('I am clicking!');
  },

  keypress: function(e) {
    console.log('I am typing!');
    e.preventDefault();
  }
}

$('#element').on(descriptor);
```

---

How to bind an event to an element that only triggers one time(without manually unbind the event)?

https://api.jquery.com/one/

---

Examine the code below and answer?
- what's the difference between `$(app.init)` and `$(app.init())`.
  - hint: think in terms of the different ways of using `$()`
- what's the difference between `$(app.init)` and `$(function() { app.init })`
- will `$(function() { app.init })` logs out `online` to the console? If not, why, and how to fix this?

```js
let app = {
  state: 'online.',

  init: function() {
    console.log(this.state);
  }
};
```

---

If we have this code, how to use `off()` with one selector to unbind all `click` events which have the word `yellow` in them?

```html
<ul id="bottle">
  <li id="link_1"><a href="#">I am link 1.</a></li>
  <li id="link_2"><a href="#">I am link 2.</a></li>
  <li id="link_3"><a href="#">I am link 3.</a></li>
  <li id="link_4"><a href="#">I am link 4.</a></li>
</ul>
```

```js
var callback = function(e) {
  event.preventDefault();
  console.log(this.textContent);
};

$('#link_1').on('click.blue.yellow', callback);
$('#link_2').on('click.red.yellow', callback);
$('#link_3').on('click.red.blue', callback);
$('#link_4').on('click.yellow.black', callback);
```

---

Use jQuery's `closest()` and `find()` method to locate the sibling `p` element starting from the `button` element with "show_less" class?

```html
<div class="container">
  <h3>JavaScript</h3>
  <p>JavaScript is a high-level, dynamic, untyped, and interpreted programming language. It ......</p>
  <button type="button" name="button" class="show_more"><a href="#">show more</a></button>
  <button type="button" name="button" class="show_less"><a href="#">show less</a></button>
</div>
```

---

Which one is functionally equivalent to `$('#n').on('click', 'span', callback)`, why?

```js
document.querySelector('#n').addEventListener('click', function(event) {
  if event.currentTarget.tagName === 'SPAN' {

  }
});

document.querySelector('#n').addEventListener('click', function(event) {
  if event.target.tagName === 'SPAN' {

  }
});
```

- https://api.jquery.com/on/#on-events-selector-data-handler

---

Differentiate the term "polyfill" and "transcompiler" under the context of web development?

- https://remysharp.com/2010/10/08/what-is-a-polyfill
- https://developer.mozilla.org/en-US/docs/Glossary/Polyfill
- https://en.wikipedia.org/wiki/Babel_(transcompiler)

---

What's the org that provides standards for implementing JavaScript language?

- http://www.ecma-international.org/default.htm

---

What's the org that provides standards for implementing HTML and related technologies?

- https://whatwg.org/
- https://en.wikipedia.org/wiki/WHATWG

---

What's `ECMAScript`, is it a programming language? What's the relationship between `ECMAScript` and JavaScript?

- http://www.ecma-international.org/memento/tc39.htm
- https://en.wikipedia.org/wiki/ECMAScript
- https://benmccormick.org/2015/09/14/es5-es6-es2016-es-next-whats-going-on-with-javascript-versioning

---

What is the sequence of messages being output?

- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Timeouts_and_intervals

> NOTE:  The specified amount of time (or the delay) is not the guaranteed time to execution, but rather the minimum time to execution. The callbacks you pass to these functions cannot run until the stack on the main thread is empty.

> As a consequence, code like setTimeout(fn, 0) will execute as soon as the stack is empty, not immediately. If you execute code like setTimeout(fn, 0) but then immediately after run a loop that counts from 1 to 10 billion, your callback will be executed after a few seconds.

> Using 0 as the value for setTimeout() schedules the execution of the specified callback function as soon as possible but only after the main code thread has been run.

```js
function nowAndThen() { // main thread
  console.log("Now and then......");
};

setTimeout(nowAndThen, 0); // asynchronous

// main thread
var n = 0;
while(n <= 1000000000) {
  if (n === 1000000000) console.log('I am done!');
  n += 1;
};
```

---

What does this code do?

```js
let [a, b, ...c] = [1,2,3,4,5];
```

---

What problem does the 'bubbling and capturing' model solve?

---

What is a `Promise`?

---

What's the way to chain promises together?

---

What are the mainly possible return value types within a `then()` call? And what happens to each of these types if there are further chained `then`s?

---

Simply describe what is the event loop model in browser?
