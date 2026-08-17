# Passport.js

[Passport.js](http://www.passportjs.org/) is a widely-used authentication library for Node.js, coming in as the second most popular choice. It's known for its flexibility and support for various authentication strategies, making it a solid option if you need more than just JSON Web Tokens (JWT).

- **Supports Various Strategies:** Passport.js supports different authentication strategies, such as local (username and password), OAuth, and OpenID.
- **Flexibility:** It offers flexibility in integrating with different authentication methods, allowing developers to choose the most suitable approach for their application.

### Example Usage

code

```
const passport = require('passport');
const LocalStrategy = require('passport-local').Strategy;

passport.use(
  new LocalStrategy((username, password, done) => {
    // Verify user credentials here
    if (username === 'user' && password === 'password') {
      return done(null, { id: 1, username: 'user' });
    } else {
      return done(null, false, { message: 'Invalid credentials' });
    }
  })
);
```

In this example, we're setting up Passport.js for local authentication. We define a new LocalStrategy and provide a callback function to verify the user's credentials. If the credentials are valid, we call `done(null, user)` to indicate success, otherwise `done(null, false)` to indicate failure.
