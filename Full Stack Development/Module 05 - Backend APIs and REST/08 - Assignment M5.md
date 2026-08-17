# Assignment M5

Learn to build a functional backend API using Node.js and MongoDB. Implement data models, perform CRUD operations, and connect the backend to the frontend in later modules.

## **Assignment Objectives**

By the end of this assignment, you will know to:

- Set up MongoDB (either locally or using MongoDB Atlas) and connect it to a Node.js application.
- Build backend routes for CRUD operations (Create, Read, Update, Delete) related to core resources (e.g., `Users` and `Blogs`).
- Implement Mongoose for data modeling and validation in MongoDB.
- Test the backend API using Postman to ensure routes are functioning correctly.

---

## Expected Folder Stucture

Ensure that your files are structured according to the following folder organization.

code

```
module-5/
├── db/
│   ├── blogQueries.js   // all crud functions exported.
│   ├── dbconn.js
│   └── userQueries.js
├── routes/
│   ├── blogsRouter.js
│   └── userRouter.js
├── scripts/
│   ├── seedDb.js
├── models/
│   ├── Blog.js
│   └── User.js
├── .gitignore
├── config.js
├── example.env
├── .env
├── index.js
├── package.json
└── package-lock.json
```

---

## **Requirements**

**Initialize a new Node Project**

- Initialize a new Node.js project by running `npm init -y`.
- Update the `package.json` file to include a start script for running the server with `nodemon`.
- Ensure that the project follows the given file structure.

**Set Up MongoDB Database and Connnection**

- Create a MongoDB account if you don’t already have one.
- Set up a database using MongoDB Atlas or install MongoDB locally.
- Install `mongoose` to establish a connection between your Express application and MongoDB.
- Ensure that MongoDB is successfully connected asynchronously before starting the server to prevent any runtime errors.

**Set Up .env**

- Create a `.env` file to securely store sensitive data like the database URI.
- Create an `example.env` file with placeholder values that mirror the structure of your main `.env` file.
- Install `dotenv` to securely manage environment variables.
- Create a `config.js` file to load all environment variables and export them for use across different parts of the project.

**Build Mongoose Models for Core Data**

- Define Mongoose schemas and models for `User` and `Blog` with appropriate validation rules:
  - `User` Schema: name, email and timestamps.
  - `Blog` Schema: title, content, user (reference to `User`), and timestamps.

**Implement CRUD Routes for API**

- Install and configure `body-parser` in Express to properly handle incoming JSON data.
- Create a separate folder named `routes` and add two new files: `blogsRouter.js` and `userRouter.js`. These files will be used to define and manage the CRUD routes for blogs and users.
- Make sure to configure the main server file to import and use the routes from the `routes` directory for proper request handling.
  - User Router – `/api/users`
  - Blogs Router – `/api/blogs`
- Create two separate files: `blogQueries.js` and `userQueries.js`. These files will contain the CRUD functions for managing blogs and users. The functions will be exported from these files so they can be imported and used in the corresponding router files.
- Implement backend API routes using Express.js to perform CRUD operations in the respective files. (Refer to the following table and make sure you follow every step.)

| **Action** | **Method** | **Endpoint** | **Description** | **Expected Response** |
| --- | --- | --- | --- | --- |
| Create a new user or blog | `POST` | `/` | Adds a new user or blog to the database. | A user or blog object |
| Get all users or blogs | `GET` | `/` | Retrieves a list of all users or blogs. | An array of users or blogs |
| Get a specific user or blog | `GET` | `/:id` | Fetches details of a specific user or blog based on the provided ID. | A user or blog object. |
| Update user or blog details | `PUT` | `/:id` | Updates the details of an existing user or blog by ID. | A user or a blog object. |
| Delete a user or blog | `DELETE` | `/:id` | Removes a specific user or blog from the database using the provided ID. | A user or a blog object. |

**Morgan for middleware**

- Install Morgan as middleware to log every incoming request.
- Configure your Express app to use Morgan for request logging.

**Enable Cors**

- Install `CORS` and configure Express to handle cross-origin requests by enabling CORS in your app.

**Create a seedDb.js script**

- Create a `seedDB.js` file inside the `scripts` folder to populate the database with initial dummy data.
- Add a `db:seed` script in your `package.json` to run the `seedDB.js` file and populate the database with the dummy data.

**Test API Routes with Postman**

- Test the CRUD operations using Postman:
  - Add test cases for user registration, blog creation, updating, and deletion.
  - Ensure the correct response codes and data are returned.

## **Deliverables**

- Backend code with Express.js and MongoDB integration.

## **Submission Instructions**

Push your completed code to the `Metana-fullstack-bootcamp` GitHub repository. Ensure the repository contains:

- `index.js` or `server.js` for starting the backend server.
- `models/` directory for Mongoose models.
- `routes/` directory for API routes.
- `.env` file (with sensitive information excluded from the public repository).

Include a brief description of the backend in your `README.md`.

## **Tips for Success**

- **Keep Your Routes Organized**: Structure your routes logically in separate files (e.g., `userRoutes.js`, `taskRoutes.js`) to keep the code maintainable and easy to debug.
- **Use Mongoose’s Built-in Validation**: Take advantage of Mongoose’s schema validation (e.g., `required`, `unique`, `minlength`) to ensure data consistency and avoid manual validation in the routes.
- **Test Thoroughly**: Use Postman to test your API endpoints carefully, checking for correct responses and edge cases (e.g., duplicate users, missing fields).
- **Stay Consistent with Environment Variables**: Ensure your `.env` file is correctly set up and included in `.gitignore` to keep sensitive data like database credentials safe.
