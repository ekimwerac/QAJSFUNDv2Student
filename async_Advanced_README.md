Let's modify the async example to demonstrate how multiple asynchronous functions can independently collect data, and then how the promises returned by these functions can be used in the application logic.

Consider a scenario where each asynchronous function fetches data from different sources. The collected data will then be used once all the asynchronous operations are complete. Here's an extended example:

```javascript
// src/main.js

// Simulating asynchronous data fetching from different sources
async function fetchDataFromSource1() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log('Fetching data from source 1');
            resolve({ source1Data: 'Data from source 1' });
        }, 3000);
    });
}

async function fetchDataFromSource2() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log('Fetching data from source 2');
            resolve({ source2Data: 'Data from source 2' });
        }, 2000);
    });
}

async function fetchDataFromSource3() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log('Fetching data from source 3');
            resolve({ source3Data: 'Data from source 3' });
        }, 1000);
    });
}

async function doThings() {
    // Start fetching data from different sources concurrently
    const promise1 = fetchDataFromSource1();
    const promise2 = fetchDataFromSource2();
    const promise3 = fetchDataFromSource3();

    // Wait for all promises to resolve using Promise.all
    const [dataFromSource1, dataFromSource2, dataFromSource3] = await Promise.all([promise1, promise2, promise3]);

    // Now you have the data from all sources, and you can use it in your application logic
    console.log('All data collected:');
    console.log(dataFromSource1);
    console.log(dataFromSource2);
    console.log(dataFromSource3);

    return "All done";
}

doThings().then(console.log);
```

In this example:

- Three asynchronous functions (`fetchDataFromSource1`, `fetchDataFromSource2`, and `fetchDataFromSource3`) simulate fetching data from different sources with different delays.
- In the `doThings` function, all three functions are invoked concurrently, and `Promise.all` is used to wait for all promises to resolve.
- Once all the promises are resolved, the data from each source is available, and you can use it in your application logic.

This structure allows you to efficiently fetch data from multiple sources concurrently and process the results once all the data is available.

## more on resolve() ##

In JavaScript promises, the `resolve` function is a callback provided by the promise constructor. It is not explicitly passed as an argument but rather is a function that you call to fulfill the promise with a certain value. The `resolve` function is part of the promise contract and is used to indicate that the asynchronous operation represented by the promise has completed successfully, and it passes the result (or value) of that operation.

In the examples provided, `resolve` is not a placeholder; it's a function provided by the `Promise` constructor. Here's a breakdown:

1. **Basic Example:**

   ```javascript
   return new Promise((resolve, reject) => {
       setTimeout(() => {
           console.log('Async operation completed');
           resolve('Result of async operation');
       }, 2000);
   });
   ```

   In this example:
   - The `resolve` function is part of the promise executor function, which is the function passed to the `Promise` constructor.
   - The `resolve` function is called inside the `setTimeout` callback after the asynchronous operation is completed.
   - The value `'Result of async operation'` is passed to the `resolve` function, indicating that this is the result of the asynchronous operation.

2. **Data Fetching Example:**

   ```javascript
   async function fetchDataFromSource1() {
       return new Promise((resolve) => {
           setTimeout(() => {
               console.log('Fetching data from source 1');
               resolve({ source1Data: 'Data from source 1' });
           }, 3000);
       });
   }
   ```

   Here, `resolve` is still a function provided by the `Promise` constructor. When the asynchronous operation (simulated data fetching) is completed, `resolve` is called with the fetched data, indicating that the promise is fulfilled with this data.

So, to answer your question, 'is resolve a placeholder for a callback?': `resolve` is not a placeholder for a callback; it is a function provided by the promise infrastructure itself. You use `resolve` to fulfill the promise when the asynchronous operation represented by the promise is successfully completed, and you want to provide the result of that operation.

The `reject` function, which is also provided by the promise constructor, is used to indicate that the operation has failed and to provide an error reason if necessary. In the examples you provided, error handling is minimal, but in a real-world application, you would typically include appropriate error handling using `reject` as well.
