# Deploying Apps as Serverless Functions

### What are Serverless Functions ?

- **Serverless functions** (also called **Functions as a Service**, or **FaaS**) are a deployment model similar to PaaS, that uses very short-lived web applications.
- Both serverless functions and PaaS abstract away the server, so you never see or interact with it.
- Serverless Functions are a way to deploy an application that runs once, when called from an URI endpoint, and then disappears.
- Serverless Functions are event-driven triggers — code runs in response to events or requests.

![](https://resources.metana.co/public/0d/ba/0dba3ae7d944f566e37a3066988d811af4e9c583e7e48f22011fe82582f4a876.png)

### Cost Model

- You normally only pay for the time you use running the functions — so, if your function is very quick, or infrequently called, the costs for running it can be very low.

### Scaling vs Permanence

- Serverless functions start almost instantly, allowing you to perform a process as if it were a live API.
- Serverless functions scale quickly — meaning, you can call 1000s of them at the same time without a hitch.
- The drawback is that these are short-lived — when the function ends, the application ends.

### Web Applications

- Because serverless functions are transient, they’re not usually well-suited for using as website.
- However, they can deliver any kind of content, including HTML or even a complete Node web application — *assuming the process ends when completed.*

### Common FaaS Platforms

- AWS Lambda - <https://aws.amazon.com/lambda/>
- Cloudflare Workers - <https://workers.cloudflare.com/>
- Google Cloud Functions - <https://cloud.google.com/functions/>
- Azure Functions - <https://azure.microsoft.com/en-us/products/functions/>
- Vercel Functions - <https://vercel.com/docs/functions>
- DigitalOcean Functions - <https://docs.digitalocean.com/products/functions/>

### Serverless Functions Use Cases

- **APIs for Web and Mobile Applications** → Serverless APIs are easy to build and maintain and are able to easily scale to meet demand.
- **Multimedia and Data Processing** → FaaS is frequently used to store or process user inputs, such as multimedia processing or other types of data.
- **Internet of Things** → Devices are increasingly using FaaS to execute their tasks, only sending and receiving data when triggered by an event.

### Deploying Web Applications as Serverless Functions

- Any code you write which performs a single function can probably be written to a serverless function.
- Node.js, Python, Go, C#, Typescript, and many other languages are supported.
- These functions can help you offload tasks from your main application — for example, if you frequently need to convert media file formats from user uploaded files, or other short-running but CPU-intensive operations.
- Typically, you pay only for the minutes your functions run, so this may save costs over running an always-on service just for one task.
- Example of deploying a “hello world” API as a serverless function — using the AWS Lambda platform

[YouTube video player](https://www.youtube.com/watch?v=xUFnPGVs7so)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=xUFnPGVs7so)
