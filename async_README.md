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
