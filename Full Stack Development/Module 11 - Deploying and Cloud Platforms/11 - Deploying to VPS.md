# Deploying to VPS

VPS deployment stands as the secondary choice for most web applications. It necessitates some system administration proficiency, commonly on a Linux server.

Reasons for opting VPS deployment

- Cost-saving potential for hosting multiple sites on a single server.
- Reduced expenses for hosted databases and other services by running them locally in the same VPS.
- Capability to work with a filesystem, unlike serverless/PaaS hosting which usually lacks this feature.

![](https://resources.metana.co/public/b4/c5/b4c5f9e64ede7ae83cd99961640a6a32985f975906191da61afdc18bf5446c2e.png)

### Considerations for Deploying to a VPS

1. Firewall → You need to allow traffic to your web application, and shut down access to any non-public services.
2. Database
   - If you intend to run a database locally on the same server, you must install it there.
   - If you intend to run the database on a cloud host, you must set it up elsewhere and configure your app to point to it.
3. SSH access → You will normally access your VPS server through SSH. This should be configured securely using SSH keys, and not password-based access.
4. Storage space and RAM → Ensure your server instance has adequate storage space and RAM for your application needs. For a typical small Node application, this should be pretty minimal.
5. Port forwarding and Proxy
   - If your application is running on a non-standard port (for example, port 8000 or 8080), you will need to forward traffic from the inbound port (like 443) to your application port. (eg: 8000)
   - You can do this directly using **firewall rules** — but, if you have multiple websites or web applications running on a single server, you will need to direct the traffic to the correct app, based on the **domain name** of the request.
   - This is best handled through a specialized software called a **reverse proxy**. We will discuss this later.

### Security considerations

1. SSH security
   - Hackers can **brute-force** attack your SSH passwords, and they will guess them.
   - Always use keys for SSH access, not passwords.
2. Disable root SSH login → always **disable root SSH login** on your server’s SSH config.
3. Never log in as root user.
   - Create a new user with sudo permissions.
   - Log in as your new user over SSH, and use `sudo su` if you need to do anything as admin.
4. Firewall
   - **Open ports are a security hazard!**
   - **Disable all ports** on your webserver except for web traffic and SSH access. These will normally be ports 80 (for http), 443 (for https), and 22 (for SSH).
5. Database
   - If you intend to run the database externally on a **cloud DB service**, it’s important that the DB service is **whitelisted** to only accept connections from your application’s IP.
   - Additionally, it’s best to have database connections running over **HTTPS** — not plain HTTP, which could be intercepted by a third party.

### Port Forwarding and Firewall

- By default, most cloud VPS operating systems will include a **firewall**.
- Firewalls control whether traffic on a given port number can reach our server — for example, port 80 for HTTP traffic.
- Common ports for web applications
  - 22 — SSH — shell access, so we can manage our VPS instance
  - 80 — HTTP — non-secure, without SSL
  - 443 — HTTPS — for HTTP with SSL
- Any ports that you don’t specifically need to allow traffic through should be **closed**.
- In our case, we’ll need to allow the above three ports, to access our web application.
- This firewall does not allow traffic from anywhere to reach our server, by default — we need to enable access.
- Enabling ports is done either through the cloud platform’s control panel, or directly using the command-line in the VPS.
