# Common Implementation Patterns

Implementations usually involve utilizing an authentication method that communicates with the backend for user authentication.

- Components within a protected route typically asynchronously call the authentication API and store the result.
- The user's authentication status is stored either in a cookie/localStorage, React `state`, or React `Context`.
- React Context facilitates easy access to information for any components beneath it.
- If the user is not logged in or authenticated, the React component will switch and either:
  - Render different content, e.g., `<div>You need to log in first!</div>`.
  - Redirect the user to a `/login` route or the home screen.
