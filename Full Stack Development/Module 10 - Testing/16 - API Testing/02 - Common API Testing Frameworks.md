# Common API Testing Frameworks

## Supertest

- Type: API testing framework
- <https://www.npmjs.com/package/supertest>
- Library for testing node.js HTTP servers using a fluent API
- **Features**
  - Simplified API for making HTTP requests.
  - Support for promises.
  - easy-to-use chaining syntax.
- **Best for:** Testing APIs and making HTTP requests in Node.js applications, particularly useful for testing RESTful APIs.

Here's an example code snippet demonstrating the usage of Supertest for API testing,

code

```
const request = require('supertest');
const express = require('express');

const app = express();

app.get('/user', function(req, res) {
  res.status(200).json({ name: 'john' });
});

request(app)
  .get('/user')
  .expect('Content-Type', /json/)
  .expect('Content-Length', '15')
  .expect(200)
  .end(function(err, res) {
    if (err) throw err;
  });
```

*Example complete implementation of tests for an Express API app with Jest and Supertest*

[YouTube video player](https://www.youtube.com/watch?v=FKnzS_icp20)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=FKnzS_icp20)
