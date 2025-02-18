# Intermittent JSON Parsing Failure in Express.js under Load

This repository demonstrates a bug where an Express.js application intermittently fails to parse JSON request bodies, resulting in `req.body` being undefined. This issue is particularly noticeable under heavy load.

## Bug Description

The provided `bug.js` file contains a simple Express.js application that expects a JSON payload. Under normal conditions, it works correctly. However, when subjected to a significant number of concurrent requests, the application sporadically fails to parse the JSON, leaving `req.body` empty.

## Solution

The `bugSolution.js` file shows a corrected version that addresses the issue by explicitly setting the `json` limit using `express.json({ limit: '50mb' })`. This prevents issues caused by excessively large request bodies which may not have been handled previously.

## How to Reproduce

1. Clone this repository.
2. Navigate to the directory.
3. Run `npm install express` to install dependencies. 
4. Run `node bug.js` to start the server.
5. Use a load testing tool (like k6 or Artillery) to send many concurrent requests to the `/user` endpoint with JSON payloads. Observe intermittent failures when using the `bug.js` file.   The `bugSolution.js` file should consistently handle large requests.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request if you encounter any problems or have suggestions for improvement.