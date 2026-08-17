# Mocks Vs. Stubs

There are two terms for simulated dependencies for testing: **mocks** and **stubs.** A **mock** is a more comprehensive replacement for the external dependency, whereas a **stub** is simpler and easier to set up, but less intelligent.

### Mocks

- Mocks are pre-programmed expectations about calls that are expected to be made during testing.
- They verify specific methods are called with particular arguments and are primarily used to test interactions between objects or components.
- Mocks are suitable for testing complex systems where interactions between components need to be closely monitored and verified.

### Stubs

- Stubs provide canned responses to calls made during testing and do not verify interactions.
- They replace actual functionality and are used to simulate the behavior of components or dependencies, offering simpler and more straightforward setup.
- Stubs are ideal for testing simpler software where the focus is on replacing external dependencies with simulated responses.

### Differences

- Mocks are more comprehensive and involve setting up pre-programmed expectations about method calls, making them suitable for testing complex interactions. Stubs, on the other hand, offer simpler functionality and are easier to set up.
- Mocks verify specific method calls and arguments, ensuring precise interactions between objects or components. Stubs do not verify interactions and provide canned responses without validating specific method calls.
- While stubs are adequate for testing simpler software, mocks are preferred for more complex systems where detailed interaction testing is necessary.

[YouTube video player](https://www.youtube.com/watch?v=ofx4Xh29JA0)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=ofx4Xh29JA0)
