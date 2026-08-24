# Exercise 4 – Testing with assert

**Table of contents:**

- **Exercise 4**
  - Targeted contract
  - Exercise
    - Goals
  - Solution

This exercise is based on the tutorial [How to test assertions](https://montyly.github.io/building-secure-contracts/program-analysis/echidna/basic/assertion-checking.html).

## Targeted contract

We will test the following contract:

code

```
contract Ownership{
    address owner = msg.sender;
    function Owner() public{
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

### Exercise

### Goals

Add asserts to ensure that after calling `transfer`:

- `msg.sender` must have its initial balance or less.
- `to` must have its initial balance or more.

Once Echidna finds the bug, fix the issue, and re-try your assertion with Echidna.

This exercise is similar to the first one, but using assertions instead of explicit properties.

However, in this exercise, it is easier to modify the original token contract.
