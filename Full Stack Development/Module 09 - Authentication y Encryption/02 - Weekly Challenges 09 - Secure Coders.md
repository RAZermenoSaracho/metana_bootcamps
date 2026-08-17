# Weekly Challenges 09 : Secure Coders

Welcome to **Weekly Challenges 09: Secure Coders!** This week’s challenges are focused on helping you understand and implement core concepts of authentication and authorization, making your web applications more secure and robust. Each challenge is designed to provide hands-on practice while being creative and fun. We encourage you to **attempt at least one challenge this week** to enhance your skills in web security!

---

### Challenge 1: **“Secret Message Locker”**

**Description:**

Create a simple web application where users can sign up and log in to access their “secret messages.” Implement authentication using JSON Web Tokens (JWT). Once authenticated, users should see their own secret messages, which are stored securely. Only authenticated users can view and add new messages, and their tokens should expire after a certain period.

- **Extensions:** Add password hashing with bcrypt, implement role-based access control (e.g., admins can delete messages), and use environment files for managing secrets like JWT keys.
- **Skills Covered:** JWT authentication, token management, bcrypt for password hashing, environment file usage.

---

### Challenge 2: **“Access Adventure”**

**Description:**

Create a simple text-based adventure game where users must “log in” to access different parts of the game. Each user is given a basic “Explorer” role by default. Use JWT to handle user authentication and restrict access to specific areas of the game based on the role. For simplicity, let users progress through a series of text-based “rooms” where some require a specific role to enter (e.g., “Knight’s Hall” requires a “Knight” role).

- **Extensions:** Allow users to “level up” and gain new roles after completing challenges, or add a secret area that requires solving a riddle.
- **Skills Covered:** JWT authentication, role-based access, route protection.

---

### Challenge 3: **“Cookie Clicker Collector”**

**Description:**

Build a simple web app where users must log in to access a “cookie collection” page. Once logged in, users can click a button to collect virtual cookies, and their progress is stored using cookies or local storage. Ensure users are authenticated with JWT before allowing access to the collection page.

- **Extensions:** Add a timer that limits how often cookies can be collected or create a “bonus cookie” feature that appears randomly.
- **Skills Covered:** Authentication with JWT, storing data using cookies or local storage, protecting routes.
