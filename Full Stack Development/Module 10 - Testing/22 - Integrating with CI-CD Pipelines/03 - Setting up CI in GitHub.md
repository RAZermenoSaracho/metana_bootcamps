# Setting up CI in GitHub

### **Intro to CI tests**

- CI tests automate the verification of new code against existing functionality.
- They run on predefined triggers to prevent breaking changes from merging into the main branch.

### **Hooks**

- The triggering action which causes tests to run is called a **hook.**
- It could be something like “new code is pushed”, or “new branch created”, or “new PR opened against main branch”

### **Configuration**

- CI configurations are specified in a YAML file stored in **`.github/workflows/`** within the repository.
- This file details the triggers, commands, and conditions for running tests.

### **GitHub Actions**

- Automates workflows directly within GitHub for CI/CD processes.
- Enables custom workflows for building, testing, and deploying code based on specific triggers.
- Introductory video for a practical setup guide: <https://www.youtube.com/watch?v=5MJRtldPOEI>
