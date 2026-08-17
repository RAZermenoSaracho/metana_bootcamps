# JSON Web Tokens

JSON Web Tokens (JWT) are a popular method for securely transmitting information between parties. *In our application, we’ll utilize JWT for authentication purposes.*

- **NPM Library: `jsonwebtoken`**
  - This library is a go-to choice for handling authentication in Node.js.
  - It’s widely trusted and commonly used by developers for secure authentication.
- **Package Homepage**
  - You can find more information and detailed documentation on the official npm package page → <https://www.npmjs.com/package/jsonwebtoken>
  - It’s highly recommended to read the docs to understand how to use it effectively.

Stay tuned for further sections where we’ll delve deeper into the functionalities and implementation of JWT in our application.

[YouTube video player](https://www.youtube.com/watch?v=p_sDlCyzUFU)

Understand how JSON Web Tokens (JWT) work and how to use them for token-based authentication to protect API routes.

---

### **What is JWT?**

JWT is a compact, URL-safe token used to represent claims between two parties. It's often used to authenticate users without the need for maintaining sessions on the server.

- **Header:** The header contains the token's type (JWT) and the signing algorithm used (e.g., HMAC SHA256).
- **Payload:** The payload contains the claims (information) like the user's ID or role.
- **Signature:** The signature verifies the token's integrity and authenticity. It's created by encoding the header and payload, then signing it using a secret key.

When a user logs in, the server creates a JWT containing the user’s information (like ID, username, and role). This token is sent back to the client.

---

### **How JWT Works in Authentication**

1. **User Login:**
   - The user sends their credentials (username/password) to the server.
   - If valid, the server generates a JWT and sends it back to the user.
2. **Storing the Token:**
   - The client stores this token in either cookies (HTTP-only) or in local storage.
   - Whenever the user makes subsequent requests to protected resources, the token is included in the request header (usually as a Bearer token).
3. **Server Validation:**
   - The server checks the token's validity using the signature. If the token is valid, the server grants access to the protected resource.
   - If the token is missing or invalid, access is denied.
4. **Expiration:** JWT tokens are usually set with an expiration time. After the token expires, the user needs to log in again to get a new one.

---

### **Securing Routes Using JWT**

When a user tries to access a protected route or API endpoint, the following happens:

1. The client sends the JWT in the HTTP request's headers.
2. The server extracts the token from the header and verifies its signature.
3. If valid, the server grants access to the resource. The server might also check additional claims, like user roles, to further authorize the request.
4. If invalid or expired, the server rejects the request with an appropriate error.

JWT is especially popular in stateless, distributed applications because the server does not need to store session data.

## Links

- [YouTube video player](https://www.youtube.com/watch?v=p_sDlCyzUFU)
