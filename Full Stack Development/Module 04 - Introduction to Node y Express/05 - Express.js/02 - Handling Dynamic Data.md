# Handling Dynamic Data

Handling data in a web application often involves dynamically generating HTML content based on the data received from the server or other sources. In the context of Node.js and Express, view engines play a crucial role in managing this dynamic content generation. Let's delve into the concept of view engines and how they facilitate the rendering of dynamic content in web applications.

1. **Dynamic Content:**
   - Web applications often need to display dynamic data to users, such as user profiles, product details, or real-time updates.
   - Express allows developers to pass data to views (templates) that can be dynamically rendered based on the provided information.
2. **Templating Engines:**
   - Templating engines are tools that help embed dynamic data into static HTML templates.
   - Express supports various templating engines, such as EJS, Pug (formerly Jade), Handlebars, and others.

## View Engines

A view engine is middleware that integrates with web frameworks, such as Express in Node.js, to facilitate dynamic content rendering on the server side.

View engines enable the dynamic generation of HTML content by embedding data into predefined templates.

- **Templates:** Predefined structures containing static HTML and placeholders for dynamic data.
- **Data Injection:** The process of inserting dynamic content into templates before rendering

### **Common View Engines**

- **Integration with Express:**
  - Install the desired view engine using npm (e.g., `npm install ejs`).
  - Configure Express to use the view engine:
- **EJS (Embedded JavaScript):**
  - Embeds JavaScript code directly into HTML templates.
  - Uses `<% %>` tags for code execution and `<%= %>` for data output.
- **Pug (formerly Jade):**
  - Relies on indentation instead of HTML tags for structure.
  - Uses concise syntax for template definition.
- **Handlebars:**
  - Employs `{{ }}` for dynamic content and allows for creating reusable components (partials).

[YouTube video player](https://www.youtube.com/watch?v=yXEesONd_54)

### In this lesson you will be learning

- To inject dynamic data into templates in Express, you can use view engines or template engines.
- Use express supports various template engines, including EJS (Embedded JavaScript), which allows you to write HTML templates with dynamic data and logic.
- To use EJS, you need to install it using npm (`npm install ejs`) and set it as the view engine in your Express application using `app.set`.
- By default, Express looks for EJS templates in a "views" folder, but you can specify a different folder using `app.set('views', 'your-folder-name')`.
- EJS templates use tags `<% %>` to enclose JavaScript code and `<%= %>` to output dynamic data.
- Dynamic data can be passed to templates by providing an object as the second parameter to the `render` method in Express.
- You can use conditions (if statements) in EJS templates to control the rendering of certain elements based on dynamic data.
- In the example, a `blocks` array is passed to the "index" template, and the template checks if there are any blocks before rendering them.
- EJS templates provide a convenient way to generate dynamic HTML content based on server-side data, making it easy to build dynamic web applications.

## Links

- [YouTube video player](https://www.youtube.com/watch?v=yXEesONd_54)
