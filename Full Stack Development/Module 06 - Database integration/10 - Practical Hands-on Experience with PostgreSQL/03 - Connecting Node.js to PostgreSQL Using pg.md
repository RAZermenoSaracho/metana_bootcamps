# Connecting Node.js to PostgreSQL Using pg

In this lesson, you will understand how a Node.js backend connects to a PostgreSQL database using a library called `pg`.

So far, you have interacted with PostgreSQL directly through the terminal. This lesson bridges the gap between that experience and how databases are actually used inside real backend applications.

By the end of this lesson, you should understand **how backend code communicates with a database in real-world projects**, even if you are not yet fully comfortable writing everything from memory.

---

## From SQL in the Terminal to SQL in Your Backend

Up to now, you have been writing SQL queries directly inside the PostgreSQL console. That is excellent for learning the fundamentals.

However, real applications do not rely on developers manually running queries in the terminal. Instead, the backend (Node.js + Express) connects to the database and sends queries automatically when users interact with the app.

Whenever you log in to a website, fetch a list of items, create a task, update your profile, or delete a record, the backend is running SQL queries behind the scenes to make that happen.

The tool that allows Node.js to communicate with PostgreSQL is a library called `pg`.

---

## What is `pg`?

`pg` (also known as node-postgres) is the most commonly used PostgreSQL client for Node.js.

It allows backend applications to connect to a PostgreSQL database, send SQL queries from JavaScript, receive results back into the application, and use database data inside APIs and routes.

This is not a special or niche tool. This is the **industry standard approach** used in real production systems.

---

## Watch This

The video below demonstrates how a real Node.js backend connects to PostgreSQL using `pg` and how queries are executed from inside application code.

As you watch, focus on:

- How the database connection is created
- Where the SQL queries are written
- How data flows from the database back into the application
- How this connects to Express routes

<https://www.youtube.com/watch?v=O4bNwkC1ZxA>

---

In real-world applications, the data flow looks like this:

Frontend → Backend (Node.js) → `pg` → PostgreSQL → Response back to user

This lesson introduces you to how professional backend systems are structured and how your code interacts with real databases.

## Links

- [https://www.youtube.com/watch?v=O4bNwkC1ZxA](https://www.youtube.com/watch?v=O4bNwkC1ZxA)
