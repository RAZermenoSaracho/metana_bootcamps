# Node.js Architecture

[YouTube video player](https://www.youtube.com/watch?v=XUSHH0E-7zk)

### What is Event-Driven Architecture ?

Imagine you're at a big party with lots of guests. Instead of having one person serve drinks to everyone (which would take a long time and create a long line), there's a bell on the table. Whenever someone wants a refill, they ring the bell, and the host quickly serves them a drink, then moves on to the next task. This is similar to how Node.js works.

In Node.js, events (like clicking a button on a website) are like the bell. When an event happens, Node.js notices (the bell rings) and runs a specific piece of code in response (serves the drink). This allows Node.js to handle lots of different tasks or events at the same time without waiting for one to finish before starting another, making it very efficient.

### What is Non-Blocking I/O ?

I/O stands for input/output, which includes operations like reading files from a disk or sending data over the internet. Non-blocking means that these operations don't stop Node.js from doing other things while they're happening.

In Node.js, when a file needs to be read or data needs to be fetched from a database, Node.js starts the operation and then moves on to handle other tasks. It doesn't wait for the file to be fully read or the data to be completely fetched. Once the file is read or the data is available, Node.js will handle the result, such as sending the data to the client. This makes Node.js very fast and efficient, especially for applications that handle lots of operations at the same time.

[YouTube video player](https://www.youtube.com/watch?v=pUQCewTC-sQ)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=XUSHH0E-7zk)
- [YouTube video player](https://www.youtube.com/watch?v=pUQCewTC-sQ)
