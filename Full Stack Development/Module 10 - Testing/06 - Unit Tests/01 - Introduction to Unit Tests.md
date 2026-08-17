# Introduction to Unit Tests

## **What is Unit Testing?**

- Unit testing is a method of testing individual units or components of software in isolation from the rest of the system.
- It focuses on checking whether a function returns the correct expected outputs when given various inputs.
- Typically, unit tests are written for one individual function or component at a time.
- Unit tests use the smallest possible scope for testing, isolating the function being tested from external dependencies such as databases or APIs.

[YouTube video player](https://www.youtube.com/watch?v=SOhM7UP-C0I)

## **Assertions**

- Unit tests, like all other automated tests, use ***assertions***, to test that something *should or should not* be true.
- Assertions can be used to test both positive and negative case scenarios
- Assertion will be tested against an **expected result** — true/false, or a returned output. The expected result often stored in a variable called `expect`

## **How to Write a Unit Test**

- Steps to write a unit test:
  1. Identify a target function to test
  2. Figure out exactly what the function should do, given inputs
  3. Write test cases, with what you **expect** for each scenario
  4. Iterate through your test cases, and check the results match the expected value.
- Rules for writing *good* unit tests
  1. Unit tests should be as simple as possible
  2. Unit tests should return the same result every time, when given the same inputs
  3. Test one thing at a time. Don’t mix in external dependencies
  4. Use descriptive names for test cases.
  5. Should test both positive and negative cases
  6. Test that invalid inputs return error, or are otherwise handled

### **Code Example of Unit Tests**

Example of a unit test for a `helloUser` function in JavaScript

code

```
// greetings.js
function helloUser(name) {
  if (typeof name !== 'string') {
    throw new Error('Name must be a string');
  }
  return `Hello, ${name}!`;
}

module.exports = helloUser;
```

code

```
// greetings.test.js
const helloUser = require('./greetings');

describe('helloUser function', () => {

  // Test positive cases: correct output
  test('should return a greeting message with the provided name', () => {
    const result = helloUser('John');
    expect(result).toBe('Hello, John!');
  });

	// Test negative cases: invalid input results in error
  test('should throw an error if name is not a string', () => {
    expect(() => {
      helloUser(123);
    }).toThrow('Name must be a string');
  });
});
```

Explanation

- The **`helloUser`** function in **`greetings.js`** is the code we want to test. It takes a **`name`** parameter and returns a greeting message.
- The unit test in **`greetings.test.js`** verifies the behavior of the **`helloUser`** function.
- The Jest testing framework is used for writing and running the tests.
- Two test cases are included: one positive case where a greeting message is returned correctly, and one negative case where an error is thrown if the **`name`** parameter is not a string.

## Additional Reading Material

[What is Unit Testing?](https://www.guru99.com/unit-testing-guide.html)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=SOhM7UP-C0I)
