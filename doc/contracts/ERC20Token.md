# ERC20Token

## Overview

#### License: AGPL-3.0-or-later

```solidity
contract ERC20Token is ERC20Permit, AccessControl
```


## Constants info

### MINT (0x3e36f4c7)

```solidity
bytes32 constant MINT = keccak256("MINT")
```


## Modifiers info

### onlyVault

```solidity
modifier onlyVault()
```


## Functions info

### constructor

```solidity
constructor(
    string memory name_,
    string memory symbol_
) ERC20(name_, symbol_, 9)
```


### mint (0x40c10f19)

```solidity
function mint(address account_, uint256 amount_) external onlyVault
```


### burn (0x42966c68)

```solidity
function burn(uint256 amount) public virtual
```


### burnFrom (0x79cc6790)

```solidity
function burnFrom(address account_, uint256 amount_) public virtual
```


### _burnFrom (0xa22b35ce)

```solidity
function _burnFrom(address account_, uint256 amount_) public virtual
```

