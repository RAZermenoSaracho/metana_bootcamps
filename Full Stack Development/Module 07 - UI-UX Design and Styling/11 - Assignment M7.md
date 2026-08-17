# Assignment M7

Design the frontend UI/UX using Figma and implement it with TailwindCSS. This will be the foundation for your React components in **Module 8**.

## **Assignment Objectives**

**By the end of this assignment, you will know to:**

- Create responsive UI/UX designs for your application using Figma, focusing on ease of use and aesthetic appeal.
- Build a static frontend with TailwindCSS to match the Figma designs.
- Ensure your design is fully responsive across multiple device types (mobile, tablet, desktop).

---

## Expected Folder Structure

Ensure that your files are structured according to the following folder organization.

code

```
module-7/
├── node_modules/
├── public/
│   ├── assets/
│   │   └── images/    // all your images here. 
│   ├── index.html     // you can break this down into sub files if needed. 
│   ├── blogs.html
│   ├── singleBlog.html
│   └── adminDashboard.html
├── server.js
├── figma_link.txt
├── package.json
├── package-lock.json
└── .gitignore
```

---

## **Requirements**

**A. Design UI/UX in Figma – Personal Portfolio Application**

You’ll be designing a **personal portfolio + blog application** that will serve as your own portfolio site to showcase your work and skills. This is your chance to create something that represents you as a developer, so make it clean, professional, and uniquely yours.

### What to Design

Create **wireframes and high-fidelity mockups** in Figma for the following key pages:

### **Homepage**

- Acts as the landing page of your portfolio.
- Should include:
  - A **navigation bar**
  - An **intro/hero section** (e.g., “Hi, I’m [Your Name]”)
  - **About Me**
  - **Skills / Tech Stack**
  - **Projects Preview** (links to blog or project details)
  - **Blog section preview**
  - **Contact Me / Footer**

### **Blog List Page**

- Displays a few blogs in a grid or list format.
- Each blog should have a title, short preview, and date.

### **Blog Detail Page**

- Displays full content of a selected blog post.
- Include author info, tags, and a back button to the blog list.

### **Admin Dashboard**

- For managing blogs and users.
- Include:
  - Blog post creation/editing
  - Blog list (with edit/delete options)
  - User management section (basic list view is enough)

---

### **User Flow and Interactions**

- Define how users move between pages (e.g., Homepage → Blog List → Blog Detail).
- Use **Figma Prototyping** to simulate these transitions.
- Implement **hover effects** on:
  - Navigation items
  - Buttons
  - Cards
  - Blog previews

---

### **Explore Design Inspiration**

Look up **software engineer portfolios** on Dribbble, Behance, or even real developer websites to get inspiration. You’re free to mix layouts and styles you like, but the final design should feel cohesive and represent your personal brand.

---

### Submission Instructions for the Figma design.

- Create a file named `figma_link.txt`.
- Paste the **shareable Figma link** on the **first line only**, with no extra text.
- Make sure the link has the correct permissions for viewing.

**Define UI Components in Figma**

- Break down your design into reusable UI components such as buttons, cards, modals, and forms.
- Ensure the design is mobile-responsive and easy to use.

---

**B. Implementing Design with TailwindCSS**

- Initialize a **simple Express application** using `npm init -y`.
- Follow the **expected folder structure** and create the necessary files and directories. If you have any doubts, feel free to reach out to your instructor.
- Configure **Express** to serve HTML files from the `public` folder and set up the necessary routes.
- Install and properly configure **TailwindCSS** within your application.
- Implement the **design using TailwindCSS**, ensuring a clean and responsive layout.
- Since this module does not involve backend development, use **dummy data** to populate the site as realistically as possible.
- Ensure the **design is fully responsive**, adapting seamlessly to both desktop and mobile screens.
- Maintain design consistency by aligning the implementation with the **Figma document** provided.

**Prepare for React Integration**

- This design will serve as the basis for the React components you’ll build in **Module 8**. Ensure that the structure is clean and easy to translate into React components.

## **Deliverables**

- A file containing the **link to the Figma design** for easy reference.
- An **HTML application** developed with **TailwindCSS**, fully aligned with the Figma design specifications.
- The project must adhere to the **expected folder structure** for consistency and organization.
- Ensure that all pages are **fully functional** and meet the design requirements.

## **Submission Instructions**

- Push the completed design and code to your `Metana-fullstack-bootcamp` GitHub repository.
- Include a `README.md` with descriptions of your design process and any key design decisions.

## **Tips for Success**

- **Plan Your Layouts**: Start with wireframes in Figma to plan the layout before diving into the design process. This will give you a clear roadmap for your HTML and CSS.
- **Consistency in Design**: Use consistent design elements, like color schemes, typography, and button styles, to create a unified look throughout the app.
- **TailwindCSS Utilities**: Take advantage of Tailwind CSS’s utility classes to quickly implement responsive layouts and styling without writing custom CSS.
- **Test Responsiveness**: Use browser developer tools to test the responsiveness of your design across different screen sizes (desktop, tablet, mobile).
