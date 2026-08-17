# Assignment M4

In this assignment, you will create a simple backend server that serves static files and integrates with a weather API to provide real-time weather information. This task will help you understand how to set up a server, serve static content like HTML and CSS, and interact with external APIs to retrieve and display dynamic data.

**Note:** In this module you will continue using localStorage for all task related data. The Node.js server you create here is only for serving your frontend and integrating the Weather API. Database integration will be introduced in a later module.

---

## Reference

You may use the demo application below as a reference for expected behavior and UI flow.

- **Demo App**: [Click here](https://mood-weather-todo.vercel.app/)

---

## Assignment Objectives

The main objective of this assignment is to:

- Set up a basic backend server using Node.js and Express.
- Serve static files such as HTML, CSS, and JavaScript.
- Integrate a weather API to fetch weather data based on a user’s request.

---

## Requirements

### Task Functionalities

**Completed Tasks Section**

![](https://resources.metana.co/public/ed/22/ed224d6d8bc51e77166e041144f585606b660335cb7fab4ca2819d2ec0278dbf.png)

- Implement a separate section to display all completed tasks.
- When a user clicks the checkmark next to a task, the task’s status should change back to “backlog.”
- In the task list on the homepage, only display tasks that are in the “backlog” status. Once a user marks a task as complete, it should disappear from the list and appear in the “Completed” section.

![](https://resources.metana.co/public/a4/fe/a4fef3c47db5d6ff2a3c3b05d9c42601b6e11efd417ee9f3056056991cf63849.png)

- Add a button that toggles the visibility of the “Completed” section. The section should only be visible when this button is clicked. If the button is clicked again, the section should be hidden.
- Refer to the provided demo to gain a clear understanding of the entire process.

**API Intergration**

Weather API Section

![](https://resources.metana.co/public/06/8d/068d0f7f87c472325ac4b30c13d5508bb44d62b2d1cf01594a4e162a94bbbbbd.png)

- Implement a separate section to display weather details.
  - The weather button in the header should open a component in the center of the screen that displays the weather information.
- Implement functionality to retrieve the user’s location (latitude and longitude) upon application startup.
- Use the following API to fetch weather data and display it in the application: [Weather API](https://www.weatherapi.com/docs/)
- Visit the website mentioned above, login to the platform, and generate your API Key. Refer to the Weather API documentation provided on their site to understand its usage, and use it to retrieve weather details effectively.
- Display the weather details fetched from the API in the weather section.

**Suggested Tasks Component**

![](https://resources.metana.co/public/f7/70/f770812e61c806992d24186c365ef6a9bc16b67fa51dfa2d58ba61d7804ee471.png)

- Implement the Suggested Tasks component to suggest tasks based on the current weather conditions and the mode selected (e.g., sunny, rainy, etc.).

**Server Files from the Backend**

1. Node.js Backend Setup
   - Initialize a new Node.js project using the command `npm init -y`.
   - Install necessary dependencies, such as Express, by running `npm i express`.
   - Set Up Express Server:
     - Create a basic Express server that listens on a specific port (e.g., port 3000).
     - Use Express’s `static` middleware to serve static files such as HTML, CSS, and JavaScript from a public directory.

**Convert to Handlebars Templates**

1. Rebuild Application with Handlebars Templates
   - Convert the entire application to use Handlebars for templating.
   - Ensure that reusable components are implemented separately and utilized properly across the application.
   - Render Handlebars files when routes are requested to dynamically generate the views.

### Responsive Design Requirements

- Use **CSS Flexbox** or **CSS Grid** to build layouts that are adaptable to screen sizes.
- Ensure:
  - All Pages are fully responsive.
  - Components adjust gracefully for desktop, tablet, and mobile views.
  - Text and interactive elements are easily readable and clickable on smaller devices.

## Deliverables

- A fully functional web application with all components integrated and working

## Submission Instructions

1. Push your completed work to your Metana-fullstack-bootcamp GitHub repository in a folder named `mood-based-todo-app`.
2. Make sure all files are included.
3. Update your README.md file with the new updates.

## Tips for Success

- Optimize Your JavaScript Code for Better Performance.

Good luck with this week’s assignment! If you have any questions, feel free to reach out to your instructor. Happy coding!
