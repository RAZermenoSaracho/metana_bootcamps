# Introduction to Authorization Frameworks

Authorization frameworks are like blueprints for deciding who gets to see what information in a digital system.

We're going to explore different ways of controlling access to information. These are not about the technical side but more about the concepts behind it. Remember, authorization is about deciding "who can see what" rather than "who someone is."

### Common Authorization Frameworks

1. **Role-Based Access Control (RBAC):** Think of this like assigning roles in a play. Each person (or user) gets a role (or role), and that role determines what they can do and see in the system. For example, an admin might have access to everything, while a regular user might only see certain parts.
2. **Discretionary Access Control (DAC):** In this method, the person who owns the data decides who can access it. It's like giving permission to someone to borrow your bike. You choose who gets access and what they can do with it.
3. **Attribute-Based Access Control (ABAC):** Here, access is determined by specific attributes or characteristics of the user, the resource, or the environment. It's like getting into a party based on whether you're over 18 or not. Your attributes decide if you're allowed in.

Among these methods, Role-Based Access Control (RBAC) and Attribute-Based Access Control (ABAC) are the most important for web applications. They're like the main characters in our story because they're widely used and super effective.

If you're curious to learn more, check out this summary: <https://www.strongdm.com/blog/rbac-vs-abac>
