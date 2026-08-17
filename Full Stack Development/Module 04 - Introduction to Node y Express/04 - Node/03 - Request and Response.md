# Request and Response

[YouTube video player](https://www.youtube.com/watch?v=DQD00NAUPNk)

In this unit you will be learning about :

- **Status Codes**:
  - Used to describe the type and success of the response.
  - Common ones: 200 (OK), 301 (Moved Permanently), 404 (Not Found), 500 (Internal Server Error).
  - Categorized into informational, success, redirects, client errors, and server errors.
- **Setting Status Code in Node.js**:
  - Use `response.statusCode` property to set the status code.
  - Examples: `response.statusCode = 200;`, `response.statusCode = 301;`.
- **Switch Statement for Routing**:
  - Create a switch statement to handle different URL routes.
  - Determine the URL using `request.url`.
  - Different cases for various routes (e.g., `/`, `/about`, `/about-me`).
  - Use `response.statusCode` to set appropriate status codes for each case.
- **Redirecting in Node.js**:
  - Redirect users by setting the status code to 301 (Moved Permanently).
  - Use `response.setHeader('Location', '/new-url');` to specify the new URL.
  - End the response to initiate the redirect: `response.end();`.
- **File System Module (fs) Usage**:
  - Use the `fs` module to read files.
  - Employ `fs.readFile()` with a callback for handling file read completion or errors.
- **Content Type Header**:
  - Set the `Content-Type` header to specify the type of content being sent.
  - Examples: `response.setHeader('Content-Type', 'text/html');`, `response.setHeader('Content-Type', 'text/plain');`.
- **Node.js HTTP Server Basics**:
  - Create a basic HTTP server using Node.js.
  - Manually handle server creation with the `http` module.
  - Listen for requests on a specified port (e.g., port 3000) and respond accordingly.
- **Routing and Sending HTML Pages**:
  - Establish a simple routing system based on URL routes.
  - Read HTML content from files based on routes using the `fs` module.
  - Send different HTML pages as responses based on the route.
- **Understanding HTTP Status Codes**:
  - Status codes categorize responses into ranges like informational, success, redirects, client errors, and server errors.
  - Each code carries a specific meaning, aiding communication between servers and clients.

Understand HTTP Status Codes by referring to this [page](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=DQD00NAUPNk)
