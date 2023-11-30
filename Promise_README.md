## JavaScript Promise and `then()` Method

Let's break down the example code and explain how promises work in JavaScript:

```javascript
let aPromise = new Promise((resolve, reject) => {
    let delayedFunc = setTimeout(() => {
        // Whether it resolves or rejects is unknown
        (Math.random() < 0.5) ? resolve("resolved") : reject("rejected");
    }, Math.random() * 5000); // Function will return sometime: 0-5s
});

aPromise
    .then(
        // Resolved callback
        data => {
            console.log(data);
        },
        // Rejected callback
        error => {
            console.log(error);
        }
    );
```

### Explanation:

1. **Promise Creation:**
   - `new Promise((resolve, reject) => {...})`: The `Promise` constructor takes a function as an argument, which in turn takes two parameters - `resolve` and `reject`. These parameters are functions that are provided by the JavaScript runtime and are used to handle the eventual completion of the asynchronous operation initiated by the `Promise`.

2. **Asynchronous Operation:**
   - `let delayedFunc = setTimeout(() => {...}, Math.random() * 5000);`: Inside the `Promise` constructor, there is a `setTimeout` function, simulating an asynchronous operation. The operation will either resolve or reject randomly (50/50 chance) after a random time delay between 0 and 5 seconds.

3. **Resolve and Reject:**
   - `(Math.random() < 0.5) ? resolve("resolved") : reject("rejected");`: Depending on the outcome of the asynchronous operation, either the `resolve` or `reject` function will be called. If the condition is true, it resolves the promise with the value "resolved"; otherwise, it rejects the promise with the value "rejected".

4. **Promise Handling:**
   - `.then()`: This method is called on the promise `aPromise` and takes two callback functions. The first one is executed when the promise is resolved, and the second one is executed when the promise is rejected.

   - `data => { console.log(data); }`: This is the arrow function that is mapped to the resolve parameter of the callback in the Promise Constructor. If the promise is resolved, the `data` parameter contains the resolved value, and it logs "resolved" to the console.

   - `error => { console.log(error); }`: This is the arrow function that is mapped to the reject parameter of the callback in the Promise Constructor. If the promise is rejected, the `error` parameter contains the rejection reason, and it logs "rejected" to the console.

In summary, the `Promise` constructor is used to create a promise that represents an asynchronous operation. The `resolve` and `reject` functions are provided as arguments to handle the success or failure of the operation, and the `.then()` method is used to specify what should happen when the promise is resolved or rejected.

When the asynchronous operation completes, and the `resolve` or `reject` function is called, the values passed to these functions become the values of the parameters in the corresponding callbacks specified in the `then()` method.
