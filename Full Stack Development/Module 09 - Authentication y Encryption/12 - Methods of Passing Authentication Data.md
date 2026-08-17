# Methods of Passing Authentication Data

When we have authentication data, such as a JWT auth token, in our frontend from login, we need a way to pass it to the backend server or REST API to authenticate requests. There are different methods for passing this data.

### Passing as JSON Data in the Request Body

- When logging in using a login form, the username and password data are typically sent as JSON in the request body.
- However, we don’t want to do this with every request because it would require the backend to check the user each time, increasing the chance of interception.
- Normally, we authenticate once and create a token or cookie to pass in future requests.

### Headers

- When interacting with REST APIs, we usually pass data using headers.
- Headers are outside the body of the request and use ‘key:value’ pairs. Any additional information needed by the server to process a request can be included in the headers.
- Auth tokens are typically put in headers with a key name like `x-auth-token`, but it can be named according to preference.
- Headers are passed with the request object to the backend handlers.

### Cookies

- Cookies provide a more permanent way to store data, such as auth tokens, or the username or email of the current user.
- Cookies are set on the client-side (the application running in the user’s browser) and are sent with every request.
- This data is available to the frontend application and can also be shared with the backend server.
- Middleware such as `cookieparser` can be used to add the `cookies` attribute to the request object, making it accessible as `req.cookies`.
