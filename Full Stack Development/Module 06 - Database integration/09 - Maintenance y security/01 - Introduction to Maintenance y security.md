# Introduction to Maintenance & security

### **What is Security ?**

Think of a database like your personal diary or a treasure chest where you keep all your secrets. You wouldn’t want just anyone to open it up and read it, right? That’s where security comes in. It’s all about keeping your database safe from unwanted access or attacks.

### **Don’t Leave Database Open to the Public if You Can Avoid It**

Leaving your diary out in the open where anyone can pick it up is not a good idea. Similarly, your database shouldn’t be easily accessible to just anyone on the internet. Here’s how you can keep it more secure:

- **Use Private Networks**: This is like keeping your diary in a locked room in your house where only your family can get in. A private network means your database is only accessible within a certain safe area, not the whole internet.
- **Optionally Use Host IP Filtering Rules**: This is like making a list of friends who are allowed to see your diary. Only the computers on this list (known by their “IP addresses”) can access your database. Everyone else is kept out.

### **Use SSL**

SSL (Secure Sockets Layer) or its newer version, TLS (Transport Layer Security), is a bit like sending your secret messages in a secure, locked box instead of out in the open. When your database is accessible over the internet:

- **Connect Using SSL/TLS**: This ensures that when your computer talks to your database over the internet, the conversation is encrypted. It’s like whispering secrets in a language only you and your friend understand.
- **This Avoids MITM (Man-In-The-Middle) Attacks**: An MITM attack is like someone sneaking up and listening to your secrets without you knowing. SSL/TLS makes sure that even if someone tries to eavesdrop, they can’t understand what’s being said.

In summary, database security involves using passwords, limiting who can access your database, and encrypting data sent over the internet to keep your valuable information safe from prying eyes.

### **Why do you need Backups ?**

Backups are copies of your important data stored in a separate location from the original. They’re like safety nets in case something goes wrong with your original data, such as accidental deletion, hardware failure, or cyberattacks.

### Additional Learning Materials

[YouTube video player](https://www.youtube.com/watch?v=qzX9tpNNFJ0)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=qzX9tpNNFJ0)
