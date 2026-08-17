# Understanding Key Terms in Hosting and Deployment

### Physical Servers vs VPS

- **Physical Servers**
  - Dedicated servers used for hosting applications.
  - Offer full control and customization, utilizing the native operating system.
  - Can be owned or rented from a hosting provider at a higher cost.
- **Virtual Private Servers (VPS)**
  - Virtualized instances hosted on a physical server.
  - Provide scalability and resource isolation at a lower cost compared to physical servers.
  - Users can choose their preferred operating system, such as
    - Ubuntu Linux
    - Red Hat Fedora
    - Windows Server
    - Unix/Linux distributions like FreeBSD, CentOS, and Debian
  - VPS instances can be duplicated and backed up to disk images, facilitating quick cloning of entire virtual servers.

### PaaS vs IaaS

- **Platform as a Service (PaaS)**
  - Provides a platform for developing, running, and managing applications without dealing with infrastructure management.
  - Typically offers "One-click deploy" solutions, where users link their codebase to the service, enter configuration settings, and deploy the app with a dedicated URL.
  - Example PaaS services:
    - Heroku
    - Vercel
    - Render
    - Google App Engine
    - Microsoft Azure App Service
    - DigitalOcean App platform
- **Infrastructure as a Service (IaaS)**
  - Offers virtualized computing resources over the internet, including servers, storage, and networking.
  - Users have control over what packages and software they install, and all system administration is their responsibility.
  - Provides more control and flexibility but requires sysadmin knowledge.
  - Example IaaS providers:
    - Amazon Web Services (AWS) EC2
    - Microsoft Azure Virtual Machines
    - Google Compute Engine
    - DigitalOcean Droplets

### 3rd Party Hosting vs. On-Premises / Self-Hosted

- **Self-hosted / On-premises**
  - You or your organization own the server, which physically resides at a location you control.
  - Pros
    - You have full control over the server and its configuration.
    - Costs are limited to power consumption and internet bandwidth.
  - Cons
    - Requires you to maintain the server, including hardware upgrades, software updates, and security patches.
    - Internet bandwidth may be insufficient for high-traffic projects, especially if hosted from a personal location.
- **Third-party hosting**
  - Hosting company owns the server, and you do not own the physical location where the server resides.
  - This approach offers convenience and scalability, as the hosting provider manages maintenance and infrastructure.
  - You pay a subscription fee or usage-based pricing for the hosting service.

### Private vs Public Cloud

Public cloud and private cloud are two distinct models for hosting web applications.

- **Private Cloud**
  - A [private cloud](https://www.cloudflare.com/learning/cloud/what-is-a-private-cloud/) is a cloud service that is not shared with any other organization. The private cloud user has exclusive access to the cloud network and its resources.
  - Advantages
    - **More flexibility**: Organizations can tailor the cloud environment to meet specific business needs.
    - **More control**: Resources are not shared with others, allowing for higher levels of control and privacy.
    - **More scalability**: Private clouds often offer superior scalability compared to on-premises infrastructure.
  - Use Cases
    - Suitable for applications with strict privacy and security compliance regulations.
  - Security Considerations
    - Private cloud applications operate within a private network, enhancing security. However, proper security practices should still be employed to mitigate risks.
- **Public Cloud**
  - A [public cloud](https://www.techtarget.com/searchcloudcomputing/definition/public-cloud) is a cloud service that shares computing resources among different customers, although each customer's data and applications remain isolated.
  - Advantages
    - **Lower costs**: Eliminates the need to purchase hardware or software, with pay-as-you-go pricing models.
    - **No maintenance**: Service providers handle maintenance and infrastructure management.
    - **Near-unlimited scalability**: On-demand resources ensure scalability to meet business needs.
    - **High reliability**: Utilizes a vast network of servers to prevent failures.
  - Use Cases
    - Ideal for businesses seeking cost-effective, scalable solutions without the burden of infrastructure management.
  - Security Considerations
    - Public cloud services are exposed to the entire internet, emphasizing the importance of robust security measures to protect against threats, including data breaches and unauthorized access.

### Serverless Platforms vs Serverless Functions

- **Serverless applications** can refer to PaaS models — where the developer deploys a site or web application directly to a platform, without ever interacting directly with a server.
- **Serverless functions** are one-off functions that fire in response to events. Similar to PaaS model, the developer uploads code for the function which will be run, but it differs in that it’s not a long-term running process.
