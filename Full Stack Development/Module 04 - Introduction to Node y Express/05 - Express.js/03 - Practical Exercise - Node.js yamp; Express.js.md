# Practical Exercise - Node.js &amp; Express.js

### **Step 1: Install Node.js (If not yet)**

**1.1. Visit the Node.js Official Website**

- Go to the official Node.js website: <https://nodejs.org/>.

**1.2. Download Node.js**

- On the homepage, you’ll see two main download options:
  - **LTS (Long Term Support)**: This version is recommended for most users as it has a stable set of features.
  - **Current**: This version includes the latest features, but it may be less stable.
- Choose the appropriate version for your operating system (Windows, macOS, or Linux).

**1.3. Install Node.js**

- Run the installer and follow the on-screen instructions.
  - On **Windows/macOS**, this process is straightforward—just click “Next” and accept the terms to install Node.js and npm (Node Package Manager).
  - On **Linux**, you can install Node.js via package managers like `apt` for Ubuntu: `sudo apt update sudo apt install nodejs sudo apt install npm`

---

### **Step 2: Verify Installation**

**2.1. Open the Terminal or Command Prompt**

- After installation, open your terminal (on macOS/Linux) or Command Prompt/PowerShell (on Windows).

**2.2. Check Node.js Version**

- In the terminal, type the following command to check the version of Node.js: `node -v` Example Output: `v16.13.0`

**2.3. Check npm Version**

- Similarly, check the version of npm (Node Package Manager): `npm -v` Example Output: `8.1.0`

If both versions are displayed correctly, Node.js and npm are installed successfully.

---

### **Step 3: Create a New Node.js Project**

**3.1. Create a Project Folder**

- Open the terminal and navigate to the location where you want to create your new project. For example, create a folder on your desktop: `mkdir my-node-project cd my-node-project`

**3.2. Initialize a New Node.js Project**

- In the project folder, run the following command to initialize the project: `npm init` This command will prompt you with several questions about your project, such as:
  - **name**: The name of your project (e.g., `my-node-project`).
  - **version**: The starting version of your project (e.g., `1.0.0`).
  - **description**: A short description of your project.
  - **entry point**: The main file of your project (default is `index.js`).
  - **test command**: You can leave this blank for now.
  - **git repository**: Optional, leave it blank for now.
  - **keywords**: Optional, but you can list keywords to help identify your project.
  - **author**: Your name or the author of the project.
  - **license**: The license for your project (e.g., `MIT`).
- Once all questions are answered, it generates a `package.json` file with metadata about the project.

**Example of `package.json` file**:

code

```
{
  "name": "my-node-project",
  "version": "1.0.0",
  "description": "A basic Node.js project",
  "main": "index.js",
  "scripts": {
    "test": "echo \\\\"Error: no test specified\\\\" && exit 1"
  },
  "author": "Your Name",
  "license": "MIT"
}
```

---

### **Step 4: Install Packages (Dependencies)**

**4.1. Install Express.js (Example of Adding a Package)**

- If you are building a web application, you might want to install **Express.js**, a popular web framework for Node.js. `npm install express`
- After running this command, a `node_modules` folder will be created in your project directory. This folder holds all the libraries (e.g., Express) that you install using npm.
- The `package.json` file will also be updated with the Express dependency, like so: `"dependencies": { "express": "^4.17.1" }`

---

### **Step 5: Run Your Application**

**5.1. Create a Basic App (app.js)**

- Create a file named `app.js` in the project directory: `touch app.js`
- Open `app.js` and add the following code to create a basic web server using Express: `` const express = require('express'); const app = express(); app.get('/', (req, res) => { res.send('Hello, world!'); }); const PORT = 3000; app.listen(PORT, () => { console.log(`Server is running on <http://localhost>:${PORT}`); }); ``

**5.2. Start the Server**

- In the terminal, run your application by executing: `node app.js`
- You should see the output: `Server is running on <http://localhost:3000>`
- Open a browser and navigate to `http://localhost:3000`. You should see the message "Hello, world!" displayed.

---

### **Step 6: Understand Asynchronous Programming in Node.js**

**6.1. Example of Asynchronous Code (Using Callbacks)**

- Node.js is asynchronous by default. Here's an example using the built-in `fs` module to read a file asynchronously: `const fs = require('fs'); fs.readFile('file.txt', 'utf8', (err, data) => { if (err) { console.log('Error:', err); } else { console.log('File contents:', data); } }); console.log('Reading file...');` The message "Reading file..." will be printed first, and the file contents will be printed after the file is read.

**6.2. Using Promises with Asynchronous Code**

- Node.js supports promises for better handling of asynchronous code: `const fs = require('fs').promises; async function readFile() { try { const data = await fs.readFile('file.txt', 'utf8'); console.log('File contents:', data); } catch (err) { console.log('Error:', err); } } readFile();`

---

### **Step 7: Using Built-in Modules**

- Node.js comes with several built-in modules, such as `http`, `fs`, and `path`, to handle various tasks without installing external libraries.

**7.1. Example: Using the `http` Module**

- You can use the `http` module to create a simple HTTP server: `const http = require('http'); const server = http.createServer((req, res) => { res.writeHead(200, {'Content-Type': 'text/plain'}); res.end('Hello, Node.js!'); }); server.listen(3000, () => { console.log('Server running at <http://localhost:3000>'); });`

---

### **Step 8: Debugging Your Application**

**8.1. Use `console.log()` for Basic Debugging**

- Use `console.log()` to print variables and check values in your application.

**8.2. Use Node.js Inspector for Interactive Debugging**

- Run your app with the inspector: `node --inspect app.js`
- Then open `chrome://inspect` in Google Chrome to interactively debug the application.
