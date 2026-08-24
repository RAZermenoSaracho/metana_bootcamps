# Exercise 1 – Testing token balances

**Table of contents:**

- Targeted contract
- Exercise

## Targeted contract

We will test the following contract:

code

```
contract Ownership {
    address owner = msg.sender;

    function Owner() {
        owner = msg.sender;
    }

    modifier isOwner() {
        require(owner == msg.sender);
        _;
    }
}

contract Pausable is Ownership {
    bool is_paused;

    modifier ifNotPaused() {
        require(!is_paused);
        _;
    }

    function paused() public isOwner {
        is_paused = true;
    }

    function resume() public isOwner {
        is_paused = false;
    }
}

contract Token is Pausable {
    mapping(address => uint) public balances;

    function transfer(address to, uint value) public ifNotPaused {
        balances[msg.sender] -= value;
        balances[to] += value;
        };
}
```

## Testing a token balance

### Goals

- Add a property to check that `echidna_caller` cannot have more than an initial balance of 10000.
- Once Echidna finds the bug, fix the issue, and re-check your property with Echidna.

The skeleton for this exercise is:

code

```
import "token.sol";

contract TestToken is Token {
    address echidna_caller = msg.sender;

    constructor() public {
        balances[echidna_caller] = 10000;
    }

    // add the property
    function echidna_test_balance() public view returns (bool) {
        // return your property condition here
    }
}
```
