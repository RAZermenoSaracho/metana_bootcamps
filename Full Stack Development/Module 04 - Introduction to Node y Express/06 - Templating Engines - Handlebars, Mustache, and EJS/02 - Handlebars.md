# Handlebars

## Intro to Handlebars

### What are templates?

Templates are pre-designed layouts that allow you to arrange content onto a web page to quickly create a well-designed website.

Think of a template as a reusable page structure where only certain parts change dynamically.

## Handlebars.js

Handlebars.js is a templating engine that allows you to build semantic templates effectively. It extends Mustache templates by adding additional features like helpers and partials, making it more powerful while maintaining simplicity.

This balance of simplicity + power is why Handlebars is the main engine used in this module.

<https://www.youtube.com/watch?v=4HuAnM6b2d8>

---

## How Handlebars Works

### Templates and Layouts

Think of a template as a page skeleton, a structure with placeholders for dynamic content.

Layouts are templates that wrap around your pages (e.g., header, footer). The video shows how Handlebars uses `{{{ body }}}` to insert the page‑specific content into a layout.

### Partials

Partials are reusable pieces of templates, such as navigation or header components, that can be included in multiple templates. Handlebars uses them to help you keep your HTML DRY (Don’t Repeat Yourself).

### Express Integration

Handlebars works with Express by registering it as the view engine. Once registered, Express can render `.hbs` templates and inject data from your routes.

## Links

- [https://www.youtube.com/watch?v=4HuAnM6b2d8](https://www.youtube.com/watch?v=4HuAnM6b2d8)
