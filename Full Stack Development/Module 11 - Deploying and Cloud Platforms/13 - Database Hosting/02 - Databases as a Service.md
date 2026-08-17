# Databases as a Service

In the past, databases required self-installation and self-management. While self-hosting your database can offer cost savings over using a hosted database, it demands additional sysadmin knowledge.

Nowadays, there are numerous hosted database services, also known as Database as a Service (DBaaS).

![](https://resources.metana.co/public/d3/d8/d3d81a557bc85615bb7c5c46ecb00afc711a59650586cff09ceed3bf57413e03.png)

### **Cloud database services**

- Some Infrastructure as a Service (IaaS) platforms provide built-in cloud database services.
  - If you're deploying on an IaaS or PaaS, this is the simplest way to set up your database.
  - However, these services may have associated costs; review the documentation for pricing details.
  - Look for free tiers, particularly for small projects, offered by your cloud host or third-party hosts, which provide limited but ample usage.
- External or third-party cloud database services are also available Examples:
  - [Firebase](https://firebase.google.com/docs)
  - [Supabase](https://supabase.com/docs)
  - [Aiven](https://aiven.io/free-postgresql-database)
  - [Heroku Postgres](https://www.heroku.com/postgres)
  - AWS RDS

### **IP whitelisting**

- After setting up your database, it's essential to whitelist the URL from your server application.
- This measure prevents unauthorized users from accessing your database, thereby protecting your resources and finances.

### **Configure your app**

- Your application must be configured to recognize your database URL, database name, and password, collectively known as the "Database URI string."
- Ensure your applications connect to the appropriate database, distinguishing between staging and production environments.
