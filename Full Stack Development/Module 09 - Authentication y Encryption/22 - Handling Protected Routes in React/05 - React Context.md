# React Context

### **What is React Context?**

- React Context is a way of passing data down to our components without using props directly. It helps avoid the complication of prop drilling.
- With React Context, we can provide data at the top of the component tree and access it in any nested component without having to pass it through every level of the component hierarchy.

### **How to implement React Context**

\*from: [https://www.freecodecamp.org/news/react-context-for-beginners/\*](https://www.freecodecamp.org/news/react-context-for-beginners/*)

1. **Create Context:** Use the `createContext` method to create a new context.
2. **Wrap Provider:** Wrap your component tree with the context provider. This makes the context available to all child components.
3. **Provide Value:** Set the desired value using the `value` prop on the provider component.
4. **Consume Value:** Access the provided value in any component using the context consumer.

**Example**

code

```
import React from 'react';

// Create context
export const UserContext = React.createContext();

function App() {
  return (
    // Provide context value at the top of the component tree
    <UserContext.Provider value="Reed">
      <User />
    </UserContext.Provider>
  )
}

function User() {
  // Consume context value in any component
  const value = React.useContext(UserContext);

  return <h1>{value}</h1>;
}

export default App;
```

**Documentation:** <https://react.dev/reference/react/useContext>

[YouTube video player](https://www.youtube.com/watch?v=j3j8St50fNY)

[YouTube video player](https://www.youtube.com/watch?v=lTjQjWemKgE)

[YouTube video player](https://www.youtube.com/watch?v=A9WlkhdLnn0)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=j3j8St50fNY)
- [YouTube video player](https://www.youtube.com/watch?v=lTjQjWemKgE)
- [YouTube video player](https://www.youtube.com/watch?v=A9WlkhdLnn0)
