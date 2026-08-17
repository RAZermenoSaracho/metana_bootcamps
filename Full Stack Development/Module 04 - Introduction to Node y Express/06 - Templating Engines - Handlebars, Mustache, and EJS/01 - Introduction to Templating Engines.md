# Introduction to Templating Engines

## From HTML & CSS to Templating

So far in this bootcamp, you’ve been building web pages using **HTML** and **CSS**.

HTML gives your page structure — things like headings, paragraphs, buttons, forms, and layout sections. CSS controls how those elements look - spacing, colors, fonts, and layout behavior.

This approach works perfectly well when you are building small projects, when you only have one or two pages, and when your content does not change very often.

But as soon as projects grow, a problem starts to appear.

---

## Imagine this real-world scenario:

Imagine you’ve built a website with multiple pages. Every page includes the same navigation bar at the top. One day, your client asks you to change just one link in that navigation.

If you are only using plain HTML, you would need to open every page, find the navigation code, update it manually in each file, and hope you didn’t miss one by mistake. This is slow, error-prone, and difficult to maintain.

This is exactly the kind of problem **templating engines are designed to solve**.

With a templating engine, you can define shared parts of your website (like navigation, footers, and layouts) once and reuse them across all pages. When you change something in one place, it automatically updates everywhere. This makes your projects easier to manage, easier to scale, and easier to maintain over time.

---

## What is a Templating Engine?

A templating engine allows developers to create HTML templates with placeholders for dynamic data. Templates are combined with data to produce HTML that can be displayed in a web browser.

In simple terms: instead of hard-coding text into HTML, you write placeholders (like `{{username}}`) and the system fills them in with real data.

<https://www.youtube.com/watch?v=5uQWAxsV4_g>

---

## Why Use Templating Engines?

Templating engines are used in real-world applications because they solve practical problems.

- **Separation of Concerns:** Keeps the logic separate from the presentation. (HTML handles layout, JavaScript handles logic)
- **Reusability:** Templates can be reused across different parts of an application. (You don’t need to copy the same header into multiple files)
- **Maintainability:** Easier to maintain and update the HTML structure without touching the logic. (One change updates many pages)

This is why almost every professional web application uses some form of templating.

---

## Client-Side vs Server-Side Templates

There are two common ways templates are rendered.

- **Client-Side Templates:** Rendered in the browser using JavaScript.
  - Examples include Handlebars.js and Mustache.js when used in frontend code.
- **Server-Side Templates:** Rendered on the server and sent to the client as HTML.
  - Examples include EJS and Pug.

In this module, you will learn how to use **Handlebars templates** **server-side with Express**, while also understanding its potential client-side applications.

## Links

- [https://www.youtube.com/watch?v=5uQWAxsV4_g](https://www.youtube.com/watch?v=5uQWAxsV4_g)
