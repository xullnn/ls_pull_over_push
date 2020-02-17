What is an in-memory object?

https://en.wikipedia.org/wiki/In-memory_processing

https://en.wikipedia.org/wiki/In-memory_database

What does `DOM` stand for?

> The DOM is the lifeblood here. It's where everything goes down in the browser. JavaScript is just the syntax, the language. It can be used totally outside the browser with no DOM APIs at all (see Node.js).

https://css-tricks.com/dom/

What is the top-most node in a DOM?

What's the relationship between nodes and elements?

What's the relationship between DOM and DOM objects and DOM object types?

What's the difference between `'load'` and `'DOMContentLoaded'` event?

What's the difference among `origin`, `host`, `referer` header in http?
https://stackoverflow.com/questions/13851946/header-origin-vs-host

How to set `Access-Control-Allow-Origin` header to allow multiple `origin`s to access resources?
https://stackoverflow.com/questions/1653308/access-control-allow-origin-multiple-origin-domains?rq=1

In a jQuery collection such as a collection returned by `$('li')`, what's the type of the `this` item when we traverse the collection by `each()` and `eq()` method?

Is there any difference between these two code snippets below? How jQuery handle situations when multiple events are added to the same element?

```js
// 1
$p.slideUp(250).fadeIn(500);

// 2
$p.slideUp(250);
$p.fadeIn(500);
```



What's the difference between `stop()` and `finish()` methods?

- notice the difference of passing different arguments

https://api.jquery.com/stop/

https://api.jquery.com/finish/

What's the meaning of these selectors? Briefly explain the rule?

```
[id^=AAA_]
[id$=_BBB] matches elements with id attribute ending with _BBB.
```

- matches elements with id attribute starting with `AAA_`, and
- matches elements with id attribute ending with `_BBB`.


What's the difference between `data()` and `attr()` method when attaching data to a DOM element?

https://api.jquery.com/data/#data-key-value

> Using the `data()` method to update data does not affect attributes in the DOM. To set a `data-*` attribute value, use `attr`.

https://api.jquery.com/attr/

How many times will the callback be invoked if we click on the anchor multiple times?

```js
$('#the_link').on('click', function(event) {
  event.preventDefault();
  console.log('Callback invoked.');
  $(this).off('click');
})
```

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

How to bind an event to an element that only triggers one time(without manually unbind the event)?

https://api.jquery.com/one/

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

Use jQuery's `closest()` and `find()` method to locate the sibling `p` element starting from the `button` element with "show_less" class?

```html
<div class="container">
  <h3>JavaScript</h3>
  <p>JavaScript is a high-level, dynamic, untyped, and interpreted programming language. It ......</p>
  <button type="button" name="button" class="show_more"><a href="#">show more</a></button>
  <button type="button" name="button" class="show_less"><a href="#">show less</a></button>
</div>
```

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

`$('#n').on('click', 'span', callback)` first select all elements with attribute `id='n'`, then further select `span`s from them.

What's `ECMAScript`, is it a programming language? What's the relationship between `ECMAScript` and JavaScript?

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
