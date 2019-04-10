1. What is internet?

2. What is a protocol?

3. What is a device's unique address under the context of the internet?

4. What is DNS?

5. How is data delivered to you reliably through the internet?

6. (Optional)What is http and html? How do two device communicate through different layers of internet?

7. (Optional)What is a socket?

8. What's the relationships among: client, port, server, IP address, DNS?

9. What is the statelessness of HTTP? What's the pros and cons?

10. What is a URL? What's the difference between a URL and an IP address?

12. In a query string `?search=ruby&results=10`, what's the different components and their meaning?

13. Does a server have to process any query string?

14. What's the pros and cons when using query strings?

15. Why URL encoding?

16. What the format of encoding char in url?

17. What is `curl`?

18. When we type a url in a tab bar of browser, then click enter, see the displayed webpage, would there only one get request be issued by the browser?

19. What is HTTP Request Method?

20. What's the main difference between get and post request?

21. Can get requests have body?

22. What are request headers used for?

23. What is status code?

24. What are response headers used for?

25. What consists of a http request message? which parts are required which are optional?

26. What consists of a http response? which parts are required which are optional?

27. What is a session id?

28. What is the difference between session data stored in server and the session data stored in a client's browser?

29. What is Ajax?

30. What is Same-Origin-Policy?

31. What is session hijacking?

32. What's the main countermeasures for session hijacking?

33. What is XSS? How it works?

34. What are the possible solutions to defend xss?

35. What determines whether a request should use GET or POST as its HTTP method?

36. In client-sever paradigm, what's the 3 main pieces of infrastructure in the server side? What are they used for?

37. In all layers of OSI(Open Systems Interconnection) model -- application, presentation, session, transport, network, data link, physical -- which layer HTTP is at, same question for TCP and IP? What's the relationship among these 3 protocols?

38. What is the scheme, host, path, port. query strings in these url?

39. What are two different ways to encode a space in a query parameter?

40. What character indicates the beginning of a URL's query parameters?

41. What character is used between the name and value of a query parameter?

42. What character is used between multiple query parameters?

43. What's the only mandatory component of a http response?

44. What is Rack? What is a Rack Application?

45. what is a `.ru` file used for? what should we write in there in order to use it?

46. How to run a Rack app and let it listen to port 9292 on your local machine?

47. In a Rack app if we don't specify which web server we use, how would Rack handle this?

48. What if we want to use another web server like `puma`?

49. What does Ruby's `ERB` library do?

51. Describe how `erb` method can display dynamic result to a client's browser based on the code example below?

52. What's template file?

53. (Optional)Rack's basic idea can be described by using the code below:

54. How sinatra redirect a user to another page?

55. What's the 3 ways to insert data to `params` hash in sinatra app?

56. What are the basic elements of a html form?

57. How to consider if a file in your project is server-side code or client-side code?

58. What's a `Procfile` used for?

59. (Optional)What's the main difference between Local Storage, Session Storage, and Cookies?

60. Is POST requests more secure than GET requests?

61. What the meaning of `__FILE__`?

64. What is `Dir::glob` used for? Give a simple example to demonstrate?

65. (Optional)When learning Rack app, we know that a Rack app can simply be a ruby object which responds to `call` method that takes an argument `env` and returns an array Rack asked for all rack apps:

66. In order to test a sinatra app with rack-test and Ruby minitest library, what preparation works we need to do?

67. Why should we isolate data from different environments? What's the general idea to do this?

68. What's the meaning of the code `last_request.env['rack.session']` in a test for a Rack app?

69. What's the code `get "/", {}, {"rack.session" => { username: "admin"} }` doing in a test for a Rack app?

70. In this test:

71. In the test for user signin:

72. (Optional)Simply describe what's an one-way hash function, and how it can be used on cryptography?

73. This is a code example from [bcrypt's doc](https://github.com/codahale/bcrypt-ruby):

74. If there's a yaml file:
