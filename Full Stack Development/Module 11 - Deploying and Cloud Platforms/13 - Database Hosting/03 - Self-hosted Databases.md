# Self-hosted Databases

A self-hosted website is one that is hosted on a server that you own or control, as opposed to being hosted by a third-party service provider. With a self-hosted website, you manage the server infrastructure, including hardware, software, and security configurations.

- When self-hosting a database, you can run it either directly on the same server as your application, or you can run it externally on another server.
- If you run it on another server, it should be set up in the same private network — this prevents outsiders from connecting to your database for malicious purposes.

### Installing a database

- Databases can be installed directly on the server using the system package. For example, on Ubuntu 20.04

code

```
# Install PostgreSQL server
sudo apt install postgresql postgresql-contrib
```

- After you’ve installed the database, you’ll need to start the service:

code

```
# Start the service
sudo systemctl start postgresql.service
```

### Preparing your database for use

- After installing and starting the database service, you will need to initialize a database and set up user permissions and roles.
- Creating databases, tables, users, and seeding can all be done via SQL scripts. Ideally, these tasks should be handled by functions (such as `initializeDatabase`, `createDbTables`, and `seedDb` functions).
- Ensure you can run your database initialization, table creation, and seeding functions from an NPM script. This allows performing these tasks in a CI/CD pipeline in the future.
- It is also possible to install databases using Docker. If you’re familiar and comfortable with Docker, this is the preferable method, but it adds a little extra complication.
