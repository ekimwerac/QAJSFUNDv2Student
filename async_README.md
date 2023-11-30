In the provided code, there are three asynchronous functions (`asyncFunc1`, `asyncFunc2`, and `asyncFunc3`) and an asynchronous function called `doThings` that orchestrates the execution of these functions in a sequential manner using `await`. Here's a breakdown of the code:

1. **asyncFunc1, asyncFunc2, asyncFunc3:**
   - Each of these functions returns a `Promise` that resolves after a specific timeout using `setTimeout`.
   - Inside the `setTimeout` callback, a message is logged to the console, and then the promise is resolved.

```javascript
async function asyncFunc1() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            console.log('Async function 1');
            resolve();
        }, 3000);
    });
}

async function asyncFunc2() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            console.log('Async function 2');
            resolve();
        }, 2000);
    });
}

async function asyncFunc3() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            console.log('Async function 3');
            resolve();
        }, 1000);
    });
}
```

2. **doThings:**
   - This function is marked as `async`, and it calls `asyncFunc1`, `asyncFunc2`, and `asyncFunc3` in sequence using `await`.
   - The `await` keyword is used to pause the execution of the function until the promise returned by the asynchronous function resolves.
   - The functions are called one after the other, and each one is awaited, ensuring that they execute sequentially.

```javascript
async function doThings() {
    await asyncFunc1();
    await asyncFunc2();
    await asyncFunc3();
    return "All done";
}
```

3. **Calling doThings:**
   - The `doThings` function is invoked, and since it returns a promise (due to the `async` keyword), you can use `.then` to handle the result when all the asynchronous operations are completed.
   - In this case, the final result is the string "All done."

```javascript
doThings().then(console.log);
```

When you run this code, you'll see the messages from each asynchronous function logged to the console in the order they are called, with delays reflecting the timeout values specified in each `setTimeout` call. The output will be something like:

```
Async function 1
Async function 2
Async function 3
All done
```

If you remove the `await` statements in the `doThings` function, the asynchronous functions (`asyncFunc1`, `asyncFunc2`, and `asyncFunc3`) will be invoked without waiting for the completion of each one before moving on to the next. This changes the behavior of the program, making the asynchronous functions run concurrently instead of sequentially.

Here's the modified `doThings` function without `await`:

```javascript
async function doThings() {
    asyncFunc1(); // No await
    asyncFunc2(); // No await
    asyncFunc3(); // No await
    return "All done";
}
```

In this case:

- All three asynchronous functions (`asyncFunc1`, `asyncFunc2`, and `asyncFunc3`) will start executing immediately.
- The function `doThings` won't wait for the completion of `asyncFunc1` before starting `asyncFunc2`, and similarly, it won't wait for `asyncFunc2` before starting `asyncFunc3`.
- The function will return "All done" almost immediately, before any of the asynchronous functions have completed.

This means that the messages logged by the asynchronous functions may appear in a mixed order, and "All done" will likely be logged before any of the asynchronous operations have finished.

Using `await` ensures that each asynchronous operation is completed before moving on to the next one, maintaining a sequential flow. Removing `await` can be useful in scenarios where you want to start multiple asynchronous operations concurrently and don't need to wait for their completion in a specific order. However, in this particular example, where you have a sequence of operations, using `await` is more appropriate to control the flow of execution.

### Running This as an App ###

Let's assume you want to create a directory structure for a Node.js application. Here's a basic setup:

### Directory Structure:

```
myAsyncApp/
|-- src/
|   |-- main.js
|-- package.json
|-- .vscode/
|   |-- settings.json
```

1. **`myAsyncApp/`**: Root directory for your project.

2. **`src/`**: Directory for your source code.

3. **`main.js`**: Main JavaScript file where you put your application code.

4. **`package.json`**: Configuration file for Node.js projects.

5. **`.vscode/`**: Directory for VSCode-specific settings.

6. **`settings.json`**: VSCode settings file.

### Setting up the files:

#### 1. `main.js`:

```javascript
// src/main.js
async function asyncFunc1() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log('Async function 1');
            resolve();
        }, 3000);
    });
}

async function asyncFunc2() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log('Async function 2');
            resolve();
        }, 2000);
    });
}

async function asyncFunc3() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log('Async function 3');
            resolve();
        }, 1000);
    });
}

async function doThings() {
    await asyncFunc1();
    await asyncFunc2();
    await asyncFunc3();
    return "All done";
}

doThings().then(console.log);
```

#### 2. `package.json`:

```json
{
    "name": "my-async-app",
    "version": "1.0.0",
    "main": "src/main.js",
    "scripts": {
        "start": "node src/main.js"
    },
    "devDependencies": {},
    "dependencies": {}
}
```

#### 3. `.vscode/settings.json`:

```json
{
    "node.defaultProgram": "node"
}
```

### Installing Dependencies:

1. Open a terminal in the root directory (`myAsyncApp`) and run:

   ```bash
   npm init -y
   ```

   This will create a `package.json` file.

2. Install Node.js dependencies:

   ```bash
   npm install
   ```

### Running the Application:

1. Open the terminal in VSCode.

2. Run the application:

   ```bash
   npm start
   ```

You should see the output of your asynchronous functions in the console.

This is a basic structure to get you started.

