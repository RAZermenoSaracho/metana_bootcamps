# Testing React Components

Testing React components is crucial for ensuring that your application behaves as expected, especially when components contain complex logic or interact with state management systems like Redux. Proper testing can help catch errors early in the development process and improve the overall quality of the application.

## Why Test React Components ?

- **Unit Testing**: Each React component can be treated as a function that returns HTML based on the given props. This makes it straightforward to test components in isolation.
- **Integration Complexity**: Components that depend heavily on external systems or child components can introduce complexities. These cases may require more integrated or end-to-end testing approaches.

## Approaches to Testing React Components

1. **Shallow Rendering**: This technique involves rendering a component without rendering its children. It's useful for unit testing individual components without getting entangled in the behaviors of child components.
2. **Full Rendering**: Useful for testing components that interact with APIs, requiring full lifecycle API availability.

## Libraries for Testing React

- **React Testing Library**: (<https://github.com/testing-library/react-testing-library>)
  - Encourages better testing practices by focusing on testing the component as it's used rather than its implementation details.
- **Enzyme**: (<https://enzymejs.github.io/enzyme/>)
  - Provides more granular control over component rendering and state, allowing for both shallow and full rendering.
- **React Test Renderer**: (<https://jest-bot.github.io/jest/docs/snapshot-testing.html>)
  - Used mainly for snapshot testing, capturing the rendered output of a component and comparing it to a reference snapshot over time.

## Examples of Testing React Components

### Using React Testing Library with Jest

*For documentation on integrating Jest with React Testing Library: <https://jestjs.io/docs/tutorial-react>*

### Testing a Simple React Component with `testing-library/react`

*From [https://blog.bitsrc.io/testing-your-react-components-step-by-step-2ce9c3b4f299](https://blog.bitsrc.io/testing-your-react-components-step-by-step-2ce9c3b4f299*)*

**Component (greeter.js):**

code

```
export default function Greeter({ name }) {
    if (name) {
        return (<p>Hi there {name}</p>);
    } else {
        return (<p>Hello stranger, nice to meet you!</p>);
    }
}
```

**Tests (greeter.test.js):**

code

```
import { render, screen } from '@testing-library/react';
import Greeter from './Greeter';

test('renders the greeter correctly without a name', () => {
  render(<Greeter />);
  const pElement = screen.getByText(/stranger/i);
  expect(pElement).toBeInTheDocument();
});

test('renders the greeter correctly with a name', () => {
  render(<Greeter name="Fernando" />);
  const pElement = screen.getByText(/Hi there Fernando/i);
  expect(pElement).toBeInTheDocument();
});
```

### React Testing with Enzyme

*See: <https://www.smashingmagazine.com/2020/06/practical-guide-testing-react-applications-jest/>*

### Tutorial

*Required viewing*

[YouTube video player](https://www.youtube.com/watch?v=JBSUgDxICg8)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=JBSUgDxICg8)
