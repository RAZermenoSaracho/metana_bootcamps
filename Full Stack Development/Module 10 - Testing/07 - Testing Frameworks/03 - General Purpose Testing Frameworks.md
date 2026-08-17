# General Purpose Testing Frameworks

## Jest

<https://jestjs.io>

Jest is a JavaScript testing framework with a focus on simplicity. It provides built-in assertions, mocking capabilities, and supports parallel test execution.

- **Strong Points**
  - Fast and parallel test execution.
  - Built-in support for mocking functions and modules.
- **Best for →** Unit testing and integration testing in Node.js applications, particularly projects with React or React Native components.

**Example Code**

code

```
test('adds 1 + 2 to equal 3', () => {
  expect(1 + 2).toBe(3);
});
```

[YouTube video player](https://www.youtube.com/watch?v=qRj5FNrNymc)

## Jasmine

<https://jasmine.github.io>

Jasmine is a behavior-driven development (BDD) testing framework for JavaScript. It offers an easy-to-read syntax, supports BDD-style test writing, and works in both browser and Node.js environments.

- **Strong Points**
  - Easy-to-read syntax suitable for behavior-driven development.
  - Provides a full-featured testing framework with assertion libraries and spies.
- **Best for →** Behavior-driven testing.

**Example Code**

code

```
describe('an order', () => {
  it('sums the prices of its line items', () => {
    const order = { total: 100.00 };
    expect(order.total).not.toBe(0.00);
    expect(order.total).toBe(100.00);
  });
});
```

[YouTube video player](https://www.youtube.com/watch?v=rw4KlxKEENQ)

## Mocha

<https://mochajs.org>

Mocha is a feature-rich JavaScript test framework, particularly popular for testing APIs and server-side code. It offers a flexible test structure, support for various assertion libraries, and asynchronous testing capabilities.

- **Strong Points**
  1. Highly flexible and customizable test structure.
  2. Supports asynchronous testing with promises or callbacks.
- **Best for →** Testing all types of JavaScript applications, from browser-based to Node.js.

**Example Code**

code

```
describe('My function', () => {
  it('should do something', async () => {
    const result = await myFunction();
    assert.equal(result, expectedValue);
  });
});
```

[YouTube video player](https://www.youtube.com/watch?v=NBjYY8P08lI)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=qRj5FNrNymc)
- [YouTube video player](https://www.youtube.com/watch?v=rw4KlxKEENQ)
- [YouTube video player](https://www.youtube.com/watch?v=NBjYY8P08lI)
