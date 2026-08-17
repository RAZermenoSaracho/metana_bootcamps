# Introduction to Deploying and Cloud Platforms

***We’re finally in the home stretch! Almost there ?***

### **Key goal for this module is “deployment”**

- Transitioning an application from code-space to being accessible by users worldwide.
- Deployment can be executed through various methodologies and utilizing diverse architectures and tools.
- Commonly, deployment involves utilizing cloud hosting services due to their flexibility and scalability.

### DevOps

- Combining development (dev) and operations (ops) functions into a unified approach.
- This is the role you’ll be taking when deploying your own applications, or determining how to best deploy a web application as part of an engineering team.
- DevOps is about keeping your deployment processes as orderly, repeatable, and maintainable as possible, using the same principles as with good coding practices.
- This unit is all about DevOps! It’s one of the many hats you’ll need to wear as a full-stack engineer.

### **Deployment Environments**

- Various stages in the development and deployment process.
  - **Development Environment**
    - Where initial coding and testing occur.
    - Often used by individual developers or small teams.
  - **Staging Environment**
    - Mimics the production environment closely.
    - Used for final testing before deployment to production.
  - **Testing Environment**
    - Dedicated space for testing new features and changes.
    - Ensures the stability and functionality of the application.
  - **Production Environment**
    - Live environment where the application is accessible to users.
    - Requires high reliability, security, and performance.
- In this section we will discuss how to divide up your development.

### **Cloud Models**

- Different ways to handle and manage your online infrastructure.
  - **VPS Hosting (Third-party Host)**
    - Users rent virtual servers from third-party providers.
    - Provider manages server hardware, networking, and maintenance.
  - **Serverless or PaaS (Platform as a Service)**
    - Platform manages infrastructure, allowing users to focus solely on application development.
    - Offers scalability and maintenance without user intervention.
  - **Self-hosted VPS**
    - Users manage their own virtual servers.
    - Provides more control but requires technical expertise for setup and maintenance.
  - **On-premises Servers**
    - Infrastructure managed within the organization's premises.
    - Offers complete control but requires significant investment in hardware and maintenance.
- Understanding these models aids in selecting the most appropriate deployment approach based on factors like control, scalability, and management preferences.

### **Hosting Providers**

- Hosting providers provide the “where” in where we deploy our web applications, and other infrastructure services to support it.
- Cloud Hosting Providers offer a variety of services including,
  - Private clouds
  - VPS hosting
  - Database as a service
  - DNS management & automatic SSL
  - Serverless application platforms
  - Automated testing, monitoring, and CI/CD tools
- Discussion will focus on determining the best fit for your application needs and exploring common hosting services available for selection.

### **Securing & Configuring Your Application**

- In this topic we will discuss below,
  - **Domain Name Registration**
    - Obtaining and managing website addresses.
  - **Securing Deployment Secrets**
    - Safeguarding sensitive information like passwords and API keys during deployment.
  - **Build Pipelines and CI/CD**
    - Establishing automated workflows for building, testing, and deploying code changes.
  - **Connecting Securely to Database Backends**
    - Ensuring encrypted and authenticated connections to database servers for data security.

### **Advanced Topics**

- Discussion at the end will cover,
  - **Static Assets & Object Storage**
    - Managing and serving static files efficiently.
  - **SSL Certificates**
    - Implementing secure communication protocols for data encryption.
  - **Container-Based Deployment**
    - Deploying applications using containerization for scalability and portability.
  - **CDNs and Static Site Deployment**
    - Utilizing Content Delivery Networks for optimized content delivery and hosting static sites.
  - **Reverse Proxies & Webserver Software**
    - Configuring reverse proxies and web server software for efficient request handling and routing.
