![0xKakashi](../banner.png)

# 📔 COOKBOOK

> Developer Bookmarks, Resources, References and Guides

---

## 📄 DOC: OPEN ZEPPELIN

> OpenZeppelin Smart Contracts Library Standard

[OpenZeppelin Documentation](https://docs.openzeppelin.com/)

---

## CONCEPTS

* [Install](#install)
* [Usage](#usage)
* [Extending](#extending)
* [Upgrades](#upgrades)
* [Access Control](#access-control)
* [Tokens](#tokens]
* [Utilities](#utilities)

---

### INSTALL

```bash
$ npm i --save @openzeppelin/contracts
```

---

### USAGE

* OpenZeppelin smart contracts are primarily meant for inheritance.
* Import the Contract utility necessary and identify inherited contract with `is`

```sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract MyNFT is ERC721 {
    constructor() ERC721("MyNFT", "MNFT") public {}
}
```

---

### EXTENDING

__Overriding__

```bash
// contracts/ModifiedAccessControl.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/access/AccessControl.sol";

contract ModifiedAccessControl is AccessControl {
    // override `revokeRole` function
    function revokeRole(bytes32, address) public override {
        revert("ModifiedAccessControl: cannot revoke roles");
    }
}
```

* The old `revokeRole` is replaced by the override function.
* Removal of the function is not possible, but modification is acceptable.

__Super__

```bash   
// contracts/ModifiedAccessControl.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/access/AccessControl.sol";

contract ModifiedAccessControl is AccessControl {
    function revokeRole(bytes32 role, address account) public override {
        require(
            role != DEFAULT_ADMIN_ROLE,
            "ModifiedAccessControl: cannot revoke default admin role"
        );

        super.revokeRole(role, account);
    }   
}
```

* `super.revokeRole` statement at the end will invoke `AccessControl`'s original version of `revokeRole`.

__Hooks__

* Override multiple related functions to inherited contract.
* Hooks are simply functions that are called before or after some action takes place.
* Hooks provide a centralized point to `hook` into and extend the original behavior.

```sol
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract ERC20WithSafeTransfer is ERC20 {
    function _beforeTokenTransfer(address from, address to, uint256 amount)
        internal virtual override
    {
        super._beforeTokenTransfer(from, to, amount);

        require(_validRecipient(to), "ERC20WithSafeTransfer: invalid recipient");
    }

    function _validRecipient(address to) private view returns (bool) {
        ...
    }
}

Hook Rules:
1. Whenever you override a parent's hook, re-apply the `virtual` attribute to the hook. Allows child contracts to add more functionality to the hook.
2. __Always__ call the parent's hook in your override using `super. Make sure all hooks in the inheritance tree are called: contracts like `ERC20Pausable` rely on this behavior.

```sol
contract MyToken is ERC20 {
    function _beforeTokenTransfer(address from, address to, uint256 amount)
        internal virtual override
    {
        super._beforeTokenTransfer(from, to, amount);
        ...
    }
}
```

---

### UPGRADES

__Install__

```bash
$ npm i --save @openzeppelin/contracts-upgradeable
```

* Similar functionality to general OpenZeppelin contracts with appended `Upgradeable` convention.
* `constructor`'s are replaced by internal initializer functions following convention `__{ContractName}_init`.

__Usage__

```sol
import "@openzeppelin/contracts/upgradeable/token/ERC721/ERC721Upgradeable.sol";

contract MyNFT is ERC721Upgradeable {
    ...
    function initialize() initializer public {
        __ERC721_init("MyNFT", "MNFT");
    }
}
```

__Deploy__

```js
const { ethers, upgrades } = require("hardhat");

async function main() {
    const MyNFT = await ethers.getContractFactory("MyNFT");

    const mc = await upgrades.deployProxy(MyNFT);

    await mc.deployed();
 
    console.log(`MyNFT contract: ${mc.address}`);
}

main();
```

---

### ACCESS CONTROL

* The standard and acceptable single-admin approach is `owner`
* OpenZeppelin provides `Ownable` for implementing ownership

```sol
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/access/Ownable.sol";

contract MyContract is Ownable {
    function uno() public {
         // anyone can call
    }

    function dos() public onlyOwner {
         // only owner can call
    }
}
```

* By default, the `owner` of an `Ownable` contract is the account deployer.
* Contracts can also be owned by other contracts, or simply `address`'s

Ownable actions:

```sol
// transfer owner account
transferOwnership

// relinquish admin privilege
renounceOwnership

__Role-based Access Control__

* Define a `minter` role along with an `owner`

```sol
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/access/AccessControl.sol";
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20, AccessControl {
    // create new role identifier for `minter`
    bytes32 public constant MINTER_ROLE = keccak256("MINTER_ROLE");
 
    constructor(address minter) public ERC20("MyToken", "TKN") {
        // grant `minter` to specified account
        _setupRole(MINTER_ROLE, minter);
    }

    function mint(address to, uint256 amount) public {
        // check account for `minter` role
        require(hasRole(MINTER_ROLE, msg.sender), "caller account not minter role");
        _mint(to, amount);
    }
}
```

__Multiple Role-based Access Control__

* `minter` role and `burner` role for token actions

```sol
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/access/AccessControl.sol";
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20, AccessControl {
    bytes32 public constant MINTER_ROLE = keccak256("MINTER_ROLE");
    bytes32 public constant MINTER_ROLE = keccak256("BURNER_ROLE");

    constructor(address minter, address burner) public ERC20("MyToken", "TKN") {
        _setupRole(MINTER_ROLE, minter);
        _setupRole(BURNER_ROLE, burner);
    }

    function mint(address to, uint256 amount) public {
        require(hasRole(MINTER_ROLE, msg.sender), "Caller is not a minter");
        _mint(to, amount);
    }

    function burn(address from, uint256 amount) public {
        require(hasRole(BURNER_ROLE, msg.sender), "Caller is not a burner");
        _burn(from, amount);
    }
}
```

__Granting and Revoking Roles__


