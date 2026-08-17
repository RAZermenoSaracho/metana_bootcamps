# Private Route Wrappers

Another common pattern is to create a component we call a wrapper and use that to wrap any routes that should be private.

- The wrapper accepts components as props.
  - Example: `<PrivateRoute component={SomeOtherComponent} props={...props} />`
- The wrapper performs the authentication checks.
  - If authentication is successful, it will render the child components.
  - If authentication fails, it redirects the user.
