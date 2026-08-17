# Understanding and Working with Session Storage

Session storage, also known as session cookies, provides an alternative to using standard cookies or local storage in web applications.

- **Similar to Local Storage:** Accessing session storage is similar to accessing local storage, using the `window.sessionStorage` object.

### Advantages and Disadvantages

- Session storage is considered *more secure* than cookies or local storage because it is ephemeral. This means that the stored data is only available for the duration of the user's browsing session. Once the user closes the browser tab, the session ends, and the data is cleared.
- This ephemeral nature can be a disadvantage as well. Since *session storage data is cleared when the browsing session ends*, users may need to reauthorize each time they visit the application.

[YouTube video player](https://www.youtube.com/watch?v=RxUc6ZWwgfw)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=RxUc6ZWwgfw)
