# Assignment M9

Implement user authentication and authorization in the backend using JWT and integrate it with your React frontend. Secure routes based on user roles.

## **Assignment Objectives**

**By the end of this assignment, you will know to:**

- Implement user authentication using JWT.
- Secure routes with role-based access control (RBAC).
- Integrate frontend login and registration forms with the backend authentication.
- Protect pages based on user roles (admin vs. regular user).

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
│   │   ├── blogs.js
│   │   ├── users.js
│   │   └── auth.js
│   ├── context/
│   │   └── AuthProvider.jsx
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
│   │	├── Login.jsx
│   │	├── SignUp.jsx
│   │	├── Profile.jsx
│   │	├── NotFound.jsx
│   │	├── AdminDashboard.jsx
│   │	├── ProtectedRoute.jsx
│   │	└── PrivateRoute.jsx
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
├── controllers/
│   ├── auth.js
│   └── contact.js
├── db/
│   ├── blogQueries.js
│   ├── dbconn.js
│   └── userQueries.js
├── middlewares/
│   └── auth-middleware.js
├── routes/
│   ├── blogsRouter.js
│   └── userRouter.js
│   └── authRouter.js
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

### Setting Up Backend

**Add a new Script**

- Add a `install:all` script in the backend’s `package.json` that will allow you to install all node modules on both the frontend and backend.

**Set Up Authentication**

- Create an `auth.js` file within the `controllers` directory.
- Implement user registration and login functions inside `auth.js` using JWT for authentication, and export them for use in other files.
  - **User Registration**: (Route – `/create-account`)
    - Collect `username`, `email`, and `password` from the user and create a new account.
    - Create roles for users (e.g., `admin`, `user`).
  - **User Login**: (Route – `/login`)
    - Retrieve `username` and `password` from the user, validate the credentials, and issue an access token upon successful authentication.
- Install and utilize `bcrypt` to securely hash passwords before storing them in PostgreSQL.
- Install and configure the `validator` package to validate user inputs before processing authentication operations.
- Create a `middlewares` folder, and within it, add an `auth-middleware.js` file to handle access token verification for protected routes.
- Remember to add a route for authentication in your backend.
  - Auth Router – (**ROUTE** – `/api/auth`)

**Integrating Authentication in the Frontend**

- **Implement Authentication Pages in React:**
  - Develop login and registration pages to allow users to authenticate. Ensure adherence to the following route specifications:
    - **Login Page:** (**ROUTE** – `/login`)
    - **Sign-Up Page:** (**ROUTE** – `/create-account)`
  - Ensure these two pages are added to the navigation bar, but only display them when the user is not logged in.
- **Authentication Functions**
  - Create an **`auth.js`** file inside the `api` folder to handle authentication-related API requests. This file should include functions for **account creation** and **login**, which will be exported for use across the application.
  - Create a **`user.js`** file to manage **user-related operations**, such as retrieving user details and any other necessary functionalities.
- **Token Management:**
  - Upon successful registration, store the JWT token in local storage and include it in the headers of all API requests for authentication. (Focus on the following point)
- **Set Up Authentication Context:**
  - Create a `context` folder and add an `AuthProvider.jsx` file to manage authentication state across the application. This context should:
    - Store the access token and user details upon login.
    - Provide authentication-related properties:
      - **`isAdmin`** → Returns `true` if the user is an admin.
      - **`isLoggedIn`** → Returns `true` if the user is authenticated.
    - Handle logout by clearing the access token and user details.
- **Implement Protected Routes:**
  - Create a `ProtectedRoute.jsx` component to check authentication status via `AuthProvider.jsx`.
    - If authenticated, allow access to the protected page.
    - If not, redirect the user to the login page.
  - Develop a **Profile Page (`Profile.jsx`)** as a protected route, accessible only when the user is logged in.
    - Wrap this page with the `ProtectedRoute` component to enforce authentication.
    - Display this page in the navigation bar only when the user is logged in.
    - Implement a **Logout** button that allows users to securely sign out of the application.
      - Utilize the authentication context to handle the logout process seamlessly.
- **Admin-Specific Access Control:**
  - Create a `PrivateRoute.jsx` component that restricts access to admin-only pages.
    - Non-admin users should be redirected to a 404 page.
  - Wrap the **Admin Dashboard (`AdminDashboard.jsx`)** with `PrivateRoute` to ensure that only admins can access it.
  - Implement the **Admin Dashboard** to allow admins to:
    - View a list of all users.
    - Manage and oversee all blog posts on the platform.

## **Deliverables**

- A full stack application with authentication implemented.
- The complete assessment should follow the expected folder structure.
- Fully functional page

## **Submission Instructions**

- Push the completed code to your `Metana-fullstack-bootcamp` GitHub repository.
- Update the `README.md` with detailed instructions on how to use the authentication system.

## **Tips for Success**

- **Secure Your JWT Tokens**: Store JWT tokens in `localStorage` on the frontend.
- **Test Role-Based Access**: Make sure that protected routes are correctly secured based on the user’s role (admin vs. regular user). Test both authenticated and unauthorized access.
- **Hash Passwords**: Use `bcryptjs` to hash user passwords before storing them in the database, and always use HTTPS in production to secure communication.
- **Validate Input**: Ensure both frontend and backend validate user input, particularly for email and password fields, to prevent vulnerabilities like SQL injection.
