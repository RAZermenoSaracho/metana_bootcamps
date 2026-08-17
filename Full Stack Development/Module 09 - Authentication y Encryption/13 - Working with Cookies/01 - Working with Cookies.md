# Working with Cookies

Cookies are a simple form of key-value storage accessible to the browser, created by the site that generates them. They are commonly utilized to store persistent site data for the user, such as JWT tokens or other private user data.

Cookies have **expiration dates**, disappearing either after the specified date or when the user clears their browser data. All cookies associated with a site are sent with every request made to that site.

### **Advantages and Disadvantages**

| Advantages | Disadvantages |
| --- | --- |
| Simplicity in implementation | Cookies have size limitations. If more storage is needed, local storage can be used |
|  | Cookies are sent with every request, potentially consuming bandwidth |

Accessing and managing cookies can be simplified using middleware.
