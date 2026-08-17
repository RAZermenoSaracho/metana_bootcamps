# Introduction to Environment Variables and Application Secrets

### What are application secrets ?

- Any information that we need to pass to our application
  - app names
  - emails
  - app URLs
  - database URIs
- Any secret information, just for our server
  - API keys and secrets
  - Database passwords and users
  - Server encryption secrets

[YouTube video player](https://www.youtube.com/watch?v=tc_jJxwOECM)

### Where do we store application secrets ?

- We typically keep these either in env files, or directly in key-value pairs that are provided to our server by our platform.
- These are passed to our application as **environment variables**

### How do they get provided to your application ?

**Env files**

Our app may read an env file directly from diskThis will work for development, and for deploying on VPS servers, but it will not work for a PaaS platform like HerokuNotes on Env files with PaaS:

- If this application is hosted on a PaaS, it may or may not have direct access to disk storage— be careful about including calls to open a file directly from your code.In the case of PaaS, using `dotenv` will probably not work — because we do not commit our .env file to the project, so it doesn’t get uploaded automatically to the PaaS server.Therefore, you will have to paste or upload the env files directly to the PaaS in a control panel.
  - Newer versions of Node.js (from version 20) allow you to specify an environment variable file when calling the application:`` # Specify your env file directly with the `--env-file` flag, for Node v20+ # This directly loads the environment variables, without need for using # packages like "dotenv" node --env-file=.env app.js ``

**Env variables**

- We may also set our env variables directly in our server OS environment
- This can be done from the server shell / command line
- You can also pass these variables directly when you call a process, such as starting your app.
- Example: `NODE_ENVIRONMENT=production npm start`

### Pasting values directly into PaaS control panel

- Your IaaS / PaaS provider’s control panel should give you options for adding setting key-value pairs directly
- These are automatically passed to your application as environment variables

### Security notes

- Never hardcode secrets
  - Never put secret values directly into your app code.
  - Always use env variables for values that may change
- Never commit env files to Git
  - Always use a `.gitignore` file that excludes `.env` files from your code.
  - Anything you commit to code is public — anyone who can see your repo can see those secrets in the Git commit history.
  - Add placeholder files: Any .env files you include should be ignored — but you can safely create and commit an `example.env` file with placeholder variables
- Don’t output secrets to logs
  - Logs are a frequently source of data leaks — if you do `console.log("username", username", "password", password)`, this may end up logs that outsiders can view and exploit

## Links

- [YouTube video player](https://www.youtube.com/watch?v=tc_jJxwOECM)
