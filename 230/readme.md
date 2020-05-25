Use this excerpt from [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction#DOM_and_JavaScript) as a hint to explain what's the relationship between javascript and DOM?

> The DOM is not a programming language, but without it, the JavaScript language wouldn't have any model or notion of web pages, HTML documents, XML documents, and their component parts (e.g. elements).

answer: DOM(Document Object Model) is cross-platform and independent implementation of interfaces for representing HTML or XML document as structured objects. Each node in a DOM instance represents a part of the whole document(HTML or XML). Also interfaces are implemented on nodes of different levels to be accessed or manipulated by certain programming languages such as JavaScript.

- https://en.wikipedia.org/wiki/Document_Object_Model

Can an instance of DOM only be used by JavaScript?

answer: no. Any languages that are DOM-Interfaces-Awared can use an instance of DOM.

What's the relationship between DOM and nodes?

answer: DOM is the way of building object representation of a document, and nodes are concrete components of a 'DOMed' document which can be manipulated by programming languages.

Under the context of DOM, which one is the superset between "Nodes" and "Elements", and why?

- Nodes is the superset.
- A DOM instance is made of structured nodes. Elements are just a type of nodes.

```js
let a_p_e = document.querySelector('p');
function getInheritanceChain(node) {
  let chain = [];
  let proto = Object.getPrototypeOf(node);
  while (proto !== null) {
    chain.unshift(proto);
    proto = Object.getPrototypeOf(proto);
  }

  return chain;
}

console.log(getInheritanceChain(a_p_e));

// logs

// (6) [{…}, EventTarget, Node, Element, HTMLElement, HTMLParagraphElement]
    // 0: {constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, hasOwnProperty: ƒ, __lookupGetter__: ƒ, …}
    // 1: EventTarget {Symbol(Symbol.toStringTag): "EventTarget", addEventListener: ƒ, removeEventListener: ƒ, dispatchEvent: ƒ, constructor: ƒ}
    // 2: Node {ELEMENT_NODE: 1, ATTRIBUTE_NODE: 2, TEXT_NODE: 3, CDATA_SECTION_NODE: 4, ENTITY_REFERENCE_NODE: 5, …}
    // 3: Element {…}
    // 4: HTMLElement {…}
    // 5: HTMLParagraphElement {Symbol(Symbol.toStringTag): "HTMLParagraphElement", constructor: ƒ}
  // length: 6
  // __proto__: Array(0)
```

- check the prototypal chain starts from a `p` element, the relationship is
  - HTMLParagraphElement -->
  - HTMLElement -->
  - Element -->
  - Node -->
  - EventTarget -->
- So an element is just a type of node

What is the top-most node in a DOM?

answer: The `document` node.

Explain the main purpose of these DOM object types: `Node`, `Element`, `Text`, `EventTarget`?

answer:
- `EventTarget` is the supertype of `Node`, which also makes it the supertype of `Element` and `Text`
  - it provides interfaces to interact with nodes in a DOM
- `Node` is the supertype of all elements, so it provides shared properties and behaviors for all elements
- `Element` represents all html elements
- `Text` represents all text nodes in a DOM

What are the two ways to know the type of a node?

answer:
- `toString()`, `String()` or call `.constructor` on the node
- use `instanceof` operator

> The `instanceof` operator tests whether the prototype property of a constructor appears **anywhere** in the prototype chain of an object.

Which of these two returns a static or live collection?

- document.querySelectorAll();
- node.childNodes;

answer:
  - `document.querySelectorAll()` returns the static, `node.childNodes` returns the live.

What type of selector `querySelector()` and `querySelectorAll()` are?

answer: CSS selector

What can be called "sequential code"?

answer: code that are execute line by line, in a certain sequence.

Which statements are more accurate when talking about lines of code that contains `setTimeout()`?

- the execution of code is divided by `setTimeout()` into a number of parts, non-setTimeout parts are execute immediately, setTimeout parts will pause for given time delay, then execute, then continue to execute the next part
- actually all lines of code are executed in sequence, only the (operations contained in)functions passed to `setTimeout` are delayed for the given delays. And we can somehow treat the starting points for calculating delays as the same time point, because the sequential execution of all code is very fast.

answer: the second one.

Insert `'load'` and `'DOMContentLoaded'` event at the right place where they are fired? Which one is more useful, why?

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

answer:

- `DOMContentLoaded` fired when the building of Document Object Model is finished, and before page(interfaces) displayed to user, so it's at the place 3.
- `load` fired when all html, js, and all related assets(css, image, videos etc) finishes loading, so it's at place 5.
- `load` event is fired at a very late moment of a page's life cycle, waiting for all assets to finish loading is an uncertain situation, so it's not very useful. Instead, `DOMContentLoaded` fired when the DOM built successfully, which is the point when the main frame of a page is built, that's when most useful interactions can happen.

What's is event listener in JavaScript?

answer: the answer of 'what' is tightly bound with the 'how'. An event listener is like a monitor attached to specific DOM object(s), which can detect and recognize an interaction happening between user and the device(browser), if the interaction meets the pre-specified event type, it will invoke some predefined procedures(functions).

What's the difference between `target` and `currentTarget` properties of an `Event` object?

answer: `target` refers to the exact DOM object that the event is happening on. `currentTarget` refers to the DOM object that we originally attach the event. The difference is not obvious until we use event delegation.

For any event triggered in a webpage, what are the default starting and ending DOM objects of the event dispatching path?

answer: when an event is happened on a webpage, the dispatch of it won't start with the `currentTarget` or `target` object. Instead the event will first be dispatched to the top most object `window`, then all the way down to where the event is exactly happened or say the `target`, then from there it reverses the dispatch direction, all the way up back to the `window` again. So the starting and ending points are both `window` object.

Will the dispatching of an event be stopped after the event is triggered once in the bubbling phase?

answer: No. This depends on how many event listeners with the same type sit in the bubbling path. If there are more than one event listener, all of them will be triggered sequentially from inside out. Unless we call `event.stopPropagation()` when the first event is triggered.

Can we add multiple same type event listeners to the same DOM object? If so what would happen?

answer: Yes. This allows many same type events happen on the same object without overwriting one another.

Which one comes into play first? And why?
- the third argument of `obj.addEventListener()`
- `event.stopPropagation()`

answer: the third argument of `obj.addEventListener()` is a boolean value that indicates at which phase an event be fired -- capture phase or bubbling phase -- `true` for capture phase. `event.stopPropagation()` will stop the passing of the event after it is fired no matter it's fired on capture or bubbling phase. So logically the third argument of `obj.addEventListener()` must go first then the `event.stopPropagation()` can determine if the dispatching of event is stopped.

If we want to rename `stopPropagation()`, would `stopEventDispatching()` make sense? If not, can you think of anything else?

answer: In essence, what `stopPropagation()` does is stopping the dispatching of an event along the default dispatching path which is from `window` down to `target` then up to `window` again. So `stopPropagation()` stops the dispatching of an event, so the event will be done there, no further listeners will response to the event. So it makes sense to name it `stopEventDispatching()`.

When handling `XMLHttpRequest` object, what's the difference between `load` and `loadend` events?

answer: `loadend` is an event happens after `load`. `load` refers to the point when a successful(such as `2xx`) response is returned. `loadend` is an event happens after any type of response is returned, on matter the response is `2xx` or `3xx` or others.

> The `loadend` event is fired when a request has completed, whether successfully (after load) or unsuccessfully (after abort or error).

> The `load` event is fired when an `XMLHttpRequest` transaction completes successfully.

What's the difference when using `Content-Type` header in HTTP request or response?

answer:
  - `Content-Type` in request is set by the sender telling the format or type of data in request body if there's any. It's not asking the server to return a specified type of data.
  - `Content-Type` header in response is to indicate the type of data in response body.

What is the request header that a client advises the server to respond(in regard to data type of the response )?

answer: `Accept` header. And advising types can be multiple, then the server will inform the client what's the returned type by using `Content-type` response header.

https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept

What's the difference between `encodeURI()` and `encodeURIComponent()`?

answer:
- `encodeURI()` accepts a complete URL as argument, and it doesn't escape reserved chars in the url, since this will make the url invalid.
- `encodeURIComponent()` can be used to encode query string, which means chars with special meaning in (protocol + host + path) will be escaped.

> The `encodeURI()` function does not encode characters that have special meaning (reserved characters) for a URI.

What's the difference between `XMLHttpRequest.responseType` and  `Accept` request HTTP header?

answer:
  - they both specify the response type, but `Accept` is a http header, which means it's part of the implementation of HTTP, it's set by calling `XMLHttpRequest.setRequestHeader()` method. `XMLHttpRequest.responseType` is not a method but a property, it can directly set by `request.responseType = type` syntax.

what is the full name of 'CORS'? What does it do?

answer:
- Cross Origin Resource Sharing
- It's used to let us issue legitimate Cross Origin Requests which are forbidden by the Same-Origin Policy by default. It's a mechanism(also a W3C specification) to allow Cross Origin access to resources on other origins.

https://en.wikipedia.org/wiki/Same-origin_policy

https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

Is the `'Access-Control-Allow-Origin'` set on the server side or on the client side?

answer: Server side.

> The Access-Control-Allow-Origin response header indicates whether the response can be shared with requesting code from the given origin.

https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin

What `event` will be fired when the value of an `<input>`, `<select>`, or `<textarea>` element has been changed?

answer: `input` event.

In the console of a web page which has `jQuery` loaded, what is the return value of `typeof $`?

answer: it returns `'function'` since at its core, jQuery is a function that wraps the DOM and some methods.

How to check whether an object is jQuery wrapped?

answer: try `jquery` property on the object, like `obj.jquery`. If it returns a jQuery version number, then it's a jQuery object, otherwise it's not.

Many jQuery methods act as both getter and setter method such as `css()` and `width()`. What's the difference between the return values of `$jqueryObj.css('font-size')` and `$jqueryObj.css('font-size', '15px')`?

answer:
- `$jqueryObj.css('font-size')` returns a string such as `"14px"`
- `$jqueryObj.css('font-size', '15px')` returns another jQuery object so it can be chained with other jQuery methods like `$jqueryObj.css('font-size', '15px').width()`

In a jQuery collection such as a collection returned by `$('li')`, what's the keyword `this` is referring to when we traverse the collection by `each()` method?

answer: It's a plain DOM object.

What are the meanings of the application of regex in below syntaxes? And what are the return values?

```js
$("a[href*=abc]")
$("a[href^=abc]")
$("a[href$=abc]")
$("a[href!=abc]")
```

answer:
```js
$("a[href*=abc]") // choose anchor(s) whose href attribute contains 'abc'
$("a[href^=abc]") // choose anchor(s) whose href attribute starts with 'abc'
$("a[href$=abc]") // choose anchor(s) whose href attribute ends with 'abc'
$("a[href!=abc]") // choose anchor(s) whose href attribute not with 'abc'
```

https://stackoverflow.com/questions/190253/jquery-selector-regular-expressions

Is there any difference between these two code snippets below? How jQuery handle situations when multiple methods are added to the same element?

```js
// 1
$p.slideUp(250).fadeIn(500);

// 2
$p.slideUp(250);
$p.fadeIn(500);
```

answer: They are the same. All these operations either chained or called in multiple lines will be executed sequentially.

What's the difference between `stop()` and `finish()` methods?

answer:
  - `stop`:
    - stop the *current* running animation
    - 1st argument: clear all queued animation of the current element
    - 2nd argument: jump to the end value of the animation
  - `finish`:
    - stop all *current* running animation(so it is more suitable to be called on a collection)
    - 1st argument: clear all queued animation on current page, this is due to the argument it takes `queue (default: 'fx')`
      - `fx`: a reference to the `jQuery.fx` prototype object
    - 2nd argument: jump to the end value of the animation of each element within the collection

https://api.jquery.com/stop/

https://api.jquery.com/finish/

https://api.jquery.com/jquery.fx.off/

What's the difference between `attributes` and `properties` when talking about an html page?

answer:
  - when talking about `attributes` in the context of HTML tag, `attributes` are the additional key-value pairs written within the tag, such as `id='1'`, `class='container abc'`
  - when talking about `attributes` in the context of a DOM object, its an `property` which returns a live collection that contains data extracted from the corresponding HTML tag's concrete `attributes`
  - when talking about `properties`, we are in the context of DOM object. A DOM object can contain many `properties` relating to many aspects of itself such as `children`, `className`, `classList`, `id`, as well as `attributes`


What's the difference between jQuery's `data()` and `attr()` method when attaching data to a DOM element?

answer:
  - `data()` method only get and set data to an element without affecting DOM attributes of that element, neither does at HTML level.
  - using `attr()` to set `data-` will write a new `data-` attribute in HTML code as well as update the corresponding attributes of that DOM object.

https://api.jquery.com/data/#data-key-value

> Using the `data()` method to update data does not affect attributes in the DOM. To set a `data-*` attribute value, use `attr`.

https://api.jquery.com/attr/

What's the native Web API to access information in related to `data-` attributes?

answer:
  - use `element.dataset` to get all `data-` related information
  - use `element.dataset = ` as the setter method
  - but older browsers may not support this API, so jQuery's `attr` is recommended

What is 'namespace' of an event in jQuery? How to use it?

answer: A namespace is a further identifier for a specific event, in contrast to the general ones such as `click` and `submit`. For example, an event being named with `click.remove` is bound to an anchor, this event can be pinpoint by the exact name `click.bob`, it can also be found by `click` but along with many other `click` events being bound to this anchor. This is useful when we have multiple events bound to a single element and we have the need to handle one of the event separately. For example, we want to `off()` one of the `click` event on the element while keeping the others unchanged.

How many times will the callback be invoked if we click on the anchor multiple times?

```js
$('#the_link').on('click', function(event) {
  event.preventDefault();
  console.log('Callback invoked.');
  $(this).off('click'); // or $(this).off(event)
})
```

answer: since we unbind(`off()`) the event when we first invoke the callback. This `click` event will only be invoked once.

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

answer: this code binds 2 events(one `click` and one `keypress`) to the `#element` element.

How to bind an event to an element that only triggers one time(without manually unbind the event)?

answer: use `one()` method.

https://api.jquery.com/one/

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

answers:
- what's the difference between `$(app.init)` and `$(app.init())`.
  - answer: when passing a function to `$()`, this function will be treated as a handler to be invoked after the DOM is 'ready'. When passing other things(a string, an element), it can act as a selector and wrapper function. We can even use `$()` to construct a new jQuery object, for example `$('<span>', { class: 'highlight', id: 1 })` will create a new jQuery collection with a `span` element wrapped in and at the collection's index of `[0]`.
  - `app.init` returns a function, this function will **later** be invoked when the DOM is ready
  - `app.init()` returns `undefined`, `$(undefined)` returns an empty jQuery object.
- will `$(app.init)` logs out `online` to the console? If not, why, and how to fix this?
  - answer: No. We first call `app.init`, this returns a function as a first class value to the DOM ready syntax `$()`. The time we invoke this function is when the DOM is ready, the way we invoke the function is not calling it with the `app` object, therefore the function will by then lose its execution context.  So when the function is invoked, `this` is referencing the global object which has no `state` property being defined.
  - To fix this. We need to hard bind the `app` object as the context of `init` when we pass it to the `$()` -- `$(app.init.bind(app))`. Or we can use a wrapper function then change the way we invoke `init()` -- `$(function() { app.init() })`

If we have this code, how to use `off()` with one selector to unbind all `click` events of which have the word `yellow` in them?

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

answer:

```js
$('li').off('click.yellow');
```

Use jQuery's `closest()` and `find()` method to locate the sibling `p` element starting from the `button` element with "show_less" class?

```html
<div class="container">
  <h3>JavaScript</h3>
  <p>JavaScript is a high-level, dynamic, untyped, and interpreted programming language. It ......</p>
  <button type="button" name="button" class="show_more"><a href="#">show more</a></button>
  <button type="button" name="button" class="show_less"><a href="#">show less</a></button>
</div>
```

answer:

```js
$('button.show_less').closest('div').find('p');
```

- `$e.closest()` starts from current element(including itself), traverses up through its ancestors to find the target element.
- `$e.find()` starts from the current element(excluding), searches through its descendants to find the target element.

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

answer:
- the second code snippet.
- `$('#n').on('click', 'span', callback)` first delegates `click` event on the parent element with an id of `n`. Then it only triggers the event when any `span` descendants are clicked.

The meaning of the second selector argument:

> A selector string to filter the descendants of the selected elements that trigger the event. If the selector is null or omitted, the event is always triggered when it reaches the selected element.

- https://api.jquery.com/on/#on-events-selector-data-handler

Differentiate the term "polyfill" and "transcompiler" under the context of web development?

answer:
- "polyfill" is the code we write to provide feature that are not natively supported by the browser. 'The code' here is often JavaScript on the Web, but it doesn't have to be JavaScript. "Poly" means the new feature can be implemented by many other techniques including JavaScript.
- a "transcompiler" can support the use of new feature(or syntax) of a language to be used in older runtimes(engines).
  - one example is Babel.

> Babel is a free and open-source JavaScript transcompiler that is mainly used to convert ECMAScript 2015+ (ES6+) code into a backwards compatible version of JavaScript that can be run by older JavaScript engines.

- the main difference between "polyfill" and "transcompiler" is that polyfill is talking about features of browser, while 'transcompiler' is talking about features of language.


- https://remysharp.com/2010/10/08/what-is-a-polyfill
- https://developer.mozilla.org/en-US/docs/Glossary/Polyfill
- https://en.wikipedia.org/wiki/Babel_(transcompiler)

What's the org that provides standards for implementing JavaScript language?

answer: ECMA International.

> Ecma International is an industry association founded in 1961, dedicated to the standardization of information and communication systems.

- http://www.ecma-international.org/default.htm

What's the org that provides standards for implementing HTML and related technologies?

answer: WHATWG.

> On 28 May 2019, the W3C announced that WHATWG would be the sole publisher of the HTML and DOM standards.

- https://whatwg.org/
- https://en.wikipedia.org/wiki/WHATWG

What's `ECMAScript`, is it a programming language? What's the relationship between `ECMAScript` and JavaScript?

answer: 'ECMAScript' is the standard to implement Javascript language.

> Standardization of the general purpose, cross platform, vendor-neutral programming language ECMAScript™. This includes the language syntax, semantics, and libraries and complementary technologies that support the language. This work intends not to use patents or if so then only royalty free patents.

- http://www.ecma-international.org/memento/tc39.htm
- https://en.wikipedia.org/wiki/ECMAScript
- https://benmccormick.org/2015/09/14/es5-es6-es2016-es-next-whats-going-on-with-javascript-versioning

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

answer: First the string `'I am done!'` is logged out, then the `'Now and then'`. Though the time delay of the callback `nowAndThen` is set to `0` millisecond, but it doesn't mean that it will be invoked immediately. The way asynchronous code works is first to wait the synchronous part(the main thread) to finish, then it starts counting down the time delay and executing the callbacks queued there.

What does this code do?

```js
let [a, b, ...c] = [1,2,3,4,5];
```

answer: it's a syntax to initiate multiple variables in single line. `a` and `b` will reference integer `1` and `2` separately, `c` will reference the array `[3, 4, 5]`.

What problem does the 'bubbling and capturing' model solve?

answer:

1. when we want to listen certain type of event on many elements held by a parent elements, but it's not approachable to attach many listeners on each of the child elements.

2. It also solves the problem that when new node(s) is dynamically inserted into the parent element, using 'bubbling and capturing' model can, to some extent, maintain the listening behaviors we set before, means the changing of the DOM structure won't break the feature of the page.

What is a `Promise`?

answer: a promise is an object that represents the eventual completion state of an asynchronous operation and its result(when succeed) or failure reason(when error occurs)


What's the way to chain promises together?

answer: we use `promise.then()` to chain promises together.

What are the mainly possible return value types within a `then()` call? And what happens to each of these types if there are further chained `then`s?

answer:

- returns a new promise
  - the next chained `when` will wait until the returned promise to settle
- return async values such as array or string
  - the program flow will move to the next chained `then` and returned async value will be passed as argument to the success callback of next `then`.
- throw an error
  - the error will be caught by the next chained `catch()`

Simply describe what is the event loop model in browser?

answer:

the event loop model consists of:
- a main thread, which is the calling stack of synchronous functions
- a scheduler, which is an API provided by browser to act as a timer and to schedule async functions
- a task queue, async functions(tasks) are pushed into here
  - tasks in here will only be executed if the main thread is clear
