# Assignment M2

This week’s assignment focuses on laying the foundation for your To-Do app by creating its static pages and core components. Your goal is to design and build responsive, visually appealing pages that will later be enhanced with functionality.

---

## **Reference**

You may reference the application below to better understand the layout and structure.

- **Demo App**: [Click here](https://mood-weather-todo.vercel.app/)

---

## **Assignment Objectives**

By the end of this assignment, you will:

- Create static HTML/CSS templates.
- Build reusable components like the **Task Component**, **Task Creation Form**, and **Mood Selector**.
- Apply responsive design principles to ensure the app looks good on various screen sizes (desktop, tablet, mobile).

---

## Expected Folder Stucture

Ensure that your files are structured according to the following folder organization.

code

```
module-2/mood-based-todo-app/
├── Styles
│	├── index.css
│	├── login.css
│	├── tasksComponent.css
│	├── suggestedTaskComponent.css
│	├── taskCreationForm.css
│	├── moodSelecter.css
│	├── loginForm.css
├── Assets
│	├── // all assets you use in your project
├── Components
│	├── taskComponent.html
│	├── suggestedTaskComponent.html
│	├── taskCreationForm.html
│	├── moodSelecterForm.html
│	├── loginForm.html
├── index.html
```

---

## **Requirements**

### **Static Pages**

**Home Page**

![](https://resources.metana.co/public/50/b2/50b2ad300d1b55979392353c3a8e85377535544609047fe44d86a33c2c6269ba.png)

- Create a layout to display:
  - A list of tasks (will use the **Task Component** to display the tasks later in module 03).
  - A button to open up the form to create new tasks (with the **Form for Creating a Task Component** that will be later integrated into this page in module 03.)
  - A Button to open up the mood selector form (with the **Mood Selector Component** that will be later integrated into this page in module 03.)
- Include space to display suggested tasks based on the current mood and weather (You do not have to integrate the component yet, that will be done in the following module assessments).

### **Components**

In this assessment, you’ll create separate reusable components in individual HTML files. Later, in Module 03, we’ll integrate them into a complete web application. (Make sure you follow the expected folder structure)

**Login Page**

![](https://resources.metana.co/public/d8/80/d88035ef0a2c55da8c334b021533b0d4bef60a85799a159699ca869dd2c8776e.png)

- Design a simple component inside `loginForm.html` with the following content.
  - Input fields for **username/email** and **password**.
  - A **login button**.
  - Basic styling to make it visually appealing.
- Ensure the page adapts well to both desktop and mobile screens.

**Task Component**

![](https://resources.metana.co/public/2d/14/2d14cd0557ad671a892686bee9c3157a928bb9ba05abe04b7bb8dffe5055fdaf.png)

**Suggested Task Component**

![](https://resources.metana.co/public/6d/98/6d98a3e3672a312fb33c728e2cf00ed51571d8b87b5b908d31f647812e1d7e42.png)

- Build a reusable card or box to represent individual tasks. (You do not have to integrate this component with the main page yet)
- Include static placeholders for:
  - Task title.
  - Task description. (Optional)
  - Buttons for editing, completing, and deleting tasks.
- Ensure the component is styled neatly and adjusts well to different screen sizes.

**Form for Creating a Task**

![](https://resources.metana.co/public/4d/1e/4d1e9b6322754f1b0dff632170e9b4db35b531ddafb2dc04a8e8a579bfb3371b.png)

- Design a static form with fields for:
  - Task Title.
  - Task Description.
  - Due Date.
- Include a button to “Add Task.”
- Style the form to make it clean and user-friendly.

**Mood Selector**

![](https://resources.metana.co/public/a1/7d/a17d1d4416d17b80d1c242def47af68e5355abcd0a11310e2c1e448ca8f3b51f.png)

- Create a static dropdown or button group for selecting a mood (e.g., Happy, Neutral, Sad).
- Style it to match the theme of the app.

### **Responsive Design Requirements**

- Use **CSS Flexbox** or **CSS Grid** to build layouts that are adaptable to screen sizes.
- Ensure:
  - All components are fully responsive.
  - Text and interactive elements are easily readable and clickable on smaller devices.

---

## **Deliverables**

- The main page and all components as static HTML/CSS files.
- The complete assessment should follow the expected folder structure.

---

## **Submission Instructions**

1. Push your completed work to your Metana-fullstack-bootcamp GitHub repository in a folder named `mood-based-todo-app`.
2. Include:
   - `index.html` for the Home Page.
   - All html and css files for the static components.
3. Ensure your `README.md` file is updated with:
   - A brief description of your project.
   - Screenshots or links to any live demos (optional).

---

## **Tips for Success**

- Use consistent colors, fonts, and spacing to create a cohesive design.
- Test your design on multiple devices or use browser developer tools to simulate different screen sizes.
- Focus on simplicity and clarity; aim for clean and user-friendly layouts.

Good luck with this week’s assignment! If you have any questions, feel free to reach out to your instructor. Happy coding!
