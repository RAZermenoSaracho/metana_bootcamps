# JSON Web Tokens (JWT)

JSON Web Tokens (JWT) are a popular method for securely transmitting information between parties as a JSON object. JWTs are commonly used for authentication and authorization in web applications. They consist of three parts: a header, a payload, and a signature, which are encoded and concatenated to form a token.

**Example:** After a user successfully logs in, the server generates a JWT containing the user's ID and role. This token is then sent back to the client and stored locally (e.g., in local storage or a cookie). Subsequent requests to protected routes include this JWT in the request headers for authentication. JWTs (JSON Web Tokens) act like backstage passes at a concert.

- **How Does It Work?**
  - After login, the server hands the user a JWT (like getting a backstage pass).
  - The user includes the JWT in every request (like showing the pass at different checkpoints).
  - The server checks the JWT to verify the user’s identity (like checking the pass at the backstage entrance).

[YouTube video player](https://www.youtube.com/watch?v=fYaduF4iUSQ)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=fYaduF4iUSQ)
