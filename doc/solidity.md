![0xKakashi](../banner.png)

# 📔 COOKBOOK

> Developer Bookmarks, Resources, References and Guides

---

## 📄 DOC: SOLIDITY

> Ethereum Solidity Smart Contracts Language Reference

[Website](https://ethereum.org) | [Documentation](https://ethereum.org/en/developers/docs) | [GitHub](https://github.com/ethereum)

---

## CONCEPTS

> Solidity Smart Contract Concepts

* [Contracts](#contracts)
* [Functions](#functions)
* [Modifiers](#modifiers)
* [Comments](#comments)
* [Interface](#interface)
* [Event Log](#event-log)
* [Global Units](#global-units)
* [Block Transaction](#block-transaction)
* [Reserved](#reserved)

---

### Contracts

__State Variables__

State variables are variables whose values are permanently stored in contract storage.

```sol
contract SimpleStorage {
    uint storedData; // @state
}
```

__Functions__

Functions are the executable units of code.
Functions are defined inside a contract, but can be outside a contract as well.
Function Calls can happen `internally` or `externally` and have different levels of visibility towards other contrats.

```sol
contract SimpleAuction {
    function bid() public payable {
        // @func
    }
}
```

__Function Modifiers__

Function Modifiers can be used to amend the semantics of functions in a declarative way.
Overloading, is having the same modifier name with different parameters, and is not possible.
Modifiers can be overriden like Functions.

```sol
contract Purchase {
    address public seller;

    // @mod
    modifier onlySeller() {
        require(
            msg.sender == seller,
            "Only seller can call this."
        );
        _;
    }

    function abort() public view onlySeller {
        // @func with @mod
    }
}
```

__Events__

```sol
contract SimpleAuction {
    // @event
    event HighestBidIncreased(address bidder, uint amount); 

    function bid() public payable {
        // @event-trigger
        emit HighestBidIncreased(msg.sender, msg.value);
    }
}
```

__Struct Types__

```sol
contract Ballot {
    // @struct
    struct Voter {
        uint weight;
        bool voted;
        address delegate;
        uint vote;
    }
}
```

__Enum Types__

```sol
contract Purchase {
    // @enum
    enum State { Created, Locked, Inactive }
}
```

---

### Functions

__Visibility Specifiers__

* `public`: Visible externally and internally - Getter for storage/state variables.
* `private`: Only visible in the current contract.
* `external`: Only visible externally (only for functions).
* `internal`: Only visible internally.

---

### Modifiers

* `pure` _FUNCTION_: Disallows modification or access of state.
* `view` _FUNCTION_: Disallows modifications of state.
* `payable` _FUNCTION_: Allows receiving of Ether with call.
* `constant` _VARIABLE_: Disallows assignment (except initialisation), does not occupy storage slot.
* `immutable` _VARIABLE_: Allows exactly one assignment at construction time and is constant afterward. Stored in code.
* `anonymous` _EVENT_: Does not store event signature as topic.
* `indexed` _EVENT_: Stores the paramters as topic.
* `virtual` _FUNCTION_ / _MODIFIER_: Allows the function/modifier behavior to be changed in derived contracts.
* `override`_FUNCTION_ / _MODIFIER_ / _VARIABLE_: Changes the behavior of an entity in a base contract.

---

### Comments

```sol
/**
 * Multi-line comment
 * 
 * @author
 * @notice
 * @dev
 * @param
 * @return 
 */

// single-line comment
```

---

### Interface

```sol
interface HelloWorld {
    function hello() external pure;
    function world(int) external pure;
}
```

```sol
interface HelloWorldEvent {
    event Event();
    function hello() external pure;
    function world(int) external pure;
}

contract Test {
    bytes4 public hello_world_event = type(HelloWorldEvent).interfaceId;
}
```

__Contract ABI__

```sol
abi.decode(bytes memory encodedData, (...)) returns (...)

abi.encode(...) returns (bytes memory)

abi.encodePacked(...) returns (bytes memory)

abi.encodeWithSelector(bytes4 selector, ...) returns (bytes memory)

abi.encodeWithSignature(string memory signature, ...) returns (bytes memory)
abi.encodeWithSelector(bytes4(keccak256(bytes(signature)), ...)
```

---

### Event Log

```sol
event Deposit(address indexed _from, bytes32 indexed _id, uint _value);

emit Deposit(msg.sender, _id, msg.value);
```

---

### Global Units

```sol
1 ether
1 wei
1 gwei
1 seconds
1 minutes
1 hours
1 days
1 weeks
type(uint).min
type(uint).max
type(int8).min
type(int8).max
```

---

### Block Transaction

```sol
this | address
super

blockhash(blockNumber)
block.coinbase
block.difficulty
block.gaslimit
block.number

block.timestamp

gasleft()

revert()
revert(string memory message)

require()
require(bool condition, string memory message)

assert(bool condition)

msg.data
msg.gas
msg.sender
msg.sig
msg.value

tx.gasprice
tx.origin
```

---

### Reserved

> Reserved Keywords in Solidity Language

* `after`
* `alias`
* `apply`
* `auto`
* `case`
* `copyof`
* `default`
* `define`
* `final`
* `immutable`
* `implements`
* `in`
* `inline`
* `let`
* `macro`
* `match`
* `mutable`
* `null`
* `of`
* `partial`
* `promise`
* `reference`
* `relocatable`
* `sealed`
* `sizeof`
* `static`
* `supports`
* `switch`
* `typedef`
* `typeof`
* `unchecked`
