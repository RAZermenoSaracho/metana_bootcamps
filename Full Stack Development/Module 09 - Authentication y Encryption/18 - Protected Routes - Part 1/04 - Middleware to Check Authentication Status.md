# Middleware to Check Authentication Status

Middleware functions are functions that have access to the request and response objects in an Express.js application's request-response cycle. Middleware can be used to perform tasks like logging, authentication, or modifying the request or response objects.

**Example:** In an Express.js application, a middleware function can be created to check whether a JWT exists in the request headers and if it is valid. If the JWT is valid, the middleware allows the request to proceed; otherwise, it returns an error response indicating unauthorized access.

Middleware is like a helpful guide at a museum:

- **Extracting the Token:**
  - Middleware intercepts incoming requests (like guiding visitors through the museum).
  - It grabs the JWT from the request headers (like checking tickets).
- **Verifying the Token:**
  - The guide (middleware) validates the JWT.
  - If it’s genuine, the visitor (user) continues the tour; otherwise, access is denied.

[YouTube video player](https://www.youtube.com/watch?v=zYi9PguVFx8)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=zYi9PguVFx8)
