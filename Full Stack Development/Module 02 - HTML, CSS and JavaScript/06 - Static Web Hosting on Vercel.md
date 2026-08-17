# Static Web Hosting on Vercel

[YouTube video player](https://www.youtube.com/watch?v=8nTcV6zH7eY)

### Folder Structure

\**Ensure your project follows the recommended folder structure*

**Without JavaScript**

code

```
project-root/
├── index.html
└── styles/
    └── styles.css
```

**With JavaScript**

code

```
project-root/
├── index.html
├── styles/
│   └── styles.css
└── scripts/
    └── scripts.js
```

### Steps to Deploy on Vercel

- **Sign up / Log in to Vercel**
  - Go to [Vercel](https://vercel.com/).
  - Sign up for a new account or log in to your existing account.
- **Add a New Project**
  - Once logged in, click on the “Add New...” button.

![](https://resources.metana.co/public/8f/87/8f87bbbdf9334a4aefb2a6ef12f14480bdd777be43f101c8916949bf0a9d0669.png)

- **Select 'Project'**
  - Click on the “Project” option.

![](https://resources.metana.co/public/a0/e5/a0e52ca2b5b77c015313e605f3dfdb3c21f5ba04fd0497e088daf49a63e7942a.png)

- **Connect Your GitHub Account**
  - If you haven’t already connected your GitHub account, Vercel will prompt you to do so. Follow the instructions to authorize Vercel to access your GitHub repositories.
- **Import Your Git Repository**
  - Choose the repository containing your static site from the list. Then “Import” it.

![](https://resources.metana.co/public/25/83/2583f177c5cb57d6fe46647930e9426f62e3616ab198cf234d401610ed85eef8.png)

- **Configure Project Settings**
  - Give your project a name.
  - If your project files are in a specific subdirectory, change the root directory to point to that folder. For example, if your static site files are inside a folder named `public`, set the root directory to `public`.
- **Deploy Your Project**
  - Click on the “Deploy” button.

![](https://resources.metana.co/public/7e/d9/7ed9ea601b7b60872855fea294347314ee2912ff9d7226f94f00289b638f5933.png)

- **Redirect to Dashboard**
  - After the deployment process, you will be redirected to the Vercel dashboard where you can see the status of your deployment.

![](https://resources.metana.co/public/47/02/4702bc93c169b2e81554887a29a90dc293559ad9b877a36b4a8c23ad203d96b8.jpeg)

Your site should now be live, and you can access it via the URL provided by Vercel. The deployment process will automatically handle updates whenever you push changes to the connected GitHub repository.

## Links

- [YouTube video player](https://www.youtube.com/watch?v=8nTcV6zH7eY)
