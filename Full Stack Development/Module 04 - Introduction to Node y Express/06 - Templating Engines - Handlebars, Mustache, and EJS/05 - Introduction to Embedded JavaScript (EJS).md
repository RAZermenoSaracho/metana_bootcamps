# Introduction to Embedded JavaScript (EJS)

## Introduction to EJS

In this lesson, you will understand what **EJS** is and where it is used when building web applications with Node.js and Express.

---

## What is EJS?

EJS (Embedded JavaScript) is a templating engine that allows you to write HTML and embed JavaScript directly inside the template.

It is often used with Node.js and Express to generate dynamic HTML on the server before sending it to the browser.

<https://www.youtube.com/watch?v=AHtSPnHb7Cs>

---

## How EJS Compares to Handlebars

EJS allows embedding JavaScript inside HTML to generate dynamic content, offering greater flexibility. It’s a widely used standard engine for Node.js applications, making it easy to integrate and use.

- **EJS**: Allows JavaScript directly in the HTML, enabling more flexibility but with slightly more complexity.
- **Handlebars**: Focuses on simple syntax and clear structure with less JavaScript inside HTML.

Both are useful in real-world applications, and you will encounter both in your projects.

---

## Example of EJS Syntax

html

```
<h1>Hello <%= username %></h1>

<ul>
  <% users.forEach(user => { %>
    <li><%= user %></li>
  <% }) %>
</ul>
```

You do **not** need to memorize this. This is only to help you recognize EJS templates.

---

In the next lesson, you’ll complete a short quiz to check your understanding of Handlebars concepts before moving on to the assignment.

## Links

- [https://www.youtube.com/watch?v=AHtSPnHb7Cs](https://www.youtube.com/watch?v=AHtSPnHb7Cs)
