# Assignment M8

Build the frontend of the application using React, integrate with the backend APIs developed in **Modules 6**, and implement the UI/UX designs from **Module 7**.

---

## **Assignment Objectives**

**By the end of this assignment, you will know to:**

- Build a React frontend that implements the UI/UX designs created in the previous module.
- Integrate your React components with the backend API to fetch and display data dynamically.
- Implement state management to manage and pass data between components.
- Use React Router to set up routing for different views (e.g., Homepage, Blog Details, User Profile).

---

## Expected Folder Structure

Ensure that your files are structured according to the following folder organization.

code

```
client/
├── public/
│   └── index.html
├── src/
│   ├── api/
│   │   └── blogs.js
│   ├── components/
│   │   ├── Footer.jsx
│   │   ├── Header.jsx
│   │   ├── Layout.jsx
│   │   └── Navigation.jsx
│   ├── pages/
│   │   ├── About.jsx
│   │   ├── Blogs.jsx
│   │   ├── Contact.jsx
│   │   ├── Home.jsx
│   │   ├── Projects.jsx
│   │   ├── SingleBlog.jsx
│   │	├── NotFound.jsx
│   │	└── AdminDashboard.jsx
│   ├── App.css
│   ├── App.js
│   ├── App.test.js
│   ├── index.css
│   ├── index.js
│   ├── logo.svg
│   ├── reportWebVitals.js
│   ├── setupProxy.js
│   └── setupTests.js
├── .gitignore
├── README.md
├── package.json
├── package-lock.json
└── tailwind.config.js

server/
├── db/
│   ├── blogQueries.js
│   ├── dbconn.js
│   └── userQueries.js
├── routes/
│   ├── blogsRouter.js
│   └── userRouter.js
├── scripts/
│   ├── initDb.js
│   ├── seedDb.js
│   └── setup-db.sql
├── .gitignore
├── config.js
├── example.env
├── index.js
├── package.json
└── package-lock.json
```

---

## **Requirements**

**Set Up React App**

- Use `create-react-app` to initialize a new React project inside the `client` directory.
- Install necessary dependencies, such as `react-router-dom` for routing and `axios` for making API requests.
- Install `http-proxy-middleware` to setup proxy on the frontend to forward all API calls to the backend.
- Setup proxy to be [http://localhost:3000](http://localhost:3000/) on the client `package.json`
- Start implementing the frontend part of your UI design form the last module assessment.

**Build React Components**

- Implement React pages for the following:
  - **Homepage – (Route – `/`)**
    - Ensure all sections from the previous module are implemented.
  - **Blogs – (Route – `/blogs`)**
    - A dedicated page to display all blogs.
  - **Projects – (Route – `/projects`)**
    - A separate page showcasing all your projects.
  - **About – (Route – `/about`)**
    - A page that introduces you and your background.
  - **Contact – (Route – `/contact`)**
    - A page with a contact form and your contact details.
  - **Single Blog Page – (Route – `/blogs/:id`)**
    - A detailed view for displaying individual blog information.
  - **Admin Dashboard – (Route – `/admin-dash`)**
    - Includes user management and blog creation features. (For now, display dummy data; full functionality will be added in Module 09.)
  - **Not Found – (Route can be anything that is not the above)**
    - A 404 page that will show when the user navigates to an unknown route.
- Ensure components are modular and reusable.
- Make sure to use the exact same route mentioned in the specification.

**React Routing**

- Set up `react-router-dom` for navigation between pages (e.g., homepage, individual blog pages, dashboard).
- For adding path to routes, refer to the above section and add the specified one.
- Create a `Navigation.js` component inside the components folder. \*\*\*\*This will handle the navigation bar of your application. Make sure it includes links to all necessary pages.
- **Create `Header` and `Footer` components inside the components folder**:
  - The **Header** should contain the logo, navigation component and other necessary details.
  - The **Footer** should include copyright information, links to important resources, and other necessary details.
- **Create a `Layout` component**:
  - This will serve as a wrapper for all pages, ensuring consistency across the app.
  - It should include the **Navigation, Header, and Footer** components.
  - Wrap all the application routes within this `Layout` component to maintain a uniform structure.

**Connect Frontend to Backend**

- Use `axios` to make API calls to your Node.js backend (from **Module 6**).
- Display dynamic data in the frontend (e.g., render the list of blogs from the `/blogs` endpoint).
- Create an `api` folder and organize all API-related functions within it. For instance, create a file like `blogs.js` to handle all Axios requests related to blogs. Export these functions so they can be easily imported and used in the relevant JSX files.
- create a `serverProxy.js` and utilize the `http-proxy-middleware` to create a proxy that forwards all requests from the frontend to the backend. (Refer to the provided file structure to see where you can add this file.)
  - Make sure that all requests are forwarded to `http://localhost:3000/api`

**Setup Concurrently**

- Install `concurrently` on frontend.
- Add a `dev` script in the frontend’s `package.json` that will allow you to run both the frontend and backend in development mode at the same time.
- Make sure that the backend runs on port `3000` and the frontend on port `3001`

**Setup backend to run production build**

- Include a script `build:frontend` in the backend `package.json` to run production build on the frontend.
- Setup express to feed frontend build on production mode.
  - In production mode, Express will serve the static files from the `frontend/build` directory.
  - You’ll need to configure Express to serve the frontend files when the app is running in production.
- Include a script `prod` in the backend `package.json` to run the application on production mode.
  - This script will typically set the `NODE_ENV` to `production` and run the app.

## **Deliverables**

- React app with all components integrated with the backend.
- The complete assessment should follow the expected folder structure.
- Fully functional pages.
- A link to your GitHub repository.

## **Submission Instructions**

- Push the completed React project to the `Metana-fullstack-bootcamp` GitHub repository inside the `module-8` folder.
- Include a detailed `README.md` describing your React components and how they interact with the backend.
