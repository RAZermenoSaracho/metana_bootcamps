# Webserver Software and Reverse Proxies

[YouTube video player](https://www.youtube.com/watch?v=9J1nJOivdyw)

### Introduction to Webserver Software

Webserver software serves web-based applications and HTML to end-users from a server, handling various tasks like SSL certificate management and traffic routing.

- **Key Questions**
  - How do we serve our web application to the users when we’ve deployed it to a VPS ?
  - Do we serve it directly from the Node process directly to the user ?
  - What happens if the process crashes? How would it restart ?
  - What happens if there are multiple web apps on a single server ? How does the server know where to direct the traffic to ?
  - How does our web app know where its SSL certs are ?
- **Solution**: These questions are addressed by webserver software.

### Understanding Webserver Software

- Webserver software serves web-based applications and HTML to end-users from a server.
- It can serve raw HTML files from a directory, or serve complex web applications running in their own process.
- It can also handle things like SSL certificates, and filtering or redirecting traffic based on certain rules.
- **Common Examples**
  - Apache2 — the most common webserver software in the world.
    - <https://en.wikipedia.org/wiki/Apache_HTTP_Server>
  - Nginx - a lightweight alternative to Apache, very popular for small web applications, but equally powerful
    - <https://www.nginx.com/resources/glossary/nginx/>[What Is NGINX? - NGINX](https://www.nginx.com/resources/glossary/nginx/)

### Key Functions

- Each of these has multiple functions, including:
  - Reverse Proxy
  - Load Balancer
  - Web Server
  - Caching
  - Media Streaming
  - Managing SSL Certificates
- We won’t go into detail on all, but we will focus on two of these capabilities: **Reverse Proxy** and **managing SSL certificates** — which we will use in our assignment later for deploying an app to a VPS.

### Reverse Proxy Functionality

- Webserver software can be configured to direct traffic to different **web applications** based on what domain name the request is for.
- This allows us to have multiple web applications running on a single host, and listening on the same port. This is called a **reverse proxy**.
- For example:
  - We have **web application A** running in our VPS on port **5000**
  - Another **web application B** is running in our VPS on port **5001**
  - The domain for application A is “[example-app.com](http://example-app.com)”
  - The domain for application B “[a-different-app.com](http://a-different-app.com)”
  - We configure out web server software:
    - direct all requests for “[example-app.com](http://example-app.com)” to the process on port 5000
    - direct all requests for “[a-different-app.com](http://a-different-app.com)” to the process on port 5001
  - So, visitors for each site are directed to the correct application, based on the domain name

### Introduction to Reverse Proxy

[YouTube video player](https://www.youtube.com/watch?v=-QcQd3Bkc9o)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=9J1nJOivdyw)
- [YouTube video player](https://www.youtube.com/watch?v=-QcQd3Bkc9o)
