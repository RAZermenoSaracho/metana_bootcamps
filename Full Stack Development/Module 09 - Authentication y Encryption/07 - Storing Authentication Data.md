# Storing Authentication Data

After successfully authenticating a user, it's crucial to store their authentication data securely for future use.

### Why Store Authentication Data ?

- Storing authentication data allows the application to reuse it without having to re-authenticate with every request. This saves time and reduces unnecessary network traffic.
- By storing authentication data, users can remain logged in across sessions, providing a smoother and more convenient experience.

### Storage Locations

- **Cookies:** Cookies offer persistent storage of small amounts of data. They are commonly used for authentication tokens due to their automatic inclusion in HTTP requests and compatibility across browsers.
- **Local Storage:** Local storage provides persistent storage of larger amounts of data. It's suitable for storing authentication data such as user profiles or preferences.
- **Session Storage:** Session storage offers temporary storage of larger amounts of data. It's ideal for short-term storage of authentication data during a user's session.

*Additional Considerations*

- **Server-Side Caching:** Short-lived session authentication tokens can be cached on the server-side using tools like Redis, enhancing performance and scalability.
- **Node Libraries:** Regardless of the storage method chosen, using Node libraries can simplify and streamline the interaction with authentication data storage.

### Methods for Interaction

- **set Method:** Used to store data by providing a keyname.
- **get Method:** Used to retrieve the value of stored data using its keyname.

[YouTube video player](https://www.youtube.com/watch?v=GihQAC1I39Q)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=GihQAC1I39Q)
