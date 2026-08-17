# Assignment M6

Implement and integrate PostgreSQL with your backend to store structured data and perform relational queries. Transition from MongoDB to PostgreSQL for a relational approach.

## **Assignment Objectives**

**By the end of this assignment, you will know to:**

- Integrate PostgreSQL with your backend and implement relational database schemas.
- Convert MongoDB CRUD operations to equivalent SQL queries using PostgreSQL.
- Design and test relational models such as `Users` and `Blogs` with foreign key relationships.
- Replace MongoDB queries with SQL queries and interact with the PostgreSQL database using Node.js.

---

## Expected Folder Stucture

Ensure that your files are structured according to the following folder organization.

code

```
module-6/
├── db/
│   ├── blogQueries.js   // all crud functions exported.
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
├── .env
├── index.js
├── package.json
└── package-lock.json
```

---

## **Requirements**

### Copy Backend from Module 5

- **Duplicate** the folder from the **Module 5 assessment** as a starting point.
- **Remove** all MongoDB-related content:
  - Delete the **models** folder.
  - Uninstall **mongoose** and any other related Node modules.

### **Set Up PostgreSQL & Design Database Schema**

- Install PostgreSQL locally.
- Create a `setup-db.sql` files inside the `scripts` folder and include SQL queries to create tables for entities `Users` and `Blogs`.
- Remember to create relationships between `Users` and `Blogs` (e.g., a `User` has many `Blogs`) by implement foreign keys.
- Create an `initDb.js` file and write JavaScript code to execute the `setup-db.sql` file, ensuring the database is initialized with the required tables.
- Add a `db:init` script in your `package.json` to run the `initDb.js` file and set up the database with all necessary entities.

### **Integrate PostgreSQL with Backend**

- Update the `dbconn.js` file to establish a connection with the PostgreSQL database..
- Use the `pg` library to connect to PostgreSQL from your Node.js backend.
- Ensure consistency by following the same route structure and Response formate from **Module 5** for all CRUD operations.
- Replace the MongoDB queries inside `blogQueries.js` and u`serQueries.js` from **Module 5** with PostgreSQL queries. Ensure the routes (`/api/users`, `/api/blogs`) are now working with the PostgreSQL database.

### **Prepare for Frontend Integration**

The backend API developed here will be connected to your React frontend in **Module 8**, so make sure your endpoints are standardized and return the data in a format that React can easily consume (JSON).

## **Deliverables**

- PostgreSQL database schema and queries.
- Backend code with PostgreSQL connected.

## **Submission Instructions**

- Push your completed work to the `Metana-fullstack-bootcamp` GitHub repository.
- Ensure your `README.md` describes the database setup and usage.

## **Tips for Success**

- **Understand SQL Joins**: Focus on understanding how to use `JOIN` queries in SQL to fetch related data, such as linking users and blogs.
- **Practice Querying Data**: Practice writing SQL queries to fetch, update, and delete data to become comfortable with PostgreSQL’s syntax.
- **Leverage PostgreSQL’s Features**: Use features like `timestamps`, `foreign keys`, and `ON DELETE CASCADE` to manage data integrity.
- **Test SQL Queries**: Write sample queries directly in the PostgreSQL database before integrating them into your Node.js app to ensure they work correctly.
