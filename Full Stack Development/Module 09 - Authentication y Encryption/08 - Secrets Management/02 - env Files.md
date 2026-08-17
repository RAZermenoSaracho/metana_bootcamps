# env Files

### **What is an Env File ?**

- An env file, short for environment file, is a text file containing key-value pairs of configuration data used by applications.
- It typically stores sensitive information like API keys, database credentials, and other environment-specific settings.

**Is it different from Environment Variables ?**

- Yes, env files are different from environment variables.
- Environment variables exist in the operating system's memory or the process running the application.
- Env files are loaded by the operating system or the application itself and are often used to set environment variables.

**How are they “loaded” ?**

- Applications usually read env files automatically, especially if named ".env" and placed in the top-level directory.
- In Node.js applications, the `dotenv` library is commonly used to read env files explicitly.
- Shell scripts can use the `source` command to load env files into memory.

**Why “.env” naming convention ?**

- The ".env" naming convention implies that the file contains secret information and should be hidden on the filesystem.

**Where should they be stored ?**

- Env files should be stored securely, preferably outside of version control systems, to prevent accidental exposure of sensitive data.

**Can you have multiple env files ?**

- Multiple env files can be used for different environments or configurations, such as development, testing, and production.

**Where does the data from “env” files end up ?**

- Data from env files is loaded into OS environment variables, making it accessible to the application during runtime.

### **Best Practices for Env Files**

- Avoid including env files in version-controlled repositories to prevent accidental exposure of sensitive information.
- Provide an "example.env" file with placeholder data and comments to explain the purpose of each key.
- Use descriptive key names and include comments to enhance readability and maintainability.

Env files play a crucial role in managing application configurations and secrets securely, ensuring that sensitive information remains protected and accessible only to authorized entities.

[YouTube video player](https://www.youtube.com/watch?v=txGL-Ld9zD8)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=txGL-Ld9zD8)
