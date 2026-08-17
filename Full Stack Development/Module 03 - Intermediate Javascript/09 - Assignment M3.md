# Assignment M3

This week’s assignment focuses on bringing your To-Do app to life by adding interactivity using JavaScript and implementing CRUD (Create, Read, Update, Delete) functionality. Your goal is to enhance the app with features that allow users to manage their tasks dynamically.

---

## **Reference**

You may use the demo application below as a reference for expected behavior and UI flow.

- **Demo App**: [Click here](https://mood-weather-todo.vercel.app/)

---

## **Assignment Objectives**

By the end of this assignment, you will:

- Implement interactivity in your To-Do app using **JavaScript**.
- Create full **CRUD functionality** to manage tasks:
  - Add tasks dynamically.
  - Display tasks from storage.
  - Update task details.
  - Delete tasks from the list.
- Understand how to persist tasks using **localStorage**.

---

## Expected Folder Stucture

Ensure that your files are structured according to the following folder organization.

code

```
module-3/
├── Styles
│		├── index.css
│		├── tasksComponent.css
│		├── suggestedTaskComponent.css
│		├── taskCreationForm.css
│		├── moodSelecter.css
│		└── loginForm.css
│
├── Scripts
│		├── index.js
│		├── tasksComponent.js
│		├── suggestedTaskComponent.js
│		├── taskCreationForm.js
│		├── moodSelecter.js
│		└── loginForm.js
│
├── Assets
│		└── // all assets you use in your project
│
└── index.html  // all components created during the previous assessment should be intergrated in here
```

---

## **Requirements**

### **Connect Everything**

**Integrate Components from Week 02 – Refer to the Link Provided to get more Clarity**

- This assessment focuses on integrating all components developed in Week 02 using JavaScript to ensure seamless interactivity.
  - Connect the **Profile** button to displays the login form centered on the page.
  - Connect the **Add Task** button to open the task creation form, positioned centrally on the page.
  - Connect the **Mood** button to open the **Mood Slider** centered to the page.
  - Integrate the **Task Component** and **Suggested Task Component** to display tasks in the list on the home page. For now, use dummy data for visualization—later in the assessment, you’ll implement dynamic functionality.
- Upon successful integration, you can go ahead and delete the components folder. (Only once you have successfully moved all components into integration)

### **Auth Functionalities**

**Login Functionality**

- In the Login Form, once the Login Button is clicked, save the user details to the localStorage and close the dialog box.
- Add Form Validation to make sure that the user has entered Valid Information.

![](https://resources.metana.co/public/d3/af/d3af96b9cbeb53f5e96e36397ca6d1c7a72278598325e88bfd0ccee0d8b66a7e.png)

- Display a success Message on the bottom left corner when the operation was successful.

![](https://resources.metana.co/public/d8/b1/d8b1ebd719affaeb82073d2382d8d709e4d492cb2233d962348e3eee120bea01.png)

- Make sure to change the name to the user name from Guest on the Top-Left corner after a successful login.

**Edit User Details**

![](https://resources.metana.co/public/79/36/7936535f75cd9eb8458b09f07cfffa4913c04f90d61deb83d32c2aa9974730ab.png)

- When the **Profile** button is clicked, check if user details are already stored in local Storage:
  - If details exist, display an **Edit Profile Form** in the dialog box, pre-filled with the user’s information, allowing them to update their details.
  - If no details are found, display the **Login Form** instead.
- When the **Save Changes** button is clicked in the **Edit Profile Form**, update the user details in localStorage with the modified information.
- Make sure Form Validation is Implemented.
- Implement a **Logout** button that clears user details from localStorage. Upon logout, the **Login Form** should automatically be displayed in the dialog box.
- Display a success Message on the bottom left corner when the operation was successful.
- Make sure to change the name to the Guest from user name on the Top-Left corner after a successful logout.

### **Task Functionalities**

**Add Task Functionality**

- In the **Task Creation Form**, once **Create Task** is clicked, save the task to localStorage and display it in the task list dynamically.
- Add Form Validation to make sure that the user has entered Valid Information.

![](https://resources.metana.co/public/b8/85/b885d018f356042194463ae997988ae4e54a875dbf61ddd62036c9c7a59ffc04.png)

**Display Task List**

![](https://resources.metana.co/public/d6/d0/d6d025af473dda9a10d0784e4696d70680a8e3c00d35b374561f96d609eb53ef.png)

- Fetch tasks from localStorage upon page load.
- Dynamically display tasks in a styled format using the **Task Component** in the home page.
- When clicked on the check mark on **Task Component**, update the task status to **complete** in localStorage and visually distinguish the task (e.g., strike-through text or change background color).

**Edit Task**

![](https://resources.metana.co/public/1d/dd/1ddd4db4250dc539919b568f7bfb9563e5a7d266c271c68970251e226d8790b8.png)

- Clicking on a task should open an **Edit Task Component** with pre-filled details, allowing users to update the title, duration, and due date.
- Once **Save changes** is clicked, save the updated task details to localStorage and update the task in the list.
- Display a success Message on the bottom left corner when the operation was successful.

**Delete Task**

![](https://resources.metana.co/public/b3/9d/b39d8c499f7c6e5a28c3a2c5e45c01678ad220ee8a5513a25f4eb2b3e448568b.png)

- Add a **Delete Button for Tasks**
- Ensure the button is only visible when the user hovers over the task component.
- Clicking the **Delete Button** should remove the corresponding task from localStorage.
- Make sure to update the task list immediately to reflect the deletion.
- Display a success Message on the bottom left corner when the operation was successful.

### **Responsive Design Requirements**

- Use **CSS Flexbox** or **CSS Grid** to build layouts that are adaptable to screen sizes.
- Ensure:
  - All Pages and Components are fully responsive.
  - Components adjust gracefully for desktop, tablet, and mobile views.
  - Text and interactive elements are easily readable and clickable on smaller devices.

---

## **Deliverables**

A fully functional web application with all components integrated and CRUD operations implemented.

---

## **Submission Instructions**

1. Push your completed work to your Metana-fullstack-bootcamp GitHub repository in a folder named `mood-based-todo-app`.
2. Make sure all files are included.
3. Update your [README.md](http://readme.md/) file with the new updates.

---

## **Tips for Success**

- Optimize Your JavaScript Code for Better Performance. (Follow the file structure given)

Good luck with this week’s assignment! If you have any questions, feel free to reach out to your instructor. Happy coding!
