# Express JS Notes
## Brief Overview of Express
* Node.js Web Framework for `building networking services` and applications

### Installation
Express can be added into any project with `npm`:

```
npm install express --save
```

### First Server
Using a `javascript file` called _`index.js`_, add the following code

```javascript
const express = require('express');
const app = express();
app.get('/', (req, res) => res.send('Hello World!'));
app.listen(3000, () => console.log('Server ready'));

```

In the __above__ code that we've added to _`index.js`_ we first import the `express` package and __`save it to`__ the express value.

Then, we create a __`new instance`__ of the `express` application (a new express application object) and saves it the the constant `app`

The next line tells the application object to listen for `GET Requests` on the `/` path by calling the `express method` (software method not request method) `get()`

And the last line tells the express application to `listen` for requests on `port 3000`

### HTTP Methods
> `Hyper Text Transfer Protocol`

Instances of the `express()` object actually have `methods (OOP METHODS)` for `each HTTP verb / method`

Those `methods accept a callback function`, which is called when a request is sent to that specific endpoint

> A `callback function` is a function `used as an input to another function`

```javascript
app.get('/', (req, res) => { /* */ });
app.post('/', (req, res) => { /* */ });
app.put('/', (req, res) => { /* */ });
app.delete('/', (req, res) => { /* */ });
app.patch('/', (req, res) => { /* */ });
```

Express provides us with two objects with these callbacks which represent the `Request` and `Response` objects.

* The __`Request`__ is the HTTP request that gives us lots of info including request `parameters`, `headers`, the request `body` and more.
* The __`Response`__ is the HTTP response that we eventually `attach information to` and `return to the client`

## Request Parameters
> The following is a list of the main `Request object parameters`
* `.app` holds a reference to the Express app obj.
* `.baseUrl` is the base path on which the app responds
* `body` contains the data submitted in the request body (must be parsed and populated manually before you can access it)
* `.cookies` contains the cookies sent by the request (requires the `cookie-parser` middleware)
* `.hostname` is the server hostname
* `.ip` is the server IP
* `.method` is the HTTP method used`
* `.params` to access the route named parameters
* `.path` is the URL path
* `.protocol` is the request protocol
* `.query` is an object containing the query strings used in the request
* `.secure` is a booolean that is true if the request is secure (uses HTTPS)
* `.signedCookies` contains the signed cookies sent by the request (needs the `cookie-parser` middleware)
* `.xhr` is true if the request is an XMLHttpRequest

### Retrieving GET Query String Params
> The query string is the section of the URL path succeeding the `?` mark E.g: (https://google.com/search?name=flavio)

In the above case the `query string parameter` is the following: 

```javascript
?name=flavio
```

Query parameters can be chained (`multiple added`) using the ampersand `&` like so:

```javascript
?name=flavio&age=35
```