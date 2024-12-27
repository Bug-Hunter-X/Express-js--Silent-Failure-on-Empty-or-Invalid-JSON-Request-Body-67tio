# Express.js Silent JSON Parsing Failure

This repository demonstrates a common yet subtle bug in Express.js applications where parsing JSON request bodies silently fails when the body is empty or contains invalid JSON.  Instead of returning an error, the application continues as if a valid JSON object was received, often leading to difficult-to-debug issues.

## The Problem

When an empty request body or an invalid JSON payload is sent to an Express.js route that uses `express.json()`, the middleware doesn't throw an error and instead logs an empty object `{}`. The application continues its execution, potentially leading to unexpected behavior and data corruption.

## How to Reproduce

1. Clone this repository.
2. Run `npm install`.
3. Run `node bug.js`.
4. Send a POST request to `http://localhost:3000/data` with an empty body or with an invalid JSON payload (e.g., an unclosed bracket).
5. Observe that the server logs `{}` and responds with `'Data received'` even with invalid input.

## Solution

The solution involves implementing error handling to catch parsing errors explicitly and returning appropriate error responses.
