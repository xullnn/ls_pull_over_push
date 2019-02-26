## Web Development

1. What is internet?

The Internet (contraction of interconnected network) is the global system of interconnected computer networks that use the Internet protocol suite (TCP/IP) to link devices worldwide.

https://en.wikipedia.org/wiki/Internet

The internet is really a design philosophy and an architecture that expressed in a set of protocols.

https://www.khanacademy.org/computing/computer-science/internet-intro/internet-works-intro/v/what-is-the-internet

2. What is a protocol?

A protocol is a well-known set of rules and standards used to communicate between machines.

3. What is a device's unique address under the context of the internet?

All the different devices on the internet have unique addresses. An address on the internet is just a number that's unique to each device on the network.

The address system for computers on the internet is similar. One of the most important protocols used in internet communication simply called **Internet Protocol** or **IP**. So the word `IP address` means `Internet Protocol address.`

4. What is DNS?

Domain Name System.

The Domain Name System (DNS) is a **system** used to convert a computer's host name into an IP address on the Internet.

<details>
<summary>More details</summary>
For example, if a computer needs to communicate with the web server `example.net`, your computer needs the IP address of the web server `example.net`. It is the job of the DNS to convert the host name(`example.com`) to the IP address of the web server. It is sometimes called the Internet's telephone book because it converts a Website's name that people know, to a number that the Internet actually uses.
</details>

5. How is data delivered to you reliably through the internet?

key concepts:
- IP address => where to send / where sent from
- TCP protocol(Transmission Control Protocol) => how to send/receive
- Router => conduct paths to send
- packets => data pieces

First we need to know exactly where we want to send the data, also the sending destination needs to know where the data sent from, this is done by IP address.

Next,  based one size and type, the data will be splitted into a set of packets before being sent out. The receiving device will receive these packets, then it will confirm and reassemble them together. This part of work(splitting, confirming, reassembling) is done by TCP(Transmission Control Protocol).

In the midst of transportation, these packets may be sent through different routes based the traffic condition or other factors. Which routes to choose is determined by many routers along the way.

All the protocols and routers let the internet send data reliably, and also give it the ability of fault tolerant and scalability. Adding more routers will not interrupt the current users but enhance the reliability of the network.

<details>
<summary>More details</summary>
<p>If the Internet were made of direct, dedicated connections, it would be impossible to keep things working as millions of users join, especially since there is no guarantee that every wire and computer is working all the time. Instead, data travels on the Internet in a much less direct fashion.</p>

</p>The way information gets transferred from one computer to another is pretty interesting. It need not follow a fixed path. In fact, your path may change in the midst of a computer-to-computer conversation. Information on the Internet goes from one computer to another in what we call **a packet of information**, and a packet travels from one place to another on the Internet a lot like how you might get from one place to another in a car, depending on traffic congestion or road conditions, you might choose or be forced to take a different route to get to the same place each time you travel. And just as you can transport all sorts of stuff inside a car, many kinds of digital information can be sent with IP packets, but there are some limits. What if, for example, you need to move a space shuttle from where it was built to where it will be launched? A shuttle won't fit in one truck, so it needs to be broken down into pieces, transported using a fleet of trucks. They could all take different routes, and might get to the destination at different times, but once all the pieces are there, you can reassemble the pieces into the complete shuttle, and it'll be ready for launch. On the Internet, the details work similarly. If you have a very large image that you want to send to a friend or upload to a website, that image might be made up of tens of billions of bits of ones and zeroes, too many to send along in one packet. Since it's data on a computer, the computer sending the image can quickly break it into hundreds or even thousands of smaller parts called **packets**. Unlike cars or trucks, these packets don't have drivers, and they don't choose their route. **Each packet has the internet address of where it came from and where it's going. Special computers on the Internet, called routers, act like traffic managers to keep the packets moving through the networks smoothly.** If one route is congested, individual packets may travel different routes through the Internet, and they may arrive at the destination at slightly different times, or even out of order.</p>

</p>As part of the Internet Protocol, every router keeps track of multiple paths for sending packets, and it chooses the cheapest available path for each piece of data, based on destination IP address for the packet. "Cheapest," in this case, doesn't mean cost, but time and non-technical factors such as politic and relationships between companies. Often the best route for data to travel isn't necessarily the most direct. **Having options for paths makes the network fault tolerant, which means the network can keep sending packets, even if something goes horribly, horribly wrong. This is the basis for a key principle of the Internet, reliability.** Now, what if you want to request some data and not everything is delivered? Say you want to listen to a song. How can you be 100% sure all the data will be delivered so the song plays perfectly? Introducing your new best friend, **TCP, Transmission Control Protocol. TCP manages the sending and receiving of all your data as packets. Think of it like a guaranteed mail service.** When you request a song on your device, Spotify sends the song broken up into many packets. When your packets arrive, TCP does a full inventory and sends back acknowledgements of each packet received. If all packets are there, TCP signs for your delivery, and you're done. If TCP finds some packets are missing, it won't sign. Otherwise, your song wouldn't sound as good, or portions of the song could be missing.</p>

<p>What's great about the TCP and router systems is they're scalable. They can work with eight devices or 8,000,000,000 devices. In fact, because of these principles of fault tolerance and redundancy, the more routers we add, the more reliable the Internet becomes. What's also great is we can grow and scale the Internet without interrupting service for anybody using it. - The Internet is made of hundreds of thousands of networks and billions of computers and devices connected physically. These different systems that make up the Internet connect to each other, communicate with each other, and work together **because of agreed upon standards for how data is sent around on the Internet**. Computing devices, or routers along the Internet, help all the packets make their way to the destination where they're reassembled, if necessary, in order. This happens billions of times a day, whether you and others are sending an email, visiting a webpage, doing a video chat, using a mobile app, or when sensors or devices on the Internet talk to each other.</p>
</details>

6. (Optional)What is http and html? How do two device communicate through different layers of internet?

HTTP stands for HyperText Transfer Protocol, it's an agreement that stipulate what format of the text should be while devices are communicating with each other on the internet. It's like a simple but rigorous language each device 'speak' to each other.

HTML stands for HyperText Markup Language. It's a text language which be can be rendered by browser then displayed on the webpage.

The simplest communication case between two devices involves a request from a client and a response sent by server. Throughout the process, TCP/IP(refers to the whole Internet protocol suite) and routers ensures that data is properly divided into packets and can be delivered to the correct destination. There also has lower physical layers under the hood to handle the data transferring, like different kinds of cables, and the data on the lower layers would also be low-level data form like binary.

<details>
<summary>More details</summary>

<p>HTTP, or Hypertext Transfer Protocol, was invented by Tim Berners-Lee in the 1980s. It is a system of rules, a protocol, that serve as a link between applications and the transfer of hypertext documents. Stated differently, it's an agreement, or message format, of how machines communicate with each other. HTTP follows a simple model where a client makes a request to a server and waits for a response. Hence, it's referred to as a request response protocol. Think of the request and the response as text messages, or strings, which follow a standard format that the other machine can understand.</p>

<p>HTML stands for HyperText Markup Language and you can think of that as the language you use to tell a web browser how to make a page look.</p>

<p>So let's say you log in to Tumblr. The first thing you do is make a "POST" request. That is, a "POST" to Tumblr's login page that has some data attached to it. It has your email address, it has your password. That goes to Tumblr's server. Tumblr's server figures out that, okay, you're David. It sends a web page back to your browser that says, "Success! Logged in as David." But along with that web page, **it also attaches a little bit of invisible cookie data that your browser sees and knows to save**, and that's really important because it's really **the only way that a website can remember who you are**. All that cookie data really is is an ID card for Tumblr. It's a number that identifies you as David. Your web browser holds onto that number, and then the next time you refresh Tumblr, the next time you go to Tumblr.com, **your web browser knows to automatically attach that ID number with the request that it sends over to Tumblr's server**, so now Tumblr's server sees the request coming from your browser, sees the ID number, and knows, okay, this is a request from David.</p>

<p>Now, the internet is completely open, all of its connections are shared, and information is sent in plain text. This makes it possible for hackers to snoop on any personal information that you send over the internet, but safe websites prevent this by asking your web browser to communicate on a **secure channel** using something called Secure Sockets Layer and its successor **Transport Layer Security**. You can think of SSL and TLS as a layer of security wrapped around your communications to protect them from snooping or tampering.</p>

<p>SSL and TLS are active when you see the little lock that appears in your browser address bar next to the HTTPS. The HTTPS protocols ensure that your HTTP requests are secure and protected. When a website asks your browser to engage in a secure connection, it first provides a **digital certificate**, which is like an official ID card proving that it's the website it claims to be. Digital certificates are published by certificate authorities, which are trusted entities that verify the identities of websites and issue certificates for them, just like a government can issue IDs or passports. Now, if a website tries to start a secure connection without a properly issued digital certificate, your browser will warn you.</p>

<p>That's the basics of web browsing, the part of the internet we see day to day. To summarize,</p>

- HTTP and DNS manage the sending and receiving of HTML, media files, or anything on the web.
- What makes this possible under the hood are TCP/IP and router networks that break down and transport information in small packets.
- Those packets themselves are made up of binary, sequences of ones and zeros that are physically sent through electric wires, fiber optic cables, and wireless networks.

<p>Fortunately, **once you've learned how one layer of the internet works, you can rely on it without remembering all the details. We can trust that all those layers will work together to successfully deliver information at scale and with reliability.**</p>
</details>

7. What is a socket?

Sockets can be thought of as interfaces on different programs or processes. These programs or processes can exist in different places in the world, or at the same machine.

<details>
  <summary>More details</summary>
  <p>A socket is one endpoint of a two-way communication link between two programs running on the network. A socket is bound to a port number so that the TCP layer can identify the application that data is destined to be sent to. An endpoint is a combination of an IP address and a port number.</p>

  <p>A way to speak to other programs using standard Unix file descriptor. Also, A way to communicate within a process, between processes on the same machine, or between processes on different continents.</p>
</details>

8. What's the relationships among: client, port, server, IP address, DNS

Clients and servers are devices on the internet, every device on the internet has its unique identifier that's IP address, for example `192.168.0.1`. For humans to locate a device we usually don't know anything else than a host name like `google.com`, Then, it's the DNS(domain name system)'s responsibility to convert the hostname into IP address, DNS a distributed database system for looking for IP addresses. The port is like a subinterface of a device. A device has its IP address(`192.168.0.1`) to locate where it is, further, it also may have different interfaces(ports like `192.168.0.1:1234` or`192.168.0.1:5678`) to handle different types of incoming requests or other information.

<details>
  <summary>More details</summary>
<p>The Internet consists of millions of interconnected networks that allow all sorts of computers and devices to communicate with each other. By convention, all devices that participate in a network are provided unique labels. The general term for this type of label is an Internet Protocol Address or IP Address and is similar to a computer's phone number on the Internet. Further, IP Addresses have port numbers that add more detail about how to communicate (think of company phone extensions). </p>

<p>This mapping from URL to IP address is handled by the Domain Naming System or DNS. DNS is a distributed database which translates computer names like http://www.google.com to an IP address and maps the request to a remote server. Stated differently, it keeps track of URLs and their corresponding IP addresses on the Internet. So an address like http://www.google.com might be resolved to an IP address 197.251.230.45.</p>

```
192.168.0.1
```

When a port number is needed, the address is specified as:

```
192.168.0.1:1234
```
</details>


10. What is the statelessness of HTTP? What's the pros and cons?

Statelessness of HyperText Transfer Protocol means every request/response between devices using http is independent from each other. No state is persisted through their communication.

The pros is it makes communication more lightweight, and both the server and client don't have to accumulate more and more data as their communication goes on, neither they need to do cleanup work when their communication finished or accidentally broken.

The cons is it makes it harder to maintain a state during a session between client and server. Developers have to find a way to simulate a statefulness so the both sides -- especially the server side -- know who is sending the information.

11. What is a URL? What's the difference between a URL and an IP address?

URL stands for Uniform Resource Locator, often referred as web address, for example `exmaple.com/pictures/1`. IP address stands for Internet Protocol Address, it's the unique identifier to recognize a device's location on the internet, in the previous example of URL `exmaple.com/pictures/1`, IP address is determined by the hostname part `example.com`.

12. Recognize all components in this URL `http://www.example.com:88/home?item=book`, describe the meaning of every component.

`http`: The scheme. It always comes before the colon and two forward slashes and tells the web client how to access the resource. In this case it tells the web client to use the Hypertext Transfer Protocol or HTTP to make a request. Other popular URL schemes are ftp, mailto or git.

`www.example.com`: The host. It tells the client where the resource is hosted or located.

`:88` : The port or port number. It is only required if you want to use a port other than the default.

`/home`: The path. It shows what local resource is being requested. This part of the URL is optional.

`?item=book` : The query string, which is made up of query parameters. It is used to send data to the server. This part of the URL is also optional.

Sometimes, we may want to include a port number which the host uses to listen to HTTP requests. A URL in the form of: http://localhost:3000/profile is using the port number 3000 to listen to HTTP requests. The **default port number for HTTP** is port 80. Even though this port number is not always specified, it's assumed to be part of every URL. Unless a different port number is specified, port 80 will be used by default in normal HTTP requests. To use anything other than the default, one has to specify it in the URL.


13. In a query string `?search=ruby&results=10`, what's the different components and their meaning?

`?`	This is a reserved character that marks the start of the query string

`search=ruby`	This is a parameter name/value pair.

`&`	This is a reserved character, used when adding more parameters to the query string.

`results=10`	This is also a parameter name/value pair.

14. Does a server have to process any query string?

No. How the server uses these parameters is up to the server side application.

15. What's the pros and cons when using query strings?

Query strings have a maximum length. Therefore, if you have a lot of data to pass on, you will not be able to do so with query strings.

The name/value pairs used in query strings are visible in the URL. For this reason, passing sensitive information like username or password to the server in this manner is not recommended.

16. Why URL encoding?

URL(web address) is originally designed to only accept chars in [ASCII Character Set](https://en.wikipedia.org/wiki/ASCII) which only has limited chars in it. If a url:

- contains some special chars out of ascii for example `example.com?name=ü`
  - the char `"ü"` is not in ascii, so we use chars in ascii charset to represent the char `"ü"` as `"%C3%BC"` the url becomes `example.com?name=%C3%BC`
  - when the server receives the url, it will decode(unescape) the encoded chars `%C3%BC` back to `"ü"`
  - here the `%C3%BC` is `"ü"`'s unique [character encoding](https://en.wikipedia.org/wiki/Character_encoding#Unicode_encoding_model), based on the encoding rule, `%C3%BC` can be converted back to the char.
- or the use of the character is unsafe or the chars have special meaning. For example `%` is unsafe because it is used for encoding other characters, `&` is reserved for use as a query string delimiter, `:` is also reserved to delimit host/port components and user/password.
- So what characters can be used safely within a URL? Only alphanumeric and special characters `$-_.+!'()`, and **reserved characters when used for their reserved purposes** can be used unencoded within a URL.

![](https://upload.wikimedia.org/wikipedia/commons/a/a7/ASCII-infobox.svg)

17. What the format of encoding char in url?

https://en.wikipedia.org/wiki/Percent-encoding

Percentage sign `%` plus two hexidecimal digits.

https://en.wikipedia.org/wiki/ASCII#/media/File:USASCII_code_chart.png

19. What is `curl`?

curl is a free command line tool that is used to issue HTTP requests.

20. When we type a url in a tab bar of browser, then click enter, and we see the whole page, would there only one get request be issued by the browser?

No. If there's other resource like css, js or images, by default the browser will automatically issue new requests to download these resource. Another situation is if the first response's headers contains status 3xx and `"Location"` header, the page we `GET` is not the page we first requested for, we'd been redirected to another page.

21. What is HTTP Request Method?

It's a verb contained in the request line which indicates the type of operation we want to perform. When we need to retrieve information from the server we normally use `GET`, when we want to change data from the server we usually use `POST`.

21. What's the main difference between get and post request?

`GET` requests send data via url, url has a maximum length.

`POST` request may contain additional data(text or even files, video etc.), these data will not appear in url, they will be encapsulated in the request's HTTP body (`form data`) portion.

![](https://s3-ap-southeast-1.amazonaws.com/image-for-articles/image-bucket-1/Snip20190225_1.png)

22. Can get requests have body?

https://stackoverflow.com/questions/978061/http-get-with-request-body

Yes it can, but not recommended to do so.

23. What are request headers used for?

Request headers give more information about the client and the resource to be fetched.

24. What is status code?

Status code is a three-digit number that the server sends back after receiving a request signifying the status of the request.

25. What are response headers used for?

Response headers offer more information about the resource being sent back.

26. What is the most important components to understand an HTTP request?

- HTTP method
- path
- request headers
- message body(for POST)

27. What consists of a http request message? which parts are required which are optional?

- a request line (e.g., `GET /images/logo.png HTTP/1.1`, which requests a resource called `/images/logo.png` from the server.)
- request header fields (e.g., `Accept-Language: en`).
- an empty line
- an optional message body

Only request line is required.

28. What consists of a http response? which parts are required which are optional?

- status code
- response headers
- message body or say response body

Only status code is required.

26. What is a session id?

Its full name is session identifier, not an id of something.

Session identifier can be used by server to identify client. A session identifier is a unique token such as(`AHWqTUmEn3d-zaGnzmAvwmYNxt1Egj......`). This string identifier is first sent from server to client -- there may have a authenticating step before -- then the client will save this session id locally, normally it would be the browser's cookies. After saving, all the sequent requests send to the said server from this client(browser) will carry this session id information, as a result, the server can identify the identity of the sender. This is how we make an app seemed stateful, even http is stateless.

27. Where is the difference between session data stored in server and the session data stored in a client's browser?

Originally, session identifier was generated by server, the client only store that information in its browser. Server can validate the session id sent by the client. It can also reset(send a new one) or make the client's session id unavailable(e.g. by means of set expire time) . It's up to the server side to determine how to handle the session data sent along with a request.

<details>
  <summary>More details</summary>
  <p>A cookie is a piece of data that's sent from the server and stored in the client during a request/response cycle. Cookies or HTTP cookies, are small files stored in the browser and contain the session information. By default, most browsers have cookies enabled. When you access any website for the first time, the server sends session information and sets it in your browser cookie on your local computer. Note that the actual session data is stored on the server. The client side cookie is compared with the server-side session data on each request to identify the current session. This way, when you visit the same website again, your session will be recognized because of the stored cookie with its associated information.</p>

  <p>The most important thing is to understand that the session id is stored on the client, and it is used as a "key" to the session data stored server side. That's how web applications work around the statelessness of HTTP.</p>
</details>

28. What is Ajax?

AJAX is short for Asynchronous JavaScript and XML. Its main feature is that it allows browsers to issue requests and process responses without a full page refresh.

29. What is Same-Origin-Policy?

[Same-Origin-Policy](https://en.wikipedia.org/wiki/Same-origin_policy) is a policy that allows scripts(code) from same origin to reference or manipulate other resources of the same origin, but prevents scripts(code) of different origins from changing the resources of each other. Same origin is defined as: 1) Same protocol; 2) Same hostname; 3) Same port

For example scripts on `www.abc.com/books` can reference the js code in `www.abc.com/application.js`, notice the port here is by default `80`. But another site `www.xyz.com/books` is forbidden from accessing any resources of `www.abc.com`, vice versa.

SOP is an important concept for security.

<details>
  <summary>More details</summary>
  <p>The same-origin policy is an important concept that permits resources originating from the same site to access each other with no restrictions, but prevents access to documents/resources on different sites. Stated differently, it prevents scripts from one site from manipulating documents from another site. Documents in the same origin must have the same :**protocol, hostname and port number**. For example, the HTML document at http://www.test.com/aboutus.html can embed the contents of the JavaScript file at http://www.test.com/fancy.js because they share the same origin, have the same protocol, hostname and port number (the default port 80). Conversely, it also means documents at http://www.test.com cannot embed documents hosted on http://www.example.com because they do not share the same origin.</p>

  <p>The same-origin policy is an important guard against session hijacking attacks and serves as a cornerstone of web application security.</p>
</details>

30. What is session hijacking?

When a malicious person hijacks a user's session id of a certain web app, that person can use the session id to access the use's information on different web apps. She/he doesn't even need to know the users username and password.

31. What's the main countermeasures for session hijacking?

An approach is re-authenticate and then reset session identifier before some important operations, for example issue a money transfer, delete account etc. The reset session id will make the hijacked session id unavailable.

Another is set expiration time for session.

Finally, always use https to protect the communication on the transportation layer.

<details>
  <summary>More details</summary>
  <p>One popular way of solving session hijacking is by resetting sessions. With authentication systems, this means a successful login must render an old session id invalid and create a new one. With this in place, on the next request, the victim will be required to authenticate. At this point, the altered session id will change, and the attacker will not be able to have access. Most websites implement this technique by making sure users authenticate when entering any potentially sensitive area, such as charging a credit card or deleting the account.</p>

  <p>Another useful solution is by setting an expiration time on sessions. Sessions that do not expire give an attacker an infinite amount of time to pose as the real user. Expiring sessions after, say 30 minutes, gives the attacker a far narrower window to access the app.</p>

  <p>Finally, as we have already covered, another approach is to use HTTPS across the entire app to minimize the chance that an attacker can get to the session id.</p>

</details>

32. What is XSS? How it works?

https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)

https://en.wikipedia.org/wiki/Cross-site_scripting

XSS stands for Cross-Site-Scripting. It's a type of malicious attack that inject script(such as js code) into a webpage which will be executed later by other visitors of this page.  This is often due to directly displaying unescaped text on webpage. The attacker can use the script to access any cookies or sessions retained in client's browser then use these information for other purposes.

<details>
  <summary>More details</summary>
  <p>The final security concern we'll talk about, and a very important one for all web developers, is called Cross-site scripting, or XSS. This type of attack happens when you allow users to input HTML or JavaScript that ends up being displayed by the site directly.</p>

  <p>Attackers can craft ingeniously malicious HTML and JavaScript and be very destructive to both the server as well as future visitors of this page. For example, an attacker can use JavaScript to grab the session id of every future visitor of this site and then come back and assume their identity. It could happen silently without the victims ever knowing about it. Note that the malicious code would bypass the same-origin policy because the code lives on the site.</p>
</details>

33. What the possible solutions to defend xss?

Sanitize all user input data, especially some sensitive text like `<script>` tag. (input)

Escape all text before displaying them on webpage.(output and presentation)

If you want to use html formatted text, ask user to use more safe syntax like markdown rather than use plain html.(application layer)

36. What determines whether a request should use GET or POST as its HTTP method?

GET requests should only retrieve content from the server. They can generally be thought of as "read only" operations, however, there are some subtle exceptions to this rule. For example, consider a webpage that tracks how many times it is viewed. GET is still appropriate since the main content of the page doesn't change.

POST requests involve changing values that are stored on the server. Most HTML forms that submit their values to the server will use POST. Search forms are a noticeable exception to this rule: they often use GET since they are not changing any data on the server, only viewing it.

37. In client-sever paradigm, what's the 3 main pieces of infrastructure in the server side? What are they used for?

From a simplified view of point, there are 3 components on the server side: web server, application server, data store

- web server responds to static resource requests, since this part of work doesn't involve business logic so it needs not to reach application server
- application server is where primarily we write out business logic
- data store is where out application server can save, retrieve or change data. It may have different forms(like file, relationship database etc.) based on the needs of our app.

<details>
  <summary>More details</summary>
  <p>A web server, an application server and a data store.</p>

  <p>A web server is typically a server that responds to static assets: files, images, css, javascript, etc. These requests don't require any data processing, so can be handled by a simple web server.</p>

  <p>An application server, on the other hand, is typically where application or business logic resides, and is where more complicated requests are handled. This is where your server-side code lives when deployed.</p>

  <p>The application server will often consult a persistent data store, like a relational database, to retrieve or create data. Data stores can also be simple files, key/value stores, document stores and many other variations, as long as it can save data in some format for later retrieval and processing.</p>
</details>

38. In all layers of OSI(Open Systems Interconnection) model -- application, presentation, session, transport, network, data link, physical -- which layer HTTP is at, same question for TCP and IP? What's the relationship among these 3 protocols?

![](https://blogs.bmc.com/wp-content/uploads/2018/06/osi-model-7-layers.jpg)

Think of this in what each of these protocols are used for.
- HTTP is a protocol tells an app what the format of requests and responses should be, so it's at the application layer
- TCP used for splitting and reassembling data, so it's at the transportation layer
- IP used for locating devices on the internet, so its at the network layer

TCP is built upon IP(and all the layers below), HTTP is built upon TCP(and all the layers below).

39. What is the scheme, host, path, port. query strings in these url?

- http://exmaple.com
- https://example.com:1001/users/1?type=human
- http://localhost:4567/todos/15
- http://amazon.com:3000/products/B60HON32?qid=142952676&sr=93
<!-- - ftp://username@ftp.empire.gov/ -->
40. What are two different ways to encode a space in a query parameter?

`%20` or `+`

41. What character indicates the beginning of a URL's query parameters?

`?`

42. What character is used between the name and value of a query parameter?

`=`

43. What character is used between multiple query parameters?

`&`

44. What's the only mandatory component of a http response?

Only **status code**. headers and body are both optional.

45. What is Rack? What is a Rack Application?

Rack is a generic interface to help application developers connect to web servers, so it works with many other servers besides WEBrick.

A Rack application is a **Ruby object** (not a class) that responds to `call` method. It takes exactly one argument, the environment and returns an Array of exactly three values: The status, the headers(a hash), and the body(an Enumerable).

https://www.rubydoc.info/github/rack/rack/master/file/SPEC

46. what is a `.ru` file used for? what should we write in there in order to use it?

`ru` file is Rack's configuration file.

```ruby
# config.ru
require_relative 'app.rb'

run App.new
```

The most simple code is first require the files which contain your application, and call `run` method on your app object which responds to `call`

48. How to run a Rack app and let it listen to port 9292 on your local machine?

```
bundle exec rackup config.ru -p 9292
```

49. In a Rack app if we don't specify which web server we use, how would Rack handle this?

Note that Rack doesn’t come with its own server, but it’s smart enough to automatically try to use a server that’s already installed on your machine. If you didn’t install any server, like Puma or Thin, then Rack will just use the default server that comes with Ruby, Webrick.

Actually Rack has an [Order of precedence](https://github.com/rack/rack/blob/4bd09c04f7e6497db4a4cef169ee9099d25c3391/lib/rack/handler.rb#L48) to choose server based on a predetermined order.

50. What if we want to use another web server like `puma`?

From the previous question, in the [Order of precedence](https://github.com/rack/rack/blob/4bd09c04f7e6497db4a4cef169ee9099d25c3391/lib/rack/handler.rb#L48) of rack(`pick ['puma', 'thin', 'falcon', 'webrick']`), webrick is at the last position, so we just need to install `puma` in our project, Rack will choose `puma`.

51. What does Ruby's `ERB` library do?

The ERB library can process a special syntax that mixes Ruby into HTML, and produces a final 100% HTML string. That’s all it does.

54. What's the difference between `<% 5.inspect %>` and `<%= 5.inspect %>`

`<%= %>` - will evaluate the embedded Ruby code, and include its return value in the HTML output.
`<% %>` - will only evaluate the Ruby code, but not include the return value in the HTML output.

55. Describe how `erb` method can display dynamic result to a client's browser?

```ruby
require './advice.rb'

class HelloWorld
  def call(env)
    path = env['REQUEST_PATH']
    case path
    when '/'
      # template_string = File.read("views/index.erb")
      # erb_obj = ERB.new(template_string)
      [200, {'Content-Type' => 'text/html'}, [erb(:index)]]
    when '/advice'
      advice = Advice.new.generate
      [200, {'Content-Type' => 'text/html'}, [erb(:advice, message: advice)]]
    else
      [200, {'Content-Type' => 'text/html'}, [erb(:not_found)]]
    end
  end

  private

  def erb(filename, local = {})
    b = binding
    message = local[:message]
    template_string = File.read("views/#{filename}.erb")
    ERB.new(template_string).result(b)
  end
end
```

Take the code example above.

- On the high level `erb` method only relates to the response body part -- the third part of the return value of `call` method.
- the only purpose of `erb` method is to return a string contains 100% html code -- that's what the last line of `erb` method do `ERB.new(template_string).result(b)`, the return value is just a string
- Then take the method invocation `erb(:advice, message: advice)` as example:
  - `def erb(filename, local = {})` requires one argument `filename` that's the path of your erb file, the second argument a `hash` named `local` is optional and set `{}` as default value
  - in this case a hash  `message: advice` is passed in
  - `b = binding` will absorb various information from surrounding environment, such as variables
  - when executing `message = local[:message]` the string(represented by `advice`) would be assigned to local variable `message`, and the binding object `b` also is updated(absorb `message` variable in it)
  - `template_string = File.read("views/#{filename}.erb")` reads the file content as string by using `File::read` method
  - `ERB.new(template_string).result(b)`
    - first pass the said string(may include the syntax `<%= %>` or `<% %>`) to `ERB::new` method, it will return a [ERB object](http://ruby-doc.org/stdlib-2.6.1/libdoc/erb/rdoc/ERB.html)
    - then we call `result` method on that erb object while passing the binding object to it, so if anywhere in the erb file calls variables or methods live in that passed binding object, they can be evaluated correctly.

58. What's template file?

Templates (or view templates) are files that contain text that will be converted into HTML before being sent to a user's browser in a response. There are a lot of different templating languages, and they all provide different ways to define what HTML to generate and how to embed dynamic values.

59. Rack's basic idea can be described by using the code below:

```ruby
def run_the_stack(middlewares, app, env)
  prev_app = app

  middlewares.reverse.each do |middleware|
    prev_app = middleware.new(prev_app)
  end

  prev_app.call(env)
end

# the App
class Talk
  def call(env)
    "Can I talk to #{env[:name]}?"
  end
end

# p run_the_stack([], Talk.new, { name: "Dana"} )

# Add middleware

class Shout
  def initialize(app)
    @app = app
  end

  def call(env)
    @app.call(env).upcase
  end
end

# p run_the_stack([Shout], Talk.new, { name: "Dana"} )

#hijacking response
class Zuul
  def initialize(app)
    @app = app
  end

  def call(env)
    "There is no #{env[:name]}. Only Zuul!"
  end
end

p run_the_stack([Shout, Zuul], Talk.new, { name: "Dana"} )
```

A more likely flow and the interaction through the course can be drawn as below:

![](https://s3-ap-southeast-1.amazonaws.com/image-for-articles/image-bucket-1/Rack+flow.png)

60. How sinatra redirect a user to another page?

The `redirect` method sets the Location header in the HTTP **response** that is sent back to the client, as well as the status code to a value in the range of **3XX**, signifying redirection; codes `301` and `302` are the most commonly used for redirection. The browser confirms that the correct status `3XX` status code is there, looks at the value of this header, and then uses that header value to navigate to a new URL.

61. What's the 3 ways to insert data to `params` hash in sinatra app?

- Using url path `users/1/pictures/3`
- Using query string in URL `?query=foods`
- By submitting a form using a POST request

62. What are the basic elements of a html form?

- a `<form></form>` object
- attributes of form
  - `action` indicates request path
  - `method` indicates http method of this form
- a input related tag for example `<input>` or `<textarea>`
  - this part is actually optional, a post request could not contain form data(like a delete operation)
  - if it has, the input tag should contain `name` and `value` attributes to form a complete a valid `name/value` pair as part of the parameters sent to server
- a submit button which has the attribute `type="submit"`

63. How to consider if a file in your project is server-side code or client-side code?

Consider where the code is first executed.

64. What's a `Procfile` used for?

When using Heroku, a project's Procfile determines what processes should be started when the application boots up.

From heroku doc:

Heroku apps include a Procfile that specifies the commands that are executed by the app on startup. You can use a Procfile to declare a variety of process types, including:

- Your app’s web server
- Multiple types of worker processes
- A singleton process, such as a clock
- Tasks to run before a new release is deployed

66. (Optional)What's the main difference between Local Storage, Session Storage, and Cookies
?

https://www.quora.com/What-is-the-difference-between-sessionstorage-localstorage-and-Cookies

68. Is POST requests more secure than GET requests?

Both GET and POST send information in the form of plain text when we use HTTP. HTTPS encrypts the connect. Note, though, that there is no significant difference in security between GET and POST requests.

69. What the meaning of `__FILE__`?

The name of the current file like `example.rb`

70. If we are in a file `some/path/example.rb`, what message will be printed out by running `puts __FILE__`

`example.rb`

71. What does `File::expand_path` do? Give a simple example to demonstrate

It will expands a given path to absolute path. For example if we are in `example.rb` we can use `File.expand_path(__FILE__)` to get the full path of the file such as `/users/bob/some/path/example.rb`. If we want to go one level up, we can pass an extra argument `File.expand_path("..", __FILE__)`, then we get `/users/bob/some/path`, if we want to go two levels up then down in another path `/users/bob/some/books` we write `File.expand_path("../../books", __FILE__)`

http://ruby-doc.org/core-2.6.1/File.html#method-c-expand_path

72. What is `Dir::glob` used for? Give a simple example to demonstrate

`Dir::glob` accepts 3 arguments and an optional block. The 3 arguments are a match pattern, flags, a keyword argument `base: path`. Only the first argument is required. If no block given, it will (based on current working directory) return an array which contains all matched filenames. The optional `base` keyword argument specifies the base directory for interpreting relative pathnames instead of the current working directory.

Match pattern is a string, not a Regexp obj.

if we are under directory `/Users/xullnn/Programming/launchschool/lesson_projects/so_minus`
- `Dir::glob("data/*.txt")` use current working directory(where the file is run on the machine) as base directory, returns all `txt` filenames under `data/` dir. The returned filenames contains leading strings of the pattern string `["data/users.txt", "data/questions.txt", "data/answers.txt"]`

if we are under `/Users/xullnn`
- `Dir::glob("data/*.txt", base: "Programming/launchschool/lesson_projects/so_minus/")` would get the same return value

http://ruby-doc.org/core-2.6.1/Dir.html#method-c-glob

73. When learning Rack app, we know that a Rack app can simply be a ruby object which responds to `call` method that takes an argument `env` and returns an array Rack asked for all rack apps.

config.ru

```ruby
app_obj = Proc.new { |env| [200, {'Content-Type' => 'text/plain'}, ['Hello World.']] }

run app_obj
```

When learning sinatra, this part of low-level work is done by sinatra, we don't have to define the app instance ourselves. But when testing a sinatra app with the help of [rack-test](https://github.com/rack-test/rack-test), we need to write `ENV["RACK_ENV"] = "test"` on top of the test file.

What's the relationship between the `env` and `ENV`?

`env` is application environment variable, it contains all essential information about Rack and the incoming request, this lowercase `env` is used by our app.

```
GATEWAY_INTERFACE : CGI/1.1
PATH_INFO : /
QUERY_STRING :
REMOTE_ADDR : 127.0.0.1
REQUEST_METHOD : GET
REQUEST_URI : http://localhost:9595/
SERVER_NAME : localhost
SERVER_PORT : 9595
SERVER_PROTOCOL : HTTP/1.1
SERVER_SOFTWARE : WEBrick/1.3.1 (Ruby/2.3.1/2016-04-26)
HTTP_HOST : localhost:9595
......
rack.version : [1, 3]
rack.input : #
rack.errors : #
rack.multithread : true
......
HTTP_VERSION : HTTP/1.1
REQUEST_PATH : /
......
```

`ENV` is a lower level variable comparing to `env`, it may be used by Rack and our sinatra app. For example to indicate the value of current `RACK_ENV`, if it's `"test"` Sinatra knows the code in current file is aiming to test, so it will not start a webserver.

https://launchschool.com/posts/11a43ad4

74. In order to test a sinatra app with rack-test and Ruby minitest library, what preparation works we need to do?

List all file changes and code changes, explain the use of every change.

- rack-test is not part of ruby or our app, so we should add it to `Gemfile`
  - in `Gemfile` add `gem rack-test`
- in the test file(where we write test suit)
  - first we should tell rack and sinatra app code in this file is used for testing, so sinatra will not start another server when running code in this file.
    - in `test/app_test.rb` add `ENV["RACK_ENV"] = "test"` at the very top
  - then in order to gain access of `minitest` and `rack-test` libraries
    - add `require 'minitest/autorun'`
    - add `require 'rack/test'`
  - then require the app file we want to test
    - add `require '../app.rb'`
  - then we need to define a test class which inherits from `Minitest::Test`
    - add `class AppTest < Minitest::Test ... end`
    - because we've already required `minitest/autorun`, we can use test methods in minitest library and methods named as `def test_xxx` will be run automatically in this test class.
  - in order to gain access to all the testing helper methods provided by `rack-test`, we need to include a module
    - add `include Rack::Test::Methods` in our test class
  - in order to let all the testing helper methods provided by rack-test to be used, rack-test need a method called `app`, inside this `app` method we need to run the app instance(just like we did in `config.ru` of a bare bone rack app)
  this is from [rack-test's doc](https://github.com/rack-test/rack-test)
  ```
  def app
    app = lambda { |env| [200, {'Content-Type' => 'text/plain'}, ['All responses are OK']] }
    builder = Rack::Builder.new
    builder.run app
  end
  ```
  - but in this app --  a sinatra app -- we need to define this `app` method as
  ```ruby
  def app
    Sinatra::Application
  end
  ```

  - Then last thing, write test methods
  ```ruby
  def test_index
    get "/"
    assert_equal 200, last_response.status
    assert_equal "text/html;charset=utf-8", last_response["Content-Type"]
    assert_equal "Hello, world!", last_response.body
  end
  ```

75. Why should we isolate data from different environments? What's the general idea to do this?

In general isolating data from different environments can prevent operations under different environments from affecting the data of each other.

There are several reasons to do so.
- if we use the same file/database/space to store data used in different environments(development, test, production)
  - while some tests contain operation that will change the data, this change will impact all other environments
  - while we may change data in test and development environments, this may break some tests either
  - while the progress of test and development are not synchronous, the data structure for development and test may vary, use the same datastore may cause problem

The general idea is to use different file/database/space for different environments. The switch of file/database/space can based on the certain environment variable that will be used in all 3 environments.

76. What's the meaning of the code `last_request.env['rack.session']` in a test for a Rack app?

Fetch the value of `'rack.session'` from the last request's application environment variable `env`

77. What's the code `get "/", {}, {"rack.session" => { username: "admin"} }` doing in a test for a Rack app?

What's the difference between this and the previous mentioned code? (hint: Are they relating to request or response? They all have `rack.session` part, where does that come from?)

- `last_request.env['rack.session']` is a expression from within a test. There should have a request before this line.
  - it grasp the last reqeust's application environment variable `env`
- `get "/", {}, {"rack.session" => { username: "admin"} }` is also a expression from within a test. But instead of fetch information, this expression is simulating issuing a get request to `"/"` path.
  - There are 3 arguments passed to `get`
    - the path `"/"`, only this one is required argument
    - the parameters sent along with the request -- in this case there's no so it's an empty hash `{}`
    - the third is information that will be inject into applicaton environment variable `env`
      - here we are setting the session information we be sent in this request
      - sinatra's session is actually supplied by Rack, this can be seen from the key name `"rack.session"`
- after `get "/", {}, {"rack.session" => { username: "admin"} }`, if there is no redirection or other operations, we can actually use `last_request.env['rack.session'][:username]` to fetch the information in session.

<details>
  <summary>More details</summary>
  <p>Requests and responses in Rack are associated with a large Hash of data related to a request-response pair, called the `"env"` by Rack internally. Some of the values in this hash are used by frameworks such as Sinatra and Rails to access the path, parameters, and other attributes of the request. The session implementation used by Sinatra is actually supplied by Rack, and as a result the session object also lives in this Hash. To access it within a test, we can use `last_request.env`.</p>

  <p>There are two Hashes passed as arguments to get; the first is the Hash of parameters (which in this case is empty), and the second is values to be added to the request's Rack.env hash.</p>

  <p>Once values have been provided like this once, they will be remembered for all future calls to get or post within the same test, unless, of course, those values are modified by code within your application. This means that you can set values for the session in the first request made in a test and they will be retained until you remove them.</p>
</details>

78. In this test:

```ruby
# corresponding route handler ------------------------------------------

get "/:file_name" do
  file_name = params[:file_name]
  file_path = File.join(data_path, "#{file_name}")
  if File.file?(file_path)
    load_file_content(file_path)
  else
    session[:message] = "#{file_name} doesn't exist."
    redirect "/"
  end
end

# test file ---------------------------------------------------------
def last_request_session
  last_request.env['rack.session'] # return a hash like obj
end

def test_redirection_of_access_nonexistent_file
  get "/nonexistent.txt"
  assert_equal 302, last_response.status #1
  assert_equal "nonexistent.txt doesn't exist.", last_request_session[:message] #2

  get last_response["Location"] # 3
  assert_includes last_response.body, "nonexistent.txt doesn't exist."
end
```

The `last_request_session` holds the session of the last request, but the message `"notafile.ext does not exist."` is set in a sinatra route handler, means in a response, why this session information still remains in the last request session?(hint: how many request will happen in this case?)

The first fact is session is set server, so in the response the server side can tell a client to store a piece of session data in this case is `session[:message] = "#{file_name} doesn't exist."`, but this happened at the first response.

`redirect "/"` only set the first responses header `status` to `302` and the `"Location"` to `"/"`, also set the session data. After the browser receiving the first response, it sees the status 302 and the Location header, it will automatically issue another get request to path `"/"` while carrying that session data `session[:message] = "#{file_name} doesn't exist."`, so the second request actually contains that session data.

Can we move line `#3` between `#1` and `#2`, Why?(hint: Where does the flash message shown on browser page come from? )

No `get last_response["Location"] # 3` will trigger the server side to render erb file and evaluate the embedded ruby code there -- include `<%= session.delete(:message)%>`, the return value of `session.delete(:message)` can be displayed on the webpage of that response, but since then the `session[:message]` had gone, if we assert `last_request_session[:message]` to be equal to `"nonexistent.txt doesn't exist."`, it will fail.

78. In the test for user signin:

```ruby
# corresponding route handler ------------------------------------------

post "/users/signin" do
  if params[:username] == "admin" && params[:password] == "secret"
    session[:message] = "Welcome!"
    session[:sign_in_as] = "admin"
    redirect "/"
  else
    session[:message] = "Invalid Credentials"
    status 422
    erb :signin
  end
end
# test file ---------------------------------------------------------

def test_hard_coded_signin
  post "/users/signin", { username: "admin", password: "secret" }
  assert_equal 302, last_response.status
  get last_response["Location"]
  assert_equal "admin", last_request_session[:sign_in_as]
end
```

Why after we performing `get last_response["Location"]` the `:sigin_in_as` request session remains？

Unlike the example above the session data about `:sign_in_as` will only be deteled when signout or delete it manually, so it will retain until then.

What if we add more requests in between:

```ruby
def test_hard_coded_signin
  post "/users/signin", { username: "admin", password: "secret" }
  assert_equal 302, last_response.status
  get last_response["Location"]
  get "/"
  get "/history.txt"
  assert_equal "admin", last_request_session[:sign_in_as]
end
```

Is the final assertion still succeed? Why?

Same result, same reason.

79. Simply describe what's an one-way hash function, and how it can be used on cryptography?

An one-way hash function is a function that can convert a string which has arbitrary length to a fixed length token. And this operation is one-way, means we cannot convert this token back to the original string.

In practice we won't store users' password or other sensitive information as raw data, we only store the hashed ones. If an attacker steal this hashed data, it's almost impossible to restore the user's real password.

80. This is a code example from [bcrypt's doc](https://github.com/codahale/bcrypt-ruby):

```ruby
require 'bcrypt'

my_password = BCrypt::Password.create("my password")
#=> "$2a$12$K0ByB.6YI2/OYrB4fQOYLe6Tv0datUVf6VZ/2Jzwm879BW5K1cHey"

my_password.version              #=> "2a"
my_password.cost                 #=> 12
my_password == "my password"     #=> true  # 1
my_password == "not my password" #=> false

my_password = BCrypt::Password.new("$2a$12$K0ByB.6YI2/OYrB4fQOYLe6Tv0datUVf6VZ/2Jzwm879BW5K1cHey")
my_password == "my password"     #=> true
my_password == "not my password" #=> false
```

At the beginning, the return value of `BCrypt::Password.create("my password")` is a hashed string. But at `#1`, why it can be euqal to `"my password" `

The returned string `"$2a$12$K0ByB.6YI2/OYrB4fQOYLe6Tv0datUVf6VZ/2Jzwm879BW5K1cHey"` is not actually a string object.
```ruby
2.5.3 :006 > BCrypt::Password.create("my password").class
 => BCrypt::Password
```
So `...2Jzwm879BW5K1cHey" == "my password"` is not invocating `String#==` it is invocating instance method `BCrypt::Password#==`

81. If there's a yaml file:

example.yaml

```yaml

test:
  id: '1'
  user_id: '1'
  description: This is a test question

test:
  id: '2'
  user_id: '1'
  description: This is a test question

test:
  id: '3'
  user_id: '1'
  description: This is a test question

```

Why the code:

```ruby
require 'yaml'
Psych.load_file("./example.yaml")
```

returns a hash that only contains single key-value pair?

`{"test"=>{"id"=>"3", "user_id"=>"1", "description"=>"This is a test question"}}`

hint: notice the key `"id"`

How to fix this that we could get 3 key value pairs?

`Psych.load_file` will parse the yaml file as a hash, in this case the keys are the three `test:` in yaml file, but in Ruby a hash cannot have two same keys, so the last one will overwrite the previous ones.
