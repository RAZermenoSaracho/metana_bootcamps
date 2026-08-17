# Introduction to Testing

## **What is testing in software development ?**

**Testing** ensures your software works correctly before others use it. It’s like double-checking your work to avoid mistakes. Imagine you’re a chef tasting your dish before serving it to guests to ensure it’s perfect. Similarly, in software, you want to verify everything works smoothly.

- **Manual testing**: It’s like having a person explore the software as a regular user would. They click buttons, type in data, and perform tasks to find any issues. It’s like having a human tester carefully inspecting every detail.
- **Automated testing**: It’s like giving the computer a set of instructions to test the software automatically. Instead of a person doing the testing, a program does it quickly and accurately. It’s like having a robot tester speedily checking your software for errors.

## **Is testing the same as debugging ?**

**Debugging** → Imagine you’re a detective searching for clues to solve a mystery. In software development, debugging is like identifying and fixing mistakes or defects in the code, similar to finding and correcting errors in a story.

**Testing** → Think of testing as checking the entire software to ensure it works correctly. It’s like inspecting a completed puzzle to ensure all pieces fit together perfectly.

While debugging is part of testing, testing goes beyond just finding and fixing coding errors. It also involves ensuring the software meets project expectations and is user-friendly.

- Problems in software aren’t always coding errors. They can be other issues like,
  - Performance bottlenecks
  - UX inconsistencies
  - Failure to meet project requirements

## **What are the aims of testing ?**

> Software testing can be stated as the process of verifying and validating whether a software or application is bug-free, meets the technical requirements as guided by its design and development, and meets the user requirements effectively and efficiently by handling all the exceptional and boundary caseshttps://www.geeksforgeeks.org/software-testing-basics/#what-is-software-testing

Unpacking the above statement

- **Bug-free**: ensure there are no technical coding errors
- **Meets technical requirements**: these would be defined by a project technical spec
- **Meets user requirements**: ensuring the software meets the purposes as required by the end-users
- **Handles all exceptional and edge cases**: ensuring that the software behaves correctly in all imaginable edge-case conditions
  - *Error handling*: what behavior should happen in an error
  - *Boundary cases*: testing input values at extreme ends: eg, min/max integer inputs, character limits, maximum of blog posts or user comments
  - *Edge conditions*: high network traffic, excessive CPU load, multiple sign-ons

## **The Pros and Cons of Software Testing**

### **Advantages of testing**

- **Bug identification**: Testing helps find mistakes in the software before users encounter them, ensuring a smoother experience.
- **Improved quality**: Thorough testing improves the overall quality of the software, making it more reliable and stable for users.
- **Cost-effectiveness**: Fixing problems early in the development process saves money in the long run. It’s like repairing a leaky roof before it causes more damage.
- **Enhanced security**: Testing identifies vulnerabilities and weaknesses in the software, making it more secure against potential threats.
- **Customer satisfaction**: High-quality software that undergoes testing provides a better user experience, leading to happier and more loyal customers.

### **Drawbacks of testing**

- **Time-consuming**: Testing takes a lot of time to plan, execute, and analyze, which can slow down the development process. It’s like checking every detail of a car before selling it.
- **Costs ($)**: Testing requires resources like engineers’ time, specialized tools, and infrastructure, which can be expensive. It’s an investment upfront to save money later.
- **False sense of security**: Testing may not catch every problem, leading to a false belief that the software is flawless. It’s like thinking your house is secure but forgetting to lock one door.
- **Complexity**: Writing and managing tests can be complicated, especially for complex software. It’s like solving a puzzle with many pieces, where even small mistakes can cause big problems.

## **Importance of Adding Tests to Your Software**

### **Always Say Yes**

You should write tests for **any** software you produce, regardless of its size.

*This applies to web projects too.*

### **Why ?**

- Writing tests helps practice critical thinking skills.
- It helps you maintain clarity about your software as you build it.
- Tests reassure new users that the software is functioning correctly.
- It builds trust for those who review your code.
- Demonstrates professionalism in your coding practices for potential future employers.

Adding tests to your software ensures its reliability, functionality, and quality, regardless of the project’s scope.

## Additional Reading Material

[Software Testing Tutorial - Tpoint Tech](https://www.tpointtech.com/software-testing-tutorial)
