# Exercise 2 – Testing access control

This exercise requires to finish the exercise 1.

**Table of contents:**

- Targeted contract
- Exercise

## Targeted contract

We will test the following contract:

code

```
contract Ownership{
    address owner = msg.sender;
    function Owner() public {
         owner = msg.sender;
     }
     modifier isOwner(){
         require(owner == msg.sender);
         _;
      }
   }

contract Pausable is Ownership{
     bool is_paused;
     modifier ifNotPaused(){
               require(!is_paused);
               _;
      }

      function paused() isOwner public{
          is_paused = true;
      }

      function resume() isOwner public{
          is_paused = false;
      }
   }

contract Token is Pausable{
      mapping(address => uint) public balances;
      function transfer(address to, uint value) ifNotPaused public{
           balances[msg.sender] -= value;
           balances[to] += value;
       }
    }
```

## Testing access control

### Goals

- Consider `paused()` to be called at deployment, and the ownership removed.
- Add a property to check that the contract cannot be unpaused.
- Once Echidna finds the bug, fix the issue, and re-try your property with Echidna.

The skeleton for this exercise is:

code

```
import “token.sol”;
 contract TestToken is Token {
      address echidna_caller = msg.sender;
      constructor(){
         paused(); // pause the contract
         owner = 0x0; // lose ownership
       }  

      // add the property
      function echidna_no_transfer() public view returns (bool) {}
   }
```
