# To-do app

[YouTube video player](https://www.youtube.com/watch?v=LoYbN6qoQHA)

- **Setup Development Environment:**
  - Install Create React App.
  - Use `npx create-react-app todo-app` to initialize the project.
  - Navigate into the project directory: `cd todo-app`.
- **Install Necessary Packages:**
  - Install required packages: `npm install uuid npm install @fortawesome/fontawesome-free`
- **Create Components:**
  - Create components directory: `src/components`.
  - Inside `src/components`, create the following files:
    - `ToDoForm.js`
    - `ToDoList.js`
    - `ToDoItem.js`
    - `EditToDoForm.js`
- **Implement ToDoForm:**
  - Inside `ToDoForm.js`, write code to create a form for adding new tasks.
  - Use state to track user input for new tasks.
  - Implement event handlers for input change and form submission.
- **Display ToDo List:**
  - Inside `ToDoList.js`, write code to display the list of tasks.
  - Map through the list of tasks and render individual `ToDoItem` components.
  - Pass task data as props to each `ToDoItem`.
- **Toggle Task Completion:**
  - Inside `ToDoItem.js`, implement functionality to mark tasks as complete or incomplete.
  - Add event handling to toggle task completion.
  - Update task status in the state accordingly.
- **Delete Tasks:**
  - Inside `ToDoItem.js`, implement functionality to delete tasks from the list.
  - Add event handling to delete tasks.
  - Update the state by removing the deleted task from the list.
- **Edit Tasks:**
  - Inside `ToDoItem.js`, implement functionality to edit existing tasks.
  - Add event handling to enable editing mode.
  - Display an input field to edit the task.
  - Update the task in the state with the edited value.
- **Styling:**
  - Add CSS styles to components for layout and aesthetics.
  - Apply styles to differentiate completed tasks, editing mode, etc.
- **Testing and Debugging:**
  - Test the application to ensure all functionalities work as expected.
  - Debug any issues or errors encountered during testing.
- **Deployment:**
  - Build the React application for production: `npm run build`.
  - Deploy the app to a hosting platform like Netlify, Vercel, or GitHub Pages.

## Links

- [YouTube video player](https://www.youtube.com/watch?v=LoYbN6qoQHA)
