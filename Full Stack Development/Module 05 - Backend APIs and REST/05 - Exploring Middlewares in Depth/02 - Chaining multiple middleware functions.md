# Chaining multiple middleware functions

Middleware functions are like a relay race – they pass the baton. Here’s how to chain them:

- **Order Matters**:
  - **Middleware runs in the order they’re defined:** Middleware functions execute sequentially in the order they are defined within the middleware stack.
  - **Use `next()` to move to the next middleware:** Calling `next()` within a middleware function passes control to the next middleware in the stack.
  - **Be cautious – some middleware can end the cycle:** Certain middleware functions may end the request-response cycle by sending a response to the client.

[YouTube video player](https://www.youtube.com/watch?v=PVzbsnc-MY4)

- **Example: Logging Middleware**:
  - **Log request details for debugging:** Logging middleware can capture request details like URL, method, and timestamp, aiding in debugging.
  - **Chain logging middleware before other middleware:** Placing logging middleware at the beginning ensures every request is logged before further processing.

[YouTube video player](https://www.youtube.com/watch?v=C80CWsCSqZA)

## Additional Learning Material

[YouTube video player](https://www.youtube.com/watch?v=giB3qGwOFGM)

[ExpressJS - Middleware](https://www.tutorialspoint.com/expressjs/expressjs_middleware.htm)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=PVzbsnc-MY4)
- [YouTube video player](https://www.youtube.com/watch?v=C80CWsCSqZA)
- [YouTube video player](https://www.youtube.com/watch?v=giB3qGwOFGM)
