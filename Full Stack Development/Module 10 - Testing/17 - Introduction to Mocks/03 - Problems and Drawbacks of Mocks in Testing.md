# Problems and Drawbacks of Mocks in Testing

Mocking, while beneficial for unit testing, introduces certain challenges and limitations that developers need to be aware of:

- **Complexity**: Building useful mocks is complex and time-consuming. This can make refactoring your application much harder.
- **Inaccuracy**: A mock may not 100% accurately represent the behavior of the thing it is mocking, resulting in expectations during testing that don’t match the real behavior.
- **Repetition:** Writing mocks may result in re-writing behaviors of existing code, which violates the DRY principle.
