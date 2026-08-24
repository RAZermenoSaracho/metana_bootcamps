# Phishing with tx.origin

Explanation of tx.origin and how it can be exploited by malicious actors

[Video: Phishing with tx.origin | Hack Solidity (0.6)](https://www.youtube.com/watch?v=mk4wDlVB4ro)

**Transcript for the AI**

Hello everyone, in this video, we’ll explore how the tx.origin variable in Solidity smart contracts can be vulnerable to phishing attacks, where an attacker disguises as a trustworthy entity to deceive a user into performing unintended actions, such as sending all their ETH to the attacker’s address. First, let’s clarify what tx.origin is. Imagine Alice calls Contract A, which then calls Contract B. In Contract B, msg.sender is Contract A, but tx.origin is Alice, the address that originated the transaction. To demonstrate the vulnerability, consider a Wallet contract where anyone can deposit ETH, but only the owner can withdraw it using the transfer function. This function, on line 27, checks if tx.origin equals the owner state variable, set to msg.sender (Alice, if she deploys the contract) during construction. When Alice calls transfer, tx.origin is her address, the check passes, and she can withdraw ETH. If Eve calls transfer, tx.origin is Eve, not the owner (Alice), so the check fails, preventing withdrawal. However, since tx.origin reflects the transaction’s originator, Eve can exploit this by tricking Alice into calling a malicious contract that invokes Wallet.transfer, making tx.origin Alice’s address and bypassing the check.

Let’s see how this phishing attack works in code. We create an Attack contract with two state variables: owner (the address receiving the stolen ETH, set to Eve’s address) and wallet (the target Wallet contract’s address), initialized via a constructor. To exploit the Wallet contract, Eve tricks Alice into calling a function in Attack that invokes wallet.transfer(owner, wallet.balance), transferring all ETH from Wallet to Eve’s address. The attack unfolds as follows: Eve deceives Alice into calling Attack’s function, which calls Wallet.transfer. The Wallet contract checks if tx.origin is Alice (the owner), and since Alice initiated the transaction, the check passes, sending all ETH to Eve. In Remix, we deploy Wallet and Attack. Alice deposits 1 ETH into Wallet, confirmed by getBalance. If Eve directly calls Wallet.transfer, it fails because tx.origin is Eve. However, if Eve tricks Alice into calling Attack’s function, the transaction succeeds, draining Wallet’s 1 ETH to Eve, leaving Wallet with zero ETH, as verified by getBalance.

To prevent this phishing attack, replace tx.origin with msg.sender in the Wallet contract’s transfer function. Unlike tx.origin, msg.sender refers to the immediate caller. If Alice calls Eve’s malicious contract, which calls Wallet.transfer, msg.sender is Eve’s contract, not Alice, causing the ownership check to fail and preventing the attack. The key lesson is that using tx.origin for authorization can make your contract vulnerable to phishing attacks, as it trusts the transaction’s originator rather than the direct caller. By using msg.sender, you ensure stricter access control. Thanks for watching, and have a nice weekend!

## Links

- [Phishing with tx.origin | Hack Solidity (0.6)](https://www.youtube.com/watch?v=mk4wDlVB4ro)
