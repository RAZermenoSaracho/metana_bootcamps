# JSON Web Tokens (JWT) - Continued

- JWTs are one method of securely storing data, commonly used in web applications but adaptable for various use cases.
- They consist of three parts: header, payload, and signature, providing a structured way to store information.
- While JWTs offer encryption and signing, they are not the sole method for securing data.
- You can find the `jsonwebtoken` package on npm for working with JWTs → [https://www.npmjs.com/package/jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken*)

### Securing Data with JWTs

- JWTs ensure data security through encryption and signing using a secret key, usually managed by the server.
- Encryption prevents unauthorized access to data, as only those with the key can decrypt the message.
- Signatures, which incorporate the header and content, help prevent tampering; if the data is altered, the signature becomes invalid.

### Example Implementation

code

```
const jwt = require('jsonwebtoken');

// Create a token
const token = jwt.sign({ userId: 1 }, 'secret_key', { expiresIn: '1h' });

// Verify a token
jwt.verify(token, 'secret_key', (err, decodedToken) => {
  if (err) {
    console.error('Token verification failed');
  } else {
    console.log('Decoded token:', decodedToken);
  }
});
```

- For an in-depth understanding of JWT implementation in Node.js, consider watching this tutorial → <https://www.youtube.com/watch?v=6ZCU4QetVTs>
