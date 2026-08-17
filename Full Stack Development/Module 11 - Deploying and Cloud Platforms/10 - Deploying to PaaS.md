# Deploying to PaaS

Deploying to a PaaS provider such as Heroku or Vercel is your first choice, for most small web applications. Using a PaaS platform can avoid the hassles of configuration and server management, and help you get from code to production faster.

![](https://resources.metana.co/public/35/c0/35c061ca6c8356532ca3706f0ca6e28c331c30d908f6b961df0b776ab80d45a6.png)

Examples

- **Heroku**: Allows you to manage environment variables directly through its dashboard or command-line interface.
- **Amazon Web Services (AWS) Elastic Beanstalk**: You can configure environment variables through the AWS Management Console or command-line interface.
- **Google Cloud Platform (GCP) App Engine**: Environment variables can be defined in the `app.yaml` configuration file or through the GCP Console.
- **Microsoft Azure App Service**: Application settings (similar to environment variables) can be configured in the Azure portal or using Azure CLI.
- **DigitalOcean App Platform**: You can define environment variables through the App Platform dashboard or using the DigitalOcean API.

**Deployment Process for PaaS**

1. **Create a Project →** Begin by creating a new project within your PaaS provider's control panel.
2. **Connect to Code Repository →** Link your project to a code repository, such as GitHub, where your application code is hosted.
3. **Configure Environment Variables →** Set up environment variables or secrets necessary for your application. This may involve uploading an Env file, manually entering key-value pairs, or copying and pasting environment values.
4. **Specify Build and Run Commands →** Define the build command that the platform should execute to build your application, if applicable. Specify the command needed to start your application once it's deployed.
5. **Deploy Your Application →** Initiate the deployment process, typically achieved with a one-click deployment option provided by the PaaS platform.

### Deployments and Rollbacks

- **Deployments**
  - A deployment refers to each successful release of your application.
  - If any errors occur or the build process encounters issues, the deployment fails, and the changes will not be released.
- **Rollbacks**
  - In the event of a deployment failure, the platform typically refrains from releasing the new deployment, maintaining the previous version of your application.
  - However, if a successful deployment contains bugs or other issues necessitating a return to a previous release, most platforms offer a rollback feature.
  - This functionality enables you to revert your application to a prior release, effectively resetting it to a stable state.

### Infrastructure Considerations

- **One Project Limitation**
  - Serverless/PaaS platforms typically restrict each project to host only one service.
  - If you require multiple services, you'll need to deploy them in separate projects.
- **Monolithic vs Microservices**
  - Preferably, your project should adopt a monolithic architecture, where it operates as a unified single application.
  - In cases where your application involves separate frontend/backend components or utilizes external services like databases, deploying them together may not be feasible.
  - Microservices architecture or utilizing third-party hosted services like databases can address this limitation.
- **Security Considerations**
  - For applications employing a non-monolithic approach, ensure all connections to the backend are secured using HTTPS.
  - Implement token-based route protection to enhance the security of your application.

[YouTube video player](https://www.youtube.com/watch?v=QAbqJzd0PEE)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=QAbqJzd0PEE)
