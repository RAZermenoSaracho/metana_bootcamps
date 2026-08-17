# Weekly Challenges 11 : Deploy and Conquer

In this set of challenges, you will explore cloud platforms, deploy web applications, and apply DevOps principles to solidify your understanding of modern deployment techniques. We recommend you attempt **at least one challenge** to gain hands-on experience in deploying and managing web applications!

---

### **Challenge 1: “Hello World Cloud Deployer”**

**Description:**

Create a simple web application (e.g., a basic “Hello World” app) and deploy it to a Platform-as-a-Service (PaaS) platform. Platforms like **Vercel** or **Render** offer free tiers to get started quickly.

Ensure your app runs on the cloud by configuring environment variables (e.g., for displaying a custom greeting). Share the live URL once deployed.

- **Extensions:** Add a form to capture user input (e.g., a “name” input that changes the greeting) and deploy the updated app.
- **Skills Covered:** PaaS deployment, configuring environment variables, basic app deployment.

**Free Hosting Recommendations:**

- **Vercel:** Great for static sites or front-end apps. Free tier with generous usage limits.
- **Render:** A free hosting option for static and dynamic web apps, with the ability to run background jobs and databases.
- **Netlify:** Perfect for static sites or serverless functions with an easy-to-use interface.

---

### **Challenge 2: “Dockerize and Deploy”**

**Description:**

Create a simple web application (e.g., a Node.js app) and use **Docker** to containerize it. Once containerized, deploy it to a VPS platform like **AWS**, **DigitalOcean**, or **Linode**. Note that **DigitalOcean** and **Linode** offer affordable options for small applications, and both offer free credits to help you get started.

Ensure the container runs correctly and configure any necessary settings for the environment.

- **Extensions:** Add a database container (e.g., a simple MongoDB or PostgreSQL instance) to create a multi-container setup.
- **Skills Covered:** Containerization with Docker, deploying to a VPS, managing containerized apps.

**Free Hosting Recommendations:**

- **DigitalOcean:** Offers $100 in credits for new users, and their smallest droplets are very affordable.
- **Linode:** Also provides competitive pricing with a $100 credit for new accounts.
- **Oracle Cloud:** Has a free tier with a couple of always-free instances for small workloads.
- **Scaleway:** Offers free credits and low-cost instances for containerized applications.

---

### **Challenge 3: “SSL Secure Your Site”**

**Description:**

Deploy a simple web application and configure it to use HTTPS by obtaining and implementing an **SSL certificate** using **Certbot** and **LetsEncrypt**. This will ensure that your app is secure and accessible via HTTPS.

Demonstrate that your app is secure by visiting it over HTTPS and ensuring there are no security warnings in the browser.

- **Extensions:** Set up a custom domain for your deployed app and ensure it uses SSL.
- **Skills Covered:** SSL configuration, deploying applications securely, using Certbot and LetsEncrypt.

**Free Hosting Recommendations:**

- **Cloudflare**: A free service that offers SSL and can be used with custom domains, providing extra security and caching features.
- **Vercel & Netlify**: Both provide SSL for custom domains out of the box, even on their free tiers.
