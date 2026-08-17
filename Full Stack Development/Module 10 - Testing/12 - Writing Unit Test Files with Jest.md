# Writing Unit Test Files with Jest

Refer this guide → <https://phillcode.io/jest-config>

**Writing a Simple Unit Test**

Below is an example of a simple unit test for a `sum` function

code

```
// Import necessary functions and modules
import { describe, expect, test } from '@jest/globals';
import { sum } from './sum'; // Import the function to be tested

// Describe the test suite
describe('sum module', () => {
  // Write a test case
  test('adds 1 + 2 to equal 3', () => {
    // Perform the test and make assertions
    expect(sum(1, 2)).toBe(3); // Check if the sum function returns the expected result
  });
});
```

In this example:

- We import the necessary testing functions (`describe`, `expect`, `test`) from `@jest/globals`.
- We import the `sum` function from the module we want to test (`./sum`).
- We use `describe` to group our tests and provide a description.
- Inside the `describe` block, we use `test` to define a specific test case.
- Inside the `test` block, we use `expect` to make assertions about the behavior of our `sum` function.
