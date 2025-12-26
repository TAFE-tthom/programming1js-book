# Server-side Rendering and Frameworks

We will be exploring writing and building a server using `express`. `express` is used to build APIs and simple servers.

## Express

Welcome to your first segment of writing some server application logic. After installing the dependency using `npm install express`, you will have noticed that it has created a `node_modules` folder in which `expressjs` will be contained inside there.

With a simple `Express` application, the following concepts are critical in understanding the lesson/domain.

* HTTP method - A method is part of the `HTTP` protocol, it is used to outline the kind of request you are performing. Common HTTP Methods are: GET, POST, PUT, DELETE.

* Port - A port, is a virtual port or application port, when a server is running (your express application), it needs to listen on a port for incoming connections. This allows the operating system to direct network traffic to the application.

* endpoint - An endpoint is typically a `HTTP` URL, similar to what you put into the browser.

* `app` - This is a common variable inside express applications that will usually have a `dictionary` that holds onto different response callbacks.

* `request` - A request is a connection and data associated with it to a webserver. A request is made by the web-browser or application

* `response` - A response is data sent to ther requester. This is the response from the webserverto to the web-browser or application.

### Express - Making your server

To get started with `express`, you need to create an `npm` package using `npm init` inside a folder which is appropriately named.

Example:

```
> mkdir firstapp
> cd firstapp
> npm init
```

Afterwards, you need to install it using `npm install express`, this will install the framework that will enable you create an express app alongside assigning a port to the application.

A basic layout of a simple express app is:

```js
const express = require('express')

const app = express(); //Application that holds onto callbacks that are associated
  //to endpoints
  
const PORT = 3000; //default port number

app.listen(port, function() { // Anonymous function called when app starts listening
  console.log("Application has started, listening on port: " + PORT);
})

```


### Express - Routes/Endpoints

A route or endpoint is the suffix added to a domain. Typically webservers are given a domain name which is associated to their IP address. The association between the domain name and the IP address gets resolved by a DNS (Domain Name Server).

Anytime you type in `tafensw.edu.au` or `google.com` into the browser URL bar, if the address is not known, the DNS will resolved what IP address you will receive. A common domain that you always have access on your own machine is `localhost` which refers your own computer and maps to the IP address `127.0.0.1`.

With `endpoints`, what comes after the domain typically is a resource that a browser wants to access (hence Uniform Resource Locator is what URL stands for).

\newpage

So, lets consider what an endpoint looks like with `localhost` of an app listening on port 3000:

* `localhost:3000/hello` - `/hello` is the endpoint which will be a resource.

* `localhost:3000/file/lesson.zip` - `/file/lesson.zip` is an endpoint in which likely the implication is that the browser is accessing a zip file.

Within express, this can be defined like so:

```js
// '/helloworld' - endpoint
// function(req, res) { ... } - function ran on response
// .get matches the HTTP method
app.get('/helloworld', function(req, res) {
  
  res.send('Hello World'); // Sends 'Hello World' to the requester
});
```


### Express - Route Parameters (ALL)

Now that we can create endpoints, this can be extended to support parameters. Specifically, as part of designing our WebAPI, our endpoints can use parts of the endpoint as an argument for our response callback.

To demonstrate this, we can create a simple greeting endpoint that allows for inputting a name as an argument.

﻿
```js
// '/hello/:name' - endpoint
// function(req, res) { ... } - function ran on response
app.get('/hello/:name', function(req, res) {
  const name = req.params.name; //name in params matches the :name part
  res.send('Hello ' + name);  
});
```

We can test this endpoint by using the command `curl` that allows for querying the endpoint and getting a set of results from that endpoint.

For example, your terminal you can do the following:

```
> curl http://localhost:3000/hello/Jake
Hello Jake
```

`curl` is a simple tool that allows for querying webservers. We can also use this command for sending more complex data that the browser would normally do.

\newpage 

### Express - Form Body (POST, PUT, DELETE)

A regular scenario when interacting with a webserver is being able to package data that would normally be part of a form on a webpage. We will be using the `POST` http method in this case.

Lets take the scenario that we are creating an endpoint which will allow us to accept a JSON object (Javascript Object Notation object) and interact with it.

```js
// We want to handle JSON data
app.use(express.json()); //Allows us to interpret

const allLinks = []; //Array we can add to

// '/link/add/' - endpoint
// function(req, res) { ... } - function ran on response
// .post maps to POST http method
app.post('/link/add', function(req, res) {
  const data = req.body; //Allows getting data from it

  // Prints out fields from the object
  console.log(data.name)
  console.log(data.description);

  allLinks.push({
    name: data.name,
    description: data.description
  })

  res.send({ message: 'Link Added!' });
});
```

The above snippet allows us to construct a handler that will respond post data and handle JSON data sent to it. We can test it using the following:


```
> curl -XPOST -H 'Content-Type: application/json' \
--data '{ "name" : "mdn", "description": "Mozilla Developer Network"}'\
 http://localhost:3000/link/add

{ "message": "Link Added!" }
```

We can observe from the server-side, the output from the `console.log` statements but from the client's perspective (curl), we can see what the server sent back.

