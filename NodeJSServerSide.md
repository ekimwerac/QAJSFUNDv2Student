Node.js is a runtime environment that allows you to execute JavaScript code on the server side. It's commonly used for building scalable network applications and is particularly well-suited for building web servers. Below, is a simple example of how Node.js can be used to create a basic web server.

### Example: Creating a Simple Web Server with Node.js

1. **Install Node.js:**
   First, make sure you have Node.js installed on your machine. You can download it from the official website: [Node.js](https://nodejs.org/).

2. **Create a Project Folder:**
   Create a new folder for your project. Open a terminal, navigate to the folder, and initialize a new Node.js project by running the following command:
   ```bash
   npm init -y
   ```

3. **Install Express:**
   Express is a popular web framework for Node.js. Install it using the following command:
   ```bash
   npm install express
   ```

4. **Create a Server File:**
   Create a file named `server.js` in your project folder. Add the following code to create a basic web server using Express:
   ```javascript
   const express = require('express');
   const app = express();
   const port = 3000;

   // Define a route
   app.get('/', (req, res) => {
       res.send('Hello, World!');
   });

   // Start the server
   app.listen(port, () => {
       console.log(`Server listening at http://localhost:${port}`);
   });
   ```

5. **Run the Server:**
   In the terminal, run the server by executing the following command:
   ```bash
   node server.js
   ```

6. **Access the Web Application:**
   Open your web browser and navigate to `http://localhost:3000`. You should see the message "Hello, World!".

In this example, we use Node.js to create a simple web server using the Express framework. The server listens on port 3000, and when you access the root path (`/`) in your browser, it responds with "Hello, World!". This is a very basic example, but it illustrates how Node.js can be used to handle web requests and serve dynamic content on the server side of a web application.

In the context of a web server built using Node.js and Express, `req` and `res` are standard names for the request and response objects, respectively. These objects contain information about the incoming request from the client and provide methods and properties to send a response back to the client.

Here's an expanded explanation:

1. **`req` (Request Object):**
   - The `req` object represents the HTTP request that the server receives from the client. It contains information about the request, such as the URL, request method (GET, POST, etc.), headers, parameters, query parameters, and more.
   - In the example code:
     ```javascript
     app.get('/', (req, res) => {
         // Handle the request using the req object
     });
     ```
     Here, `app.get` is defining a route for the HTTP GET method on the root path (`/`). The arrow function `(req, res) => { /* ... */ }` is a callback function that will be executed when a GET request is made to the root path. The `req` parameter in this function will be an instance of the request object, allowing you to access details about the incoming request.

2. **`res` (Response Object):**
   - The `res` object represents the HTTP response that the server will send back to the client. It provides methods to set the HTTP status code, headers, and send the response body.
   - In the example code:
     ```javascript
     app.get('/', (req, res) => {
         res.send('Hello, World!');
     });
     ```
     Here, `res.send('Hello, World!')` is used to send the string 'Hello, World!' as the response body. The `res` object has various other methods for sending different types of responses, such as `res.json()` for sending JSON, `res.sendFile()` for sending files, etc.

The order of these parameters is crucial. Express follows the convention of passing the request object (`req`) first and the response object (`res`) second to the route handler callback function.

So, in summary, when a request is made to the server, Express calls the route handler function with the `req` and `res` objects as arguments, allowing you to access information about the incoming request and send an appropriate response back to the client.