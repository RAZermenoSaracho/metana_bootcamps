# Example Encryption with bcryptjs

code

```
const bcrypt = require('bcryptjs');

// Function to hash a password
async function hashPassword(password) {
  try {
    const salt = await bcrypt.genSalt(10);
    const hash = await bcrypt.hash(password, salt);
    return hash;
  } catch (error) {
    throw new Error('Error hashing password');
  }
}

// Function to verify a password
async function verifyPassword(password, hashedPassword) {
  try {
    const isMatch = await bcrypt.compare(password, hashedPassword);
    return isMatch;
  } catch (error) {
    throw new Error('Error verifying password');
  }
}

// Example usage
async function exampleUsage() {
  const plainTextPassword = 'myPassword123';
  
  // Hash the password
  const hashedPassword = await hashPassword(plainTextPassword);
  console.log('Hashed password:', hashedPassword);

  // Verify the password
  const isPasswordCorrect = await verifyPassword(plainTextPassword, hashedPassword);
  console.log('Is password correct?', isPasswordCorrect);
}

exampleUsage();

// Output:
// Hashed password: $2a$10$NQxL.4hOlNNVqBPB0cGn3.qJWYh.PeiRq1KxphFgkpIcUy9E1vjtu
// Is password correct? true
```

[YouTube video player](https://www.youtube.com/watch?v=rYdhfm4m7yg)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=rYdhfm4m7yg)
