# JSX Syntax

JSX, which stands for JavaScript XML, is a special syntax in React that allows developers to write HTML-like code directly within JavaScript. It's called "XML" because it resembles XML or HTML syntax, making it easier for developers to create and visualize user interface components in React applications.

### HTML-Like Syntax Inside JavaScript

JSX looks a lot like HTML, so it's easy for developers who know HTML to work with it. Instead of writing separate HTML and JavaScript code, JSX lets you write them together in a more straightforward way, which makes creating UI components simpler.

### Compiling JSX to JavaScript

Even though JSX looks like HTML, web browsers can't understand it directly. So, JSX code has to be converted into regular JavaScript before it can run in a browser. This conversion process is called transpilation, and it's done using tools like Babel. (What is babel -> <https://babeljs.io/docs/>)

### Benefits of JSX

- **Declarative Syntax**: JSX allows developers to describe UI components more clearly and concisely compared to writing out all the DOM manipulation in JavaScript.
- **Component Reusability**: JSX encourages the use of reusable components, which helps keep code organized and makes it easier to maintain.
- **Integration with JavaScript**: Since JSX is embedded within JavaScript, you can easily include JavaScript expressions and logic directly in your JSX code, making it dynamic and powerful.

### Basic Structure

JSX elements look like HTML tags but are enclosed in curly braces `{}` when used in JavaScript. For example, `<h1>Hello, JSX!</h1>` becomes `const element = <h1>Hello, JSX!</h1>;` in JSX.

### Advantages of JSX

- **Component-Based Approach**: JSX fits well with React's component-based architecture, which makes it easy to create modular and reusable UI components.
- **Conciseness and Readability**: JSX makes code more readable and easier to understand, especially for developers familiar with HTML.
- **Seamless Integration with JavaScript**: You can mix JavaScript expressions and logic directly within JSX, making it flexible and expressive.

### Expressions in JSX

You can embed JavaScript expressions within curly braces `{}` in JSX. This allows you to dynamically insert values into JSX elements. For example, `const name = "John"; const greeting = <h1>Hello, {name}!</h1>;` dynamically inserts the value of `name` into the JSX element.

### Conditional Rendering

While traditional `if` statements are not directly supported in JSX, developers can utilize ternary expressions or logical operators for conditional rendering. For instance:

code

```
const isLoggedIn = true;
const message = isLoggedIn ? <p>Welcome back!</p> : <p>Please log in.</p>;
```

Here, the `isLoggedIn` variable determines which message to display based on its boolean value.

### Iterating Over Lists

To render lists of elements in JSX, developers can leverage the `map` method to iterate over arrays and generate JSX elements dynamically. For example:

code

```
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) => <li key={number}>{number}</li>);
```

In this example, the `map` method iterates over the `numbers` array, generating a list of `<li>` elements with unique keys assigned to each item.

[YouTube video player](https://www.youtube.com/watch?v=D_cUdRtPG-M)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=D_cUdRtPG-M)
