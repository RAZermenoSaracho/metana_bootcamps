# Exercise - Array Methods

### **Exercise: Manage a Task List**

**Problem:** You are building a simple task manager where users can add, remove, and manipulate tasks in their to-do list using array methods.

**TIP:**You can use the online JavaScript compiler linked below and complete the following tasks.  
<https://www.programiz.com/javascript/online-compiler>

### **Tasks:**

1. **Initialize the Array:**
   - Create an array named `tasks` that contains the following initial tasks: `"Do laundry"`, `"Buy groceries"`, and `"Clean room"`.
2. **Add a New Task:**
   - Create a task object `“Study for exams"`.
   - Add the task at the end of the `tasks` array using `.push()`.
3. **Remove the Last Task:**
   - Remove the last task from the array using `.pop()`.
4. **Add a Task at the Beginning:**
   - Add a task `"Go to the gym"` to the beginning of the array using `.unshift()`.
5. **Remove the First Task:**
   - Remove the first task from the array using `.shift()`.
6. **Display All Tasks:**
   - Use `.forEach()` to loop through the `tasks` array and print each task to the console.
7. **Filter Tasks:**
   - Use `.filter()` to create a new array `shortTasks` that contains only tasks that have 10 characters or fewer.
8. **Map Tasks to Uppercase:**
   - Use `.map()` to create a new array `uppercaseTasks` where all tasks are in uppercase.
9. **Count Total Characters:**
   - Use `.reduce()` to find the total number of characters in all tasks combined.

### **Bonus Tasks (Optional):**

1. **Find a Task:**
   - Use `.find()` to locate the task `"Buy groceries"` in the array.
2. **Check if a Task Exists:**
   - Use `.includes()` to check if `"Study for exams"` is still in the list.

---

### **Expected Output Example:**

If the code is executed after performing all tasks:

code

```
tasks = ["Do laundry", "Buy groceries", "Clean room"]
shortTasks = ["Do laundry", "Clean room"]
uppercaseTasks = ["DO LAUNDRY", "BUY GROCERIES", "CLEAN ROOM"]
totalCharacters = 33
Found Task: Buy groceries
Study for exams exists: false
```
