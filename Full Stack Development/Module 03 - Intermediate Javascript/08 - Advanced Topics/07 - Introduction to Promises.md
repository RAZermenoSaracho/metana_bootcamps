# Introduction to Promises

### What are Promises ?

![](https://resources.metana.co/public/f8/38/f83872517fbc56bc61027b4891c9fcbb9fa6ea07d14cadd2f983f1eb8568cec1.png)

Imagine you're waiting for a delivery package. You know it will arrive, but you don't know exactly when. A promise in JavaScript is a lot like that.

**Promise as a Guarantee:** In JavaScript, a promise is like a guarantee that something will happen in the future. It represents an action that might take some time to complete, such as loading a webpage or fetching data from the internet.

**Three Possible Outcomes:** Just like your package can have three outcomes (it arrives successfully, it gets delayed, or something goes wrong), a promise can also have three states:

- **Pending:** This means the action hasn't happened yet, and we're waiting.
- **Fulfilled:** The action was successful, and we get the result we were waiting for.
- **Rejected:** Something went wrong, and we get an error or reason for the problem.

**Actions to Take:** With promises, we can say, "When the action is done (either successfully or with an error), here's what we should do." We can specify actions for both success and failure.
