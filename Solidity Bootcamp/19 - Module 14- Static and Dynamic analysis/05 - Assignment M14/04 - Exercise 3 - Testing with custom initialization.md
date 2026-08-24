# Exercise 3 – Testing with custom initialization

This exercise requires to finish exercise 1 and exercise 2

**Table of contents:**

- Targeted contract
- Exercise
- Solution

## Targeted contract

We will test the following contract:

code

```
contract Ownership{
    address owner = msg.sender;
    constructor() public {
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
            require(balances[msg.sender] >= value);
            balances[msg.sender] -= value;
            balances[to] += value;
       }
    }
```

## Testing with custom initialization

Consider the following extension of the token:

code

```
import “token.sol”;
contract MintableToken is Token{
      int totalMinted;
      int totalMintable;

      constructor(int _totalMintable) public {
         totalMintable = _totalMintable;
      }

      function mint(uint value) isOwner() public{
          require(int(value) + totalMinted < totalMintable);
          totalMinted += int(value);
          balances[msg.sender] += value;
       }
    }
```
