# Introduction to SSL

### **What is SSL?**

- SSL (Secure Sockets Layer) is a protocol designed to ensure the security of a connection to a web host.
- Although "SSL" is the older version, it's commonly used to refer to both SSL and its successor, TLS (Transport Layer Security).
- HTTPS is a secure implementation of HTTP connections, utilizing SSL or TLS.

### **Importance of SSL and HTTPS**

- SSL enables verification of the server's identity, ensuring that the connection is secure and trustworthy.
- HTTPS, which uses SSL/TLS, encrypts the connection between the client and server, protecting sensitive data from third-party interception.

### **Browser Verification of SSL**

- Browsers check for SSL certificates when accessing websites via HTTPS.
- Certificates are verified against records held by Certificate Authorities (CAs).
- CAs sign certificates, validating their authenticity.
- If the certificate is valid and trusted, the browser initiates a secure connection process known as a Handshake before transmitting data securely.

### **Important Terms**

- SSL vs. TLS vs. HTTPS → SSL and TLS are cryptographic protocols, with HTTPS being a secure version of HTTP.
- Certificates → Digital documents that verify the identity of a website.
- Certificate Authority (CA) → Trusted entities that issue and verify SSL/TLS certificates.
- Signing Request → A request for a certificate signed by a CA.
- "Well-known" Locations → Standardized directories where certificates and other security-related information can be found.
- ACME Protocol → Automatic Certificate Management Environment protocol automates interactions between certificate authorities and servers for the deployment of public key infrastructure.

[YouTube video player](https://www.youtube.com/watch?v=67Kfsmy_frM)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=67Kfsmy_frM)
