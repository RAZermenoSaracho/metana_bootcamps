# Working with Branches

Branches in Git are like different storylines or paths of development within your project. They allow you to work on new features or bug fixes without affecting the main project until you're ready to merge your changes. Here's how you can work with branches effectively,

1. **Creating Branches**
   - To create a new branch, you use the `git branch` command followed by the name of the new branch: `git branch new-feature`
   - This creates a new branch named "new-feature" based on the current branch you're on.
2. **Switching Between Branches**
   - To switch to a different branch, you use the `git checkout` command followed by the name of the branch: `git checkout new-feature`
   - This switches you to the "new-feature" branch, allowing you to start working on it.
3. **Merging Branches**
   - Once you’ve completed work on a feature branch and are ready to incorporate your changes into the main project, first switch to the main branch using `git checkout main`, and then merge your feature branch into it with `git merge new-feature`.
   - This switches to the main branch and then merges the changes from the "new-feature" branch into it.
4. **Resolving Merge Conflicts**
   - Sometimes, when you merge branches, Git may encounter conflicts if the changes made in different branches overlap or conflict with each other.
   - Git will prompt you to resolve these conflicts manually by editing the affected files to choose which changes to keep.
   - After resolving conflicts, you need to stage the changes and commit them to complete the merge.

Working with branches allows you to manage complex projects more efficiently, collaborate with others, and experiment with new ideas without disrupting the main project. By mastering these branch-related commands, you'll have better control over your Git workflow and project development.

[YouTube video player](https://www.youtube.com/watch?v=QV0kVNvkMxc)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=QV0kVNvkMxc)
