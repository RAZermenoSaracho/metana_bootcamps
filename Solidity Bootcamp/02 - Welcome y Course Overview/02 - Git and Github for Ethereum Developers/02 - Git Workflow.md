# Git Workflow

## Workflow for Submitting Assignments on GitHub **🖥️**

This is how you will be checking your module assignments. Make sure to follow the steps below to maintain your code for the assignments in the correct structure.

### Step 1: Receive GitHub Collaboration Invitation 📩

1. **Instructor Creates the Repository**: After the orientation, your instructor will create a repository for you.
2. **Check Your [GitHub](https://github.com/) Notifications**: You will receive an invitation to collaborate on the repository. This invitation will be sent to your GitHub account.

![](https://resources.metana.co/public/e7/f8/e7f803efc59c8d4d8c1d0a9e72a9209ed5ae06f5e1f976c7ce9061eac8d457b3.png)

1. **Accept the Invitation**:
   - Go to your **GitHub notifications** or **email**.
   - Click on the invitation link, which will direct you to the repository.
   - Accept the invitation to become a collaborator.

### Step 2: Set Up Your Local Workspace with Git 💻

If you haven’t installed Git yet, [download and install it](https://git-scm.com/downloads). You can also install [GitHub CLI](https://cli.github.com/) if preferred.

1. **Open your terminal/command prompt**.
2. **Navigate to the directory** where you want your project to reside: `cd path/to/your-folder`
3. **Clone your GitHub repository**:  
   Go to the **GitHub repository** you were invited to and copy the **HTTPS URL** (located on the repository’s main page).  
   Clone the repository using the URL:  
   `git clone <HTTPS URL>`
4. **Navigate into the repository**: `cd ./<YourRepositoryName>`

### Step 3: Branching for Each Module **🌿**

For every module you work on:

1. **Navigate to the root of your repository** in the terminal.
2. **Create and switch to a new branch**: Replace `n` with the appropriate module number.  
   `git checkout -b module-n`

### Step 4: Committing Your Work 📝

After completing your tasks for a module:

1. **Add your changes** to Git: `git add .`
2. **Commit the changes**: Replace the message with a suitable description of your work. `git commit -m "Completed tasks for module-n"`
3. **Push the branch** to GitHub: `git push origin module-n`

### Step 5: Creating a Pull Request (PR) 🔀

After pushing your branch to GitHub, it’s time to create a Pull Request (PR):

1. **Go to your repository on GitHub**.
2. **Click on the `Pull requests` tab**, then click the `New pull request` button.
3. **Select your module branch** (e.g., `module-n`) as the branch you want to merge.
4. **Click on `Create pull request`**.
5. **Add a descriptive title and comment**, explaining the changes you’ve made.
6. **Request a review from the instructor**:
   - Click on the gear icon next to **‘Reviewers’** on the right-hand side and select your instructor’s name.
7. **Submit the pull request**.

### Step 6: Merging the Pull Request ✅

To ensure the main branch remains properly managed:

1. **Approval Needed**: Before merging your PR into the main branch, you **need approval from your instructor** (the code reviewer). This ensures the main branch stays clean and that code is reviewed for quality.
2. **Merge the PR**: Once your PR is approved, **you will be allowed to merge it into the main branch**.

### Conclusion 🎉

Congratulations! You’ve successfully learned how to manage and collaborate on your codebase using Git and GitHub in this updated process. By following these steps, you are now part of an efficient and well-structured workflow that will help you collaborate seamlessly with instructors and peers. Happy coding!
