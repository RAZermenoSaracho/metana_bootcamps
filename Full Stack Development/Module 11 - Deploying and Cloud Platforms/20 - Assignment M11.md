# Assignment M11

In this assignment, you’ll deploy your portfolio project to a real-world cloud environment, using AWS. The goal is to provide hands-on experience with setting up and configuring an EC2 instance, installing necessary software, and getting your full-stack application live on the web.

By completing this assignment, you’ll have a deployed version of your portfolio or any other full-stack application that can be accessed via the internet.

## Assignment Objectives

**By the end of this assignment, you will know to:**

- **Set Up and Configure an EC2 Instance**: Launch an EC2 instance on AWS, configure security settings, and access it via SSH.
- **Install Necessary Software**: Install and configure Node.js, Git, and other necessary software on the EC2 instance.
- **Deploy Your Application**: Clone your GitHub repository, build your application, and run it on the server.
- **Set Up Reverse Proxy and PM2**: Configure Nginx as a reverse proxy to serve your application, and use PM2 to keep the application running in the background.
- **Configure Domain Name and SSL**: Link your application to a custom domain and secure it with an SSL certificate using LetsEncrypt.

## Requirements

**Setting Up Your EC2 Instance**:

- Create an AWS account if you don’t have one already.
- Launch an EC2 instance (choose an Ubuntu AMI for simplicity).
- Create a new security group with HTTP (port 80) and HTTPS (port 443) open to the world.
- Generate a PEM key for SSH access to your EC2 instance.
- SSH into your EC2 instance.

**Provision the Server**:

- Create a non-root user for security.
- Update system packages and install required software.
- Ensure that your user has administrative privileges.

**Install Node.js and Git**:

- Install Node.js using Node Version Manager (NVM).
- Install Git and configure it on the server.
- Clone your application repository from GitHub using SSH deploy keys or HTTPS.

**Build and Run Your Project**:

- Install project dependencies (e.g., `npm install`).
- Set up environment variables for production.
- Build the application and verify it runs properly on the server.

**Set Up Reverse Proxy with Nginx**:

- Install Nginx on your EC2 instance.
- Configure Nginx to act as a reverse proxy for your Node.js application.
- Update firewall settings if necessary to allow Nginx to serve your app.

**Set Up PM2**:

- Install PM2 to manage your Node.js app in the background.
- Configure PM2 to start your app on boot and ensure it keeps running after logging out of the SSH session.

**Configure Domain Name (Optional)**:

- Use AWS Route 53 or another domain registrar to link your application to a custom domain.
- Configure DNS settings to point to your EC2 instance.

**Set Up SSL with LetsEncrypt**:

- Use LetsEncrypt to obtain a free SSL certificate.
- Configure Nginx to serve your app over HTTPS.

**Improve Security**:

- Close unnecessary ports on the EC2 security group (e.g., SSH should only be accessible from trusted IPs).
- Disable password-based authentication for SSH and use key-based authentication.
- Harden SSH by adjusting the configuration for increased security.

## Deliverables

**Deployed Application**:

- A live version of your full-stack application accessible via a custom domain or AWS public IP and SSL-secured (HTTPS) access to the application.

**Source Code**:

- GitHub repository with full-stack code (backend, frontend, and deployment configurations).
- Include necessary config files (e.g., `.env`), but **do not include sensitive data**.

**Deployment Documentation**:

- A README or document outlining deployment steps, configuration changes, and troubleshooting tips.

**Post-Deployment Testing**:

- Link to the live application.
- Test across multiple devices and browsers for compatibility.
- Provide screenshots or video demonstrating both HTTP and HTTPS access.

## Submission Instructions

- Push the completed React project to the `Metana-fullstack-bootcamp` GitHub repository.
- Include a detailed `README.md` describing your detailed assignment structure of module 11 and deployment.

## Tips for Success

- **Secure SSH Access**: Use key-based authentication and restrict access to specific IPs for added security.
- **Use PM2**: Configure PM2 to keep your app running after logout and auto-start on system reboots.
- **Nginx Reverse Proxy**: Ensure correct proxy settings to route traffic from Nginx to your Node.js app.
- **Monitor Logs**: Regularly check app logs using AWS CloudWatch to track errors.
- **SSL Renewal**: Automate Let’s Encrypt certificate renewal with cron jobs (every 90 days).
- **Test on Real Devices**: Verify cross-device compatibility and responsiveness on desktop and mobile.
- **Troubleshoot Gradually**: Check EC2 security, Nginx logs, and PM2 status for issues step-by-step.
