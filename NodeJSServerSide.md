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
