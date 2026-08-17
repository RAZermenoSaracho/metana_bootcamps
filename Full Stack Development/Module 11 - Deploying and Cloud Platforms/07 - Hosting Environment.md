# Hosting Environment

Hosting environment is the servers and infrastructure where our apps “live” on the web. Can be internal (locally hosted on company infrastructure) or external (hosted on 3rd party servers). May include our staging environment and/or testing environments, as well as production.

### Typically this will be a cloud hosting platform.

- Common platforms include:
  - [AWS](https://aws.amazon.com/)
  - [Microsoft Azure](https://azure.microsoft.com/)
  - [Google Cloud Platform](https://console.cloud.google.com/)
  - [Heroku](https://www.heroku.com/)
  - [Vercel](https://vercel.com/)
  - [Netlify](https://www.netlify.com/)
  - [Render](http://Render.com)
  - [DigitalOcean](https://www.digitalocean.com/)
  - [Linode](https://www.linode.com/)

### Features

- These will provide a variety of different capabilities and infrastructure services. Some are more barebones, and some more comprehensive.
- Decide in advance what type of deployment method you want to go with, and what features you need, before getting locked into a cloud hosting service, and then shop around for features vs price
- If you need simplest & least trouble, go with an all-in-one service like DigitalOcean. If you need more power and capabilities, look to a cloud platform like AWS or Azure cloud.

### Costs

- Billing & costs is a key thing to be aware of. What seems like a cheap hosting service may charge you extra for every little basic add-on feature.
- Some charge a flat rate per server instance per month: others bill hourly, and only charge you for the hours you use.
- Services like AWS tend to micro-charge for everything, but sometimes offer a generous free tier.
- Things you might be charged for:
  - Server hours (hourly/monthly)
  - DNS services
  - Bandwidth (in and out)
  - File storage (for example, S3 object storage)
  - Egress fees (if you access files or move them out of S3)
  - Database servers (hourly/monthly)
  - Upgrades (like higher bandwidth or CPU power, or higher RAM)

### Hosted databases

- Hosted databases are super-simple and help you get going quickly. However, they’re usually not free.
- If you have the skills, running a VPS and installing your own database is easy and fun. It also saves you costs for a dedicated database instance.
- However, it’s up to you to maintain and update it. ?

### Saving money

- Free tiers
  - Several services offer free tiers for a single project, or for non-commercial / personal sites, or for a limited time (like 1 year), or for a limited set of features (like — free without custom domain names). Make use of these!
- Serverless vs VPS
  - Deploying to “serverless” platforms (aka: PaaS) tend to be cheap and very quick for a single project, but costs quickly add up when you deploy a lot of different services.
  - With VPS (or dedicated servers), you can deploy multiple applications or sites to a single server, if your resource requirements are low.
  - This can save you costs for multiple apps vs “serverless” platforms.

Read more : <https://www.techslang.com/definition/what-is-a-hosting-environment/>
