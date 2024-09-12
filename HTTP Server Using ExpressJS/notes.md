https://www.youtube.com/watch?v=od4hT9abIMQ

# Which one to choose Node / Express JS for creating HTTP server

## Node.js
>Node.js is a runtime environment that allows you to run JavaScript on the server-side. It has a built-in http module, which you can use to create a basic HTTP server.

#### Features:
> Low-level control: You manually handle requests, parse URLs, set headers, and manage responses.

> Limited abstractions: You need to handle routing, middleware, and other web functionalities from scratch.

#### Use case: 
> Great for simple servers where you want complete control over how requests are handled.
> Performance is critical, and you want to avoid the overhead of additional libraries like Express.

```js
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
//   Difference between response.setHeader and response.writeHead  -- check
  res.end('Hello, World!\n');
});

server.listen(3000, () => {
  console.log('Server running at http://localhost:3000/');
});

```

### Summary:
>  http module: Provides the tools for creating an HTTP server.
    
> createServer(): Creates the server and defines how it will handle incoming requests.
    
> statusCode: Specifies the success or error state of the response.
    
> setHeader(): Sets headers like Content-Type to tell the client how to interpret the response.
    
> end(): Signals the end of the response and sends it to the client.
    listen(): Starts the server on a specific port, waiting for requests.

---------------------------------------------------------------------------------------------------------

## Express.js
> Express.js is a web application framework built on top of Node.js. It simplifies the process of building web servers by providing higher-level abstractions and features.

#### Features:
> Routing: It comes with built-in routing mechanisms, making it easy to define URL paths for different endpoints.

> Middleware: Allows you to easily add layers of processing for requests and responses (e.g., logging, authentication).

> Simplified response handling: You can easily send JSON, render templates, and handle HTTP status codes.

#### Use case: 
> Suitable for building full-featured web applications and APIs where you need middleware, routing, and other high-level features.

```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello, World!');
});

app.listen(3000, () => {
  console.log('Server running at http://localhost:3000/');
});
```


### Summary:

> express: The Express.js module provides a framework for building web applications and APIs.
    
> app: The Express application instance that defines how the server will respond to requests.
    
> app.get(): A method for defining a route that responds to HTTP GET requests. In this case, it handles requests to the root URL ('/').

> req and res: The request and response objects used to handle incoming requests and send responses.

> res.send(): Sends a response to the client. Express simplifies response handling with built-in methods like send().

> app.listen(): Starts the server and listens for requests on a specific port (3000 in this case).

> Callback functions: Both for routes and the server startup, these functions define the logic that gets executed when specific events (requests or server start) occur.

------------------------------------------------------------------------------------------------------------
### Key Differences:

##### Level of abstraction: 
> Node.js's HTTP server is low-level, while Express.js abstracts many of the tedious tasks of handling HTTP requests.
    
##### Flexibility vs Simplicity: 
> Node.js offers more flexibility and control, but Express.js is much simpler to use for common web server tasks.
    
##### Middleware: 
> Express.js supports middleware, which allows you to easily add functionality to your app without modifying your core logic.


### Conclusion:
> Express.js is generally the better choice for most web development projects due to its simplicity, built-in features, and extensibility. For more complex applications or those requiring middleware and routing, Express saves time and effort. Node.js’s native HTTP server might be preferred only for very minimalistic or performance-critical scenarios.


### routes and middleware:

> Routing is the path in which client requests talk to applications' endpoints. There are two ways in which routing can be implemented in node js, with Framework and without Framework. Many frameworks can be used with node js to run applications and servers but the most widely used one is Express

> Middleware allows you to run code before a request is completed. Then, based on the incoming request, you can modify the response by rewriting, redirecting, modifying the request or response headers, or responding directly. Middleware runs before cached content and routes are matched.