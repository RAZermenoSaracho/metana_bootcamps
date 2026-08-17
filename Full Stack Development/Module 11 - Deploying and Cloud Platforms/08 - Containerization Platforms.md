# Containerization Platforms

### **What is containerization ?**

- It is a method of packaging and deploying applications along with their dependencies into lightweight containers, which enhances portability and scalability.
- Containers encapsulate an isolated environment consisting of a virtual operating system, file system, and processes, ensuring that they do not interfere with the host system. (Note: technically not true, but they behave as if they were separate)
- Common containerization systems:
  - [Docker](https://www.docker.com)
  - [Kubernetes](https://kubernetes.io)
  - [Podman](https://podman.io)

[YouTube video player](https://www.youtube.com/watch?v=0qotVMX-J5s)

### Why use containerization systems ?

1. Consistency
   - Applications need a predictable, consistent environment and operating system to run on. We also need to install things like software dependencies, and do other configuration tasks, or build required software.
   - When the environment changes from server to server, or from one developer’s machine to another, it creates difficulty setting up and configuring the application environment, and can result in the app not running the same way.
   - Containers make it easy to deploy and run an application consistently across different environments without worrying about compatibility issues.
2. Security
   - Containers isolate the application from the host system, which adds an extra layer of security, if someone were able to compromise the application.
3. Portability
   - Containers can be moved easily between different machines, and deployed to different servers and operating systems and cloud environment

### **Advantages for local development**

- Container systems can significantly improve your local development workflows by isolating applications.
- When developing multiple applications, each may require different services such as databases or task queues. Installing these directly on your development machine can lead to conflicts in software versions, port numbers, or locations, resulting in system clutter.
- Containers enable you to manage these diverse services cleanly, facilitating easy switching between different services as you transition from one application to another.
- Additionally, using containers helps maintain a clean system, as you can easily clean up and delete containers once they are no longer needed.

### **What is Kubernetes ?**

- Kubernetes, often referred to as k8s or kube, is an open-source container orchestration platform.
- It facilitates scheduling and automating the deployment, management, and scaling of containerized applications.
- Kubernetes is commonly used for orchestrating complex containerized environments in production settings.
- While powerful, Kubernetes is a highly complex system and may not be necessary for most single-developer projects.
- However, gaining familiarity with Kubernetes can be valuable once you have mastered the fundamentals of Docker and other containerization systems.
- For more information, visit [IBM's Kubernetes topic page](https://www.ibm.com/topics/kubernetes).

**Do you need containers for your application ?**

- Probably not — but see the considerations above for local development.

**Do you need Kubernetes for your application ?**

- Almost definitely not ? — but have fun if you want to try it out.

**How do you deploy applications using containers ?**

- Deployment using containers is beyond the scope of this course, but some cloud platforms will allow you to run applications using containers.
- Common platforms that allow containerized deployment
  - Google Cloud - <https://cloud.google.com/containers/>
  - DigitalOcean App Platform - <https://www.digitalocean.com/products/app-platform>
  - Microsoft Azure
    - Azure Containers - <https://azure.microsoft.com/en-us/products/container-apps/>
    - Azure Redhat OpenShift - <https://azure.microsoft.com/en-us/products/openshift/>
    - Azure Kubernetes Service - <https://azure.microsoft.com/en-us/products/kubernetes-service/>
  - AWS
    - Amazon AppRunner - <https://aws.amazon.com/apprunner/>
    - Amazon Amazon Elastic Container Service - <https://aws.amazon.com/ecs/>
    - AWS Fargate - <https://aws.amazon.com/fargate/>
- Example of Dockerizing a React application
  - How to Dockerize a React Application In 5 Minutes
    - <https://behdadk.medium.com/how-to-dockerize-a-react-application-in-5-minutes-c6093636628f>

## Links

- [YouTube video player](https://www.youtube.com/watch?v=0qotVMX-J5s)
