# Guided Assignment: Building and Managing a PostgreSQL Database

# Practical Hands-on Experience with PostgreSQL

### Objective

The objective of this assignment is to provide step-by-step guidance for practical hands-on experience in working with PostgreSQL. Students will cover basic SQL queries, schema design, database management, migrations, and security considerations. Additionally, students will be required to write SQL scripts and check them into their Git project for review.

### Assignment Tasks

1. **Setting up PostgreSQL**
   - Follow the provided tutorials to install PostgreSQL on your operating system (macOS or Windows).
   - Launch the PostgreSQL service and access the psql console.
2. **Creating a Database**
   - Using the psql console, create a new database named “company\_records”.
   - Create a new user named “db\_user” with a password of your choice and grant all privileges on the “company\_records” database to this user.
   - Write the SQL commands for creating the database and user, and check them into your Git project.
3. **Designing a Database Schema**
   - Design a simple schema for managing employee records. Consider entities like Employees, Departments, and Salaries.
   - Utilize an online schema design tool like [dbdiagram.io](http://dbdiagram.io/) to visualize and finalize your schema.
   - Write the SQL commands for creating the tables based on your schema design and check them into your Git project.
4. **Creating Tables**
   - Based on your schema design, write SQL scripts to create tables for Employees, Departments, and Salaries in the “company\_records” database.
   - Ensure appropriate data types, primary keys, and constraints are applied.
   - Check the SQL scripts for creating tables into your Git project.
5. **Inserting Data**
   - Populate the tables with sample data. Include at least 5 employees, 3 departments, and corresponding salary information.
   - Use INSERT INTO statements to add data to the tables.
   - Write SQL scripts for inserting data into the tables and check them into your Git project.
6. **Basic SQL Queries**
   - Write SQL queries to demonstrate the following:
     - Selecting all employees from the Employees table.
     - Selecting employees based on their department ID.
     - Selecting employees with a salary greater than a specified amount.
     - Deleting an employee record based on their employee ID.
   - Write SQL scripts for these queries and check them into your Git project.
7. **Intermediate SQL Queries**
   - Explore JOIN operations to retrieve information from multiple tables. Write queries to:
     - Retrieve employee details along with their department information.
     - Calculate the total salary expenditure for each department.
     - Find the average salary of employees in the company.
   - Write SQL scripts for these queries and check them into your Git project.
8. **Migrations**
   - Create a SQL migration script to add a new column “Hire\_Date” to the Employees table.
   - Apply the migration script to update the schema accordingly.
   - Ensure that existing data is preserved during the migration process.
   - Write the SQL migration script and the commands to apply it, then check them into your Git project.

### **Note**

- *Regularly commit and push your changes to the Git repository to track your progress.*

### **Resources**

- PostgreSQL: [https://www.postgresql.org](https://www.postgresql.org/)
- PostgreSQL Documentation: <https://www.postgresql.org/docs/>
- PostgreSQL Installation on macOS: <https://www.youtube.com/watch?v=PShGF_udSpk>
- PostgreSQL Installation on Windows: <https://www.youtube.com/watch?v=uN0AfifH1TA>
