# What is Recursion

Imagine you have a big puzzle to solve. Instead of solving the whole puzzle at once, you break it into smaller pieces. If any of those smaller pieces still need breaking down, you repeat the process until the pieces are so small and simple that you can easily solve them.

In JavaScript, recursion works in a similar way. You have a function that keeps calling itself with a smaller version of the problem until it reaches a point where it can directly solve the smallest version.

### How Recursion is really used

![](https://resources.metana.co/public/1a/aa/1aaac412d51a8138569a4ce101bb7da7ac8132296fa443bb56c3ba732c567aa2.png)

Let's assume that you have a pile of books, and you need to place each one onto a shelf. You can only place one book at a time. For this you can use a recursive function to take a book from the pile and place it on the shelf, then repeat the process with the remaining books.

![](https://resources.metana.co/public/79/98/799827dc476b70798e7bcc50772415a1ca7005cf3c51715c9424a724fc7d79b6.png)

### How does recursion comes to help ?

So let's take look at how recursion helps in solving the above task

![](https://resources.metana.co/public/0c/ff/0cffc07f9220eda272389591d2099d4fb49d992dd24b9819a6c063dd73712f88.png)

**Explained:**

1. **Base case:** If there are no more books in the pile, we're done! The function just says, "All books are on the shelf!"
2. **Take a book:** The function takes a book from the pile, says which book it is, and puts it on the shelf.
3. **Call itself:** Now, the function decides to use itself again to place the remaining books on the shelf.
4. **Repeat the process:** The function keeps doing this – taking a book, placing it on the shelf, and calling itself for the remaining books – until there are no more books in the pile.

So, recursion is like having a magical book organizer that can handle placing one book at a time and uses a smaller version of itself to deal with the rest of the books. It simplifies the task by breaking it down into smaller, manageable steps.

### Let's watch this video to get a better understanding on recursion

[YouTube video player](https://www.youtube.com/watch?v=wd2vNXCfu9s)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=wd2vNXCfu9s)
