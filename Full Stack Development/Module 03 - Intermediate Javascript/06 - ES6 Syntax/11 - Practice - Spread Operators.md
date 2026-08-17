# Practice - Spread Operators

### Visit the following links to practice and enhance your understanding of Array Destructuring.

1. W3school [React ES6 Spread Operator](https://www.w3schools.com/react/react_es6_spread.asp)
2. ES6 Tutorials [ES6 Tutorials : SPREAD Operator with Fun](https://www.codingame.com/playgrounds/7998/es6-tutorials-spread-operator-with-fun)

---

### Practice and Enhance Your Understanding of Array Destructuring

Array destructuring and the spread operator are essential tools in modern JavaScript. They help simplify your code and make it more readable.

### What is Array Destructuring?

Array destructuring allows you to unpack values from an array and assign them to variables in one line. For example:

code

```
let [a, b, c] = [1, 2, 3];
console.log(a, b, c);  // Output: 1 2 3
```

You can also skip elements or provide default values:

code

```
let [a, , c = 10] = [1, 2];
console.log(a, c);  // Output: 1 10
```

### What is the Spread Operator?

The spread operator (`...`) allows you to spread the elements of an array or object. It’s useful for copying arrays or merging them. For example:

code

```
let arr1 = [1, 2];
let arr2 = [3, 4];
let mergedArr = [...arr1, ...arr2];
console.log(mergedArr);  // Output: [1, 2, 3, 4]
```

### Practice Resources

1. [\*\*W3Schools - React ES6 Spread Operator](https://www.w3schools.com/react/react_es6_spread.asp) —\*\* This guide explains how to use the spread operator in React applications.
2. [\*\*ES6 Tutorials: Spread Operator with Fun](https://www.codingame.com/playgrounds/7998/es6-tutorials-spread-operator-with-fun) —\*\* An interactive tutorial with practical examples to help you understand destructuring and the spread operator.
