# Promises in async functions

Imagine you have a list of tasks to do, and some tasks take longer than others. You want to make sure you can keep doing other things while waiting for the long tasks to finish. Promises and async functions help you do just that!

### How are they used in async functions?

![](https://resources.metana.co/public/f2/79/f279a0ffa5dc861aa5ef0f32cbc7f97e85500a47431926a6446583ace950328c.png)

**Tasks with Different Speeds:** Sometimes, in programming, we have tasks that can be slow, like fetching data from the internet, and tasks that are quick, like adding numbers. We want to keep our program responsive, so it doesn't freeze while waiting for the slow tasks.

**Async Functions:** That's where async functions come in. An async function is like a special kind of function in JavaScript that can do slow tasks without blocking everything else. It says, "Hey, this task might take some time, but don't worry, I won't stop everything."

**Promises in Async Functions:** Inside an async function, we often use promises to manage these slow tasks. A promise is like a little helper that says, "I'll let you know when the slow task is done, so you can continue doing other things in the meantime."

**The `await` Keyword:** When you have a promise inside an async function, you can use the `await` keyword to say, "Wait for this promise to finish, and then give me the result." While waiting, your program can do other tasks.

**We recommend you to do these tutorials available at W3schools :** [Click Here](https://www.w3schools.com/js/js_promise.asp)

### Let's look at how to use Promises

[YouTube video player](https://www.youtube.com/watch?v=DHvZLI7Db8E)

### Learning Outcomes

- Understanding what is Promises

## Additional Learning Material

[YouTube video player](https://www.youtube.com/watch?v=TnhCX0KkPqs)

[Promise - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=DHvZLI7Db8E)
- [YouTube video player](https://www.youtube.com/watch?v=TnhCX0KkPqs)
