# Example case 2: Deploying to VPS (AWS)

### Complete Walkthrough: Deployment to a VPS using AWS

*Important Notes:*

- **What is EC2 ?**
  - This deployment involves setting up a Virtual Private Server (VPS) on Amazon's service called EC2. It's Amazon's virtual private cloud server service.
- **AWS Users & Groups**
  - This process includes setting up AWS users and security groups to control access to the VPS from within the AWS control panel.
  - Access keys, similar to SSH keys, are set up to connect to the application via the terminal.
- **Reverse Proxy**
  - A reverse proxy called Nginx is used in this infrastructure.
  - The reverse proxy directs incoming traffic on port 80 to our application running on port 5000.
  - Configuration settings for the reverse proxy include SSL certificate settings, enabling access to the application over HTTPS.
- **What is PM2 ?**
  - This tutorial utilizes the `pm2` node package.
  - PM2 serves as a process manager, ensuring the application runs in a fail-proof manner in production.
  - Unlike running the app with "npm start," which won't automatically restart if the process crashes, using a process manager like PM2 ensures resilience against crashes.

### Tutorial video:

[YouTube video player](https://www.youtube.com/watch?v=nQdyiK7-VlQ)

### Additional content

- Deploying React Express app with Nginx and PM2 on AWS
  - <https://dev.to/rmiyazaki6499/deploying-a-production-ready-react-express-app-on-aws-62m>
  - Comments: This guide is well organized, but includes some additional setup for CI/CD — you can skip the Continuous Deployment section
- Deploying server to EC2
  - <https://aws.plainenglish.io/deploy-your-server-to-aws-ec2-66f35fd0fca2>
  - Comments: This guide provides more detailed instructions on selecting and setting up the actual EC2 instance

## Links

- [YouTube video player](https://www.youtube.com/watch?v=nQdyiK7-VlQ)
