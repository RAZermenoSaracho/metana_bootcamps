# Handlebars: Practice Exercise

In this Practice Exercise, you will practice the key Handlebars concepts learned previously, including using variables, rendering lists, and working with conditionals.

You’ll use an online playground where you can instantly see if your solution is working.

---

## Tool to Use

To get started, open the Handlebars Playground in your browser: <https://handlebarsjs.com/playground.html>

Once there, you’ll see three sections: Template, Data, and Output. As you modify the template or data, the output updates automatically so you can quickly check your work.

---

## Your Task

Using the playground, complete the following tasks.

### Task 1: Display a Title

You’ll be provided with some data. Your first task is to display the title on the page using a Handlebars variable.

---

### Task 2: Render a List

Next, the data contains a list of users. Render each user as a list item on the page.

---

### Task 3: Use a Conditional

For the final task, use a conditional to display a message:

- If `isAdmin` is true, show "Welcome, Admin."
- If `isAdmin` is false, show "Welcome, User."

You should be able to change the value of `isAdmin` in the data and see the output change accordingly.

---

## Data to Use

Paste this into the **Data (JSON)** panel in the playground:

json

```
{
"title":"User List",
"users":["Alice","Bob","Charlie"],
"isAdmin":true
}
```

---

## How You Know You’re Correct

You’ve completed the exercise successfully if:

- The title appears in the output.
- All three users (Alice, Bob, Charlie) appear as a list.
- Changing `"isAdmin"` from `true` to `false` changes the message shown in the output

If the output does not change when you update the data, review your template.

In the next lesson, you’ll learn about another templating engine called EJS.
