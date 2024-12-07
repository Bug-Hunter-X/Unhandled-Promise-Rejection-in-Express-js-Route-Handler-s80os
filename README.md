# Unhandled Promise Rejection in Express.js Route Handler

This repository demonstrates a common error in Node.js Express.js applications: improperly handling asynchronous operations within route handlers.  The `bug.js` file shows an example of a server that can fail silently or throw an unhandled promise rejection. The `bugSolution.js` demonstrates the corrected implementation.

## Problem

The `bug.js` example uses `then` and `catch` to handle the promise returned by `someAsyncOperation`. However, if an error occurs during the asynchronous operation, only the error is logged to the console. No appropriate HTTP error response is sent to the client.  This leads to a poor user experience and can be difficult to debug.  In addition, unhandled promise rejections can cause the server to crash under load.

## Solution

The `bugSolution.js` file corrects this by using `async/await` and handling errors directly within the `try...catch` block.  This ensures that an appropriate HTTP error response (e.g., a 500 Internal Server Error) is always sent to the client, even if an error occurs.