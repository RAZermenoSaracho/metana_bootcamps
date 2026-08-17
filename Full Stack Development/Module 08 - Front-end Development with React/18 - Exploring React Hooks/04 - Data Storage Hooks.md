# Data Storage Hooks

In addition to state management, React provides several hooks that facilitate data storage and manipulation within functional components. These hooks offer efficient ways to manage variables, cache values, and optimize performance. Two commonly used data storage hooks are `useRef` and `useMemo`.

### useRef

- useRef allows referencing a variable we don’t want to keep in state
- Think of useRef like a storage box for values that don't need to trigger re-renders.
- You can use it for things like accessing and changing DOM elements directly, and the value you store in useRef won't make your component re-render.
- You access and change the stored value using .current property, and you can get the updated value immediately without waiting for a re-render.
- It's handy for interacting with HTML elements directly, like focusing input fields or measuring their dimensions.
- useRef is also useful for third-party libraries that expose refs along with functions.

[YouTube video player](https://www.youtube.com/watch?v=42BkpGe8oxg)

### useMemo

- useMemo allows storing complex operations so we don’t need to do them again and again
- useMemo helps to optimize performance by remembering the result of a complex calculation.
- You provide a function that calculates the value, and useMemo will only recalculate it if the inputs change.
- For instance, if you have a component that computes a value based on some props or state, useMemo ensures it only recalculates when those inputs change, preventing unnecessary work.
- Always remember to include all relevant dependencies in the dependency array, and be cautious not to overuse useMemo, as it can affect performance negatively.

[YouTube video player](https://www.youtube.com/watch?v=vpE9I_eqHdM)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=42BkpGe8oxg)
- [YouTube video player](https://www.youtube.com/watch?v=vpE9I_eqHdM)
