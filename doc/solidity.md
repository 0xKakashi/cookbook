![0xKakashi](../banner.png)

# 📔 COOKBOOK

> Developer Bookmarks, Resources, References and Guides

---

## 📄 DOCS: SOLIDITY

> Ethereum Solidity Smart Contracts Language Reference

[Website](https://ethereum.org) | [Documentation](https://ethereum.org/en/developers/docs) | [GitHub](https://github.com/ethereum)

---

## CONCEPTS

> Solidity Smart Contract Concepts

* [Comments](#comments)
* [Interface](#interface)
* [Event Log](#event-log)
* [Global Units](#global-units)
* [Block Transaction](#block-transaction)

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
blockhash(blockNumber)
block.coinbase
block.difficulty
block.gaslimit
block.number

block.timestamp

gasleft()

msg.data
msg.gas
msg.sender
msg.sig
msg.value

tx.gasprice
tx.origin
```
