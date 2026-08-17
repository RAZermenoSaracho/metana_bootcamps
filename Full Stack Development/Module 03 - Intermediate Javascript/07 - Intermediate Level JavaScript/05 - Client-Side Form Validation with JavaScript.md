# Client-Side Form Validation with JavaScript

![](https://resources.metana.co/public/cf/dd/cfdd42822267399d7685e775fdec98b59b122abb4a50ce5892842924dffe5a0a.png)

Client-side form validation is a way to check if the information entered into a form by a user is correct before it's sent to the server. It's like having a little helper in your web browser that immediately tells you if something is wrong as you fill out a form.

Imagine you're filling out a form online to sign up for a service. When you enter your email address, the web page might instantly tell you if it's not in the right format (like missing the "@" symbol), so you can fix it right away instead of waiting until you click "submit" and find out later.

JavaScript, a programming language that works in your web browser, is what makes this instant feedback possible. It can check each piece of information you enter, like your name, email, or password, to make sure it matches what the form expects.

By doing this check on your own computer, JavaScript saves you time by catching mistakes early and making sure you fill out the form correctly before you even try to send it. This makes the whole process smoother and less frustrating for you as a user.

However, it's important to know that while client-side validation is helpful, it's not enough on its own. The server that receives the form data should also double-check everything to make sure it's correct and safe. So, client-side validation and server-side validation work together to make sure your information is accurate and secure.

**We recommend you to refer this article** : [Click Here](https://www.freecodecamp.org/news/form-validation-with-html5-and-javascript/#:~:text=Client%20side%20validation%20occurs%20using,done%20via%20client%20side%20JavaScript.)

## Assignment - Adding Client-Side Validation to a HTML Form

[Click here to download the source code..](https://drive.google.com/file/d/1j1vq0DUdIQPx33K1Se6p_cNnzbu_pUqK/view?usp=sharing)

Objective: Implement client-side form validation using JavaScript to enhance the user experience and ensure data accuracy before submission.

Step-by-Step Tasks:

1. Open the provided **`index.html`** file in a text editor or an IDE.
2. Locate the **`<script>`** tag, create and import the **`index.js`** file at the end of the **`<head>`** section.
3. Inside the **`index.js`** file, identify the following variables:
   - **`form`**: Represents the HTML form element.
   - **`username`**, **`email`**, **`password`**, **`password2`**: Represent the input fields in the form.
4. Create a function named **`validateInputs()`** to perform form validation. This function should:
   - Retrieve the values of the input fields (**`username`**, **`email`**, **`password`**, **`password2`**).
   - Check if each field is empty and display an error message if it is.
   - Validate the email format using the **`isValidEmail()`** function.
   - Ensure that the password is at least 8 characters long.
   - Verify that the password and password confirmation fields match.
   - Set error messages and apply CSS classes (**`error`** or **`success`**) to indicate validation status.
5. Inside the **`validateInputs()`** function, utilize the provided **`setError()`** and **`setSuccess()`** functions to display error messages and apply styling to the input fields accordingly.
6. Implement event handling to trigger the **`validateInputs()`** function when the form is submitted. Use the **`addEventListener()`** method to listen for the **`submit`** event on the **`form`** element.
7. Save your changes to the **`index.js`** file.
8. Test your implementation by opening the **`index.html`** file in a web browser. Try submitting the form with various inputs to ensure that validation works as expected.
9. Refine your validation logic and styling as needed to provide a user-friendly experience.
10. Once you are satisfied with the validation functionality, consider further enhancements or customizations to improve the form's usability or security.

## Additional Reading Materials

[W3Schools.com](https://www.w3schools.com/js/js_validation.asp)
