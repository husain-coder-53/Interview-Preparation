# NodeJS Interview Questions

Node.js is an open-source, cross-platform JavaScript runtime environment that enables developers to execute JavaScript on the server side. Built on Chrome's V8 engine, it allows for the creation of fast and scalable network applications using a non-blocking, event-driven architecture. This makes it particularly suitable for handling multiple concurrent connections efficiently, allowing developers to use JavaScript across both client-side and server-side development without needing to learn a different language.

## Questions and Answers

<details>
<summary><strong style="font-size: 1.2em;">1. What is Node.js?</strong></summary>

Node.js is an open-source, cross-platform JavaScript runtime environment that allows you to run JavaScript on the server side. It is built on Chrome's V8 JavaScript engine and uses an event-driven, non-blocking I/O model, making it lightweight and efficient.

```javascript
// Example of a simple Node.js server
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(3000, () => {
  console.log('Server running at http://localhost:3000/');
});
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">2. What are the advantages of using Node.js?</strong></summary>

Some advantages of using Node.js include:
- **Non-blocking I/O**: Allows handling multiple connections simultaneously.
- **Single Programming Language**: JavaScript can be used for both client-side and server-side development.
- **Large Ecosystem**: NPM (Node Package Manager) provides access to a vast number of libraries and tools.
- **Scalability**: Built to handle high traffic and large-scale applications.

</details>

<details>
<summary><strong style="font-size: 1.2em;">3. Explain the event-driven architecture in Node.js.</strong></summary>

Node.js uses an event-driven architecture, where events are emitted and listened to by event handlers. This allows for asynchronous programming, enabling the server to handle multiple requests without blocking.

```javascript
const EventEmitter = require('events');
const myEmitter = new EventEmitter();

myEmitter.on('event', () => {
  console.log('An event occurred!');
});

myEmitter.emit('event'); // Logs: An event occurred!
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">4. What are middleware functions in Node.js?</strong></summary>

Middleware functions are functions that have access to the request object (req), the response object (res), and the next middleware function in the application’s request-response cycle. They can perform operations such as modifying requests, ending requests, or calling the next middleware.

```javascript
const express = require('express');
const app = express();

app.use((req, res, next) => {
  console.log('Request received');
  next(); // Pass control to the next middleware
});
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">5. How does Node.js handle asynchronous operations?</strong></summary>

Node.js handles asynchronous operations using callbacks, promises, and async/await syntax. The event loop allows Node.js to perform non-blocking I/O operations by offloading operations to the system kernel whenever possible.

```javascript
// Using a promise for asynchronous operation
const fs = require('fs').promises;

fs.readFile('file.txt', 'utf8')
  .then(data => console.log(data))
  .catch(err => console.error(err));
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">6. What is NPM?</strong></summary>

NPM (Node Package Manager) is a package manager for JavaScript that comes with Node.js. It allows developers to install, share, and manage dependencies in their projects.

```bash
# Command to install a package using NPM
npm install express
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">7. Explain the concept of streams in Node.js.</strong></summary>

Streams are objects that allow you to read data from a source or write data to a destination in a continuous manner. There are four types of streams in Node.js: Readable, Writable, Duplex, and Transform streams.

```javascript
const fs = require('fs');

// Creating a readable stream
const readableStream = fs.createReadStream('file.txt');

readableStream.on('data', (chunk) => {
  console.log(`Received ${chunk.length} bytes of data.`);
});
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">8. What is the purpose of the package.json file?</strong></summary>

The `package.json` file is used to manage project dependencies, scripts, metadata about the project (like name and version), and configuration settings for various tools.

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "dependencies": {
    "express": "^4.17.1"
  },
  "scripts": {
    "start": "node index.js"
  }
}
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">9. How do you create a simple REST API using Express?</strong></summary>

You can create a simple REST API using Express by defining routes that respond to different HTTP methods (GET, POST, PUT, DELETE).

```javascript
const express = require('express');
const app = express();
app.use(express.json());

app.get('/api/items', (req, res) => {
  res.send([{ id: 1, name: 'Item One' }]);
});

app.post('/api/items', (req, res) => {
  const newItem = req.body;
  res.status(201).send(newItem);
});

app.listen(3000, () => {
  console.log('Server running on port 3000');
});
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">10. What is the difference between synchronous and asynchronous programming in Node.js?</strong></summary>

Synchronous programming blocks further execution until the current operation completes, while asynchronous programming allows other operations to run without waiting for the current operation to finish.

**Hint:** 💡 Asynchronous programming is essential in Node.js for handling I/O operations efficiently.

```javascript
// Synchronous example
const fs = require('fs');
const data = fs.readFileSync('file.txt', 'utf8'); // Blocks execution
console.log(data);

// Asynchronous example
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data); // Non-blocking execution
});
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">11. What is an error-first callback in Node.js?</strong></summary>

Error-first callbacks are a convention used in Node.js where the first argument of the callback function is reserved for an error object (if any), followed by any additional data.

```javascript
fs.readFile('file.txt', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">12. Explain how middleware works in Express.</strong></summary>

Middleware functions are functions that have access to the request object (`req`), response object (`res`), and the next middleware function in the application's request-response cycle. They can perform operations like modifying requests or responses or ending requests.

```javascript
app.use((req, res, next) => {
  console.log(`Request URL: ${req.url}`);
  next(); // Pass control to the next middleware
});
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">13. How do you handle errors in Express?</strong></summary>

Errors in Express can be handled using middleware specifically designed for error handling by defining an error-handling middleware function with four arguments.

```javascript
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">14. What are environment variables and how do you use them in Node.js?</strong></summary>

Environment variables are variables outside your application that can influence its behavior without changing code directly. In Node.js, you can access them using `process.env`.

```javascript
// Accessing environment variable
const dbPassword = process.env.DB_PASSWORD;
console.log(`Database Password: ${dbPassword}`);
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">15. Explain how to use Promises in Node.js.</strong></summary>

Promises provide a way to handle asynchronous operations more effectively than callbacks by representing a value that may be available now or in the future.

```javascript
const fetchData = () => {
   return new Promise((resolve, reject) => {
     setTimeout(() => {
       resolve("Data fetched!");
     }, 1000);
   });
};

fetchData().then(data => console.log(data)); // Logs after one second
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">16. What is clustering in Node.js?</strong></summary>

Clustering allows you to take advantage of multi-core systems by creating child processes that share server ports and handle incoming requests concurrently.

```javascript
const cluster = require('cluster');
const http = require('http');
const numCPUs = require('os').cpus().length;

if (cluster.isMaster) {
   for (let i = 0; i < numCPUs; i++) {
     cluster.fork();
   }
} else {
   http.createServer((req, res) => {
     res.writeHead(200);
     res.end('Hello World\n');
   }).listen(8000);
}
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">17. How do you implement file uploads in Node.js?</strong></summary>

File uploads can be handled using middleware like `multer`, which processes multipart/form-data requests.

```javascript
const multer = require('multer');
const upload = multer({ dest: 'uploads/' });

app.post('/upload', upload.single('file'), (req, res) => {
   res.send(`File uploaded successfully!`);
});
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">18. What is CORS and how do you enable it in a Node.js application?</strong></summary>

CORS (Cross-Origin Resource Sharing) is a security feature that restricts web pages from making requests to a different domain than the one that served the web page. You can enable CORS in your Node.js application using the `cors` middleware.

```javascript
const cors = require('cors');

app.use(cors()); // Enable CORS for all routes

// Or configure specific routes:
app.use('/api', cors());
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">19. Explain what REPL stands for and its use in Node.js.</strong></summary>

REPL stands for Read-Eval-Print Loop; it provides an interactive shell where you can execute JavaScript commands directly within a Node.js environment.

```bash
# Start REPL by running this command in terminal:
node

# Now you can execute JavaScript commands directly:
> console.log("Hello from REPL!");
Hello from REPL!
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">20. How do you manage dependencies in a Node.js project?</strong></summary>

Dependencies are managed using NPM (Node Package Manager). You can install packages locally or globally and specify them in your `package.json` file for easy management.

```bash
# Install a package locally
npm install express

# Install a package globally
npm install -g nodemon

# View installed packages
npm list --depth=0

# Remove a package
npm uninstall express
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">21. How can I effectively debug APIs in Node.js, and what strategies can I use to minimize I/O blocking issues? Additionally, how much time does blocking typically take, and what impact does it have on performance?</strong></summary>

### How to Effectively Debug APIs in Node.js

Debugging APIs in Node.js can be challenging due to the asynchronous nature of JavaScript. Here are strategies and tools you can use to debug effectively:

1. **Use Console Logging**: 
   - Start with simple `console.log()` statements to trace the flow of your application. This is often the quickest way to identify where things might be going wrong.

   ```javascript
   app.get('/api/data', (req, res) => {
     console.log('Received request for data');
     // Fetch data logic here
     res.send(data);
   });
   ```

2. **Node.js Built-in Debugger**:
   - Use the built-in debugger by running your application with the `--inspect` flag. This allows you to connect to Chrome DevTools for a more interactive debugging experience.

   ```bash
   node --inspect app.js
   ```

   - Open Chrome and navigate to `chrome://inspect` to start debugging.

3. **Using Visual Studio Code**:
   - Set up a launch configuration in VS Code for debugging Node.js applications. Create a `launch.json` file in your `.vscode` folder.

   ```json
   {
     "version": "0.2.0",
     "configurations": [
       {
         "type": "node",
         "request": "launch",
         "name": "Debug Current File",
         "program": "${file}"
       }
     ]
   }
   ```

4. **Conditional Breakpoints**:
   - Use conditional breakpoints in your IDE to pause execution only when certain conditions are met, which can help narrow down issues.

5. **Error Handling Middleware**:
   - Implement error-handling middleware in Express to catch errors globally and log them for easier debugging.

   ```javascript
   app.use((err, req, res, next) => {
     console.error(err.stack);
     res.status(500).send('Something broke!');
   });
   ```

### Minimizing I/O Blocking Issues

I/O blocking occurs when a synchronous operation takes too long, causing other operations to wait. Here are strategies to minimize I/O blocking:

1. **Use Asynchronous Methods**: 
   - Always prefer asynchronous methods for I/O operations (like reading files or making database queries) using callbacks, promises, or async/await.

   ```javascript
   const fs = require('fs').promises;

   async function readFile() {
     try {
       const data = await fs.readFile('file.txt', 'utf8');
       console.log(data);
     } catch (err) {
       console.error(err);
     }
   }
   ```

2. **Cluster Your Application**:
   - Use clustering to take advantage of multi-core systems by creating multiple instances of your application that can handle requests concurrently.

   ```javascript
   const cluster = require('cluster');
   const http = require('http');
   const numCPUs = require('os').cpus().length;

   if (cluster.isMaster) {
     for (let i = 0; i < numCPUs; i++) {
       cluster.fork();
     }
   } else {
     http.createServer((req, res) => {
       res.writeHead(200);
       res.end('Hello World\n');
     }).listen(8000);
   }
   ```

3. **Limit Blocking Code**:
   - Identify and refactor any blocking code that could delay responses. For example, avoid using synchronous file system methods like `fs.readFileSync()` in your API routes.

### Impact of Blocking on Performance

Blocking operations can significantly degrade the performance of a Node.js application:

- **Time Taken**: The time taken for blocking operations varies based on the operation itself—reading large files or making slow database queries can block the event loop for milliseconds to seconds.
  
- **Performance Impact**: When the event loop is blocked, no other requests can be processed, leading to increased response times and a poor user experience. For high-traffic applications, even brief periods of blocking can result in noticeable delays.

### Conclusion

Effective debugging in Node.js involves using various tools and techniques such as logging, built-in debuggers, and IDE support. To minimize I/O blocking issues, always opt for asynchronous programming patterns and consider clustering your application for better performance. Understanding how blocking impacts performance is crucial for building efficient APIs.

</details>

---

*Prepared by Husain Amravatiwala*
