# Practice - Storage and Cookies

## Practice the tutorials available in this link

[JavaScript Cookies](https://www.w3schools.com/js/js_cookies.asp)

## Additional Reading Materials

[Cookies, document.cookie](https://javascript.info/cookie)

---

### Practice JavaScript Cookies

Cookies are small pieces of data that websites store in your browser. They help remember information such as login status or user preferences. JavaScript allows you to create, read, and delete cookies.

### Setting a Cookie

To set a cookie in JavaScript, you use the `document.cookie` property:

code

```
document.cookie = "username=JohnDoe";
```

This sets a cookie named "username" with the value "JohnDoe". By default, cookies expire when the browser is closed, but you can set an expiration date.

### Setting Expiration for Cookies

To make a cookie last longer, you can set an expiration date:

code

```
let date = new Date();
date.setTime(date.getTime() + (7 * 24 * 60 * 60 * 1000));  // 7 days from now
let expires = "expires=" + date.toUTCString();
document.cookie = "username=JohnDoe; " + expires;
```

This sets the cookie to expire in 7 days.

### Reading a Cookie

To read a cookie, you can simply access `document.cookie`, but it returns all cookies as a string:

code

```
let cookies = document.cookie;
console.log(cookies);  // Output: "username=JohnDoe"
```

### Deleting a Cookie

To delete a cookie, you set its expiration date to a past date:

code

```
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 UTC";
```

### Additional Reading Materials

1. [**W3Schools - JavaScript Cookies**](https://www.w3schools.com/js/js_cookies.asp) A beginner-friendly guide to understanding and working with cookies in JavaScript.
2. [**JavaScript.info - Cookies**](https://javascript.info/cookie) A more detailed explanation of cookies, covering security and best practices.
