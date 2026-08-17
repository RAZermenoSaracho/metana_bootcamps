# Protecting REST API Endpoints

The first element of any web application to protect is API endpoints. To do that, you need to establish what routes should be accessible to whom.

1. **Choose a Method**
   - Decide what control method you will use to protect your routes
     - Simple authentication (username and password)
     - Token-based authentication
     - Session tokens (in cookies or session storage)
2. **Identify Restricted Routes**
   - Example restricted routes
     - Routes containing private data
     - User-specific routes (like "/profile")
     - Any route that modifies, inserts, or deletes data
     - Admin-specific routes
   - Some routes should typically not be private
     - Any public data routes (like "/blog/allPosts")
     - Login and logout routes — we need these to be public, so our backend can connect to them before the user is logged in
3. **Determine Roles**
   - Identify if restricted routes should be further restricted by role.
   - For example
     - GET /blog/posts: public — entire world can view blog posts
     - POST /blog/posts: create new blog post — should be private, for logged-in users with "editor" role
     - GET /user/3/messages: get user messages — private, only visible for logged-in user 3
     - DELETE /users/3/: delete user — private, for users with "admin" role
   - This results in a list of role checks
     - isLoggedIn
     - isUser(:id)
     - isAdmin
     - .. and so on
4. **Build Authentication Methods for Each Role**
   - You’ll need to build middleware functions for each role to check the given token or credentials and determine if the access should succeed or fail.
   - This may entail backend calls to your database.
5. **Implement Authentication Methods on All Routes**
6. **Test**
   - Use a tool like Postman to test your API routes.
   - It’s critically important to test all your API routes work correctly for all success and fail conditions.
   - Mistakes in API routes can lead to hacks, buggy behavior, or being unable to log in.
