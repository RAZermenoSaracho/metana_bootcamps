# Refs in React

**What is a Ref?**

A ref in React is like a variable that helps you refer to a value that isn’t directly related to how things are displayed on the screen. Unlike state or props, which handle component data and communication, refs are more about interacting with the webpage itself.

**Why Do We Need Refs?**

Refs come in handy when you want to hold onto a value but don’t want it to cause the component to re-render when it changes. This is especially useful when dealing with values that might change a lot or when you’re doing things directly with the webpage, like updating a video player or accessing a DOM element.

**Examples of Using Refs**

For instance, let’s say you have a button that keeps track of how many times it’s been clicked. Instead of storing this count in a way that would make your component re-render every time the count changes, you can use a ref. This keeps track of the count without forcing unnecessary updates to your component.

code

```
import React, { useRef, useState } from 'react';

function ButtonWithRef() {
  const countRef = useRef(0); // Initialize ref with initial count value
  const [displayCount, setDisplayCount] = useState(0);

  const handleClick = () => {
    countRef.current++; // Update count without triggering re-renders
    setDisplayCount(countRef.current); // Update state to display count
  };

  return (
    <div>
      <button onClick={handleClick}>Increment Count</button>
      <p>Count: {displayCount}</p>
    </div>
  );
}
```

[YouTube video player](https://www.youtube.com/watch?v=FXa9mMTKOu8)

## Additional Reading Material:

[React Refs - Tpoint Tech](https://www.tpointtech.com/react-refs)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=FXa9mMTKOu8)
