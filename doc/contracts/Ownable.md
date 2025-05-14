# Ownable

## Overview

#### License: AGPL-3.0-or-later

```solidity
contract Ownable is IOwnable
```


## Events info

### OwnershipPushed

```solidity
event OwnershipPushed(address indexed previousOwner, address indexed newOwner)
```


### OwnershipPulled

```solidity
event OwnershipPulled(address indexed previousOwner, address indexed newOwner)
```


## Modifiers info

### onlyManager

```solidity
modifier onlyManager()
```


## Functions info

### constructor

```solidity
constructor()
```


### manager (0x481c6a75)

```solidity
function manager() public view override returns (address)
```


### renounceManagement (0x089208d8)

```solidity
function renounceManagement() public virtual override onlyManager
```


### pushManagement (0x46f68ee9)

```solidity
function pushManagement(address newOwner_) public virtual override onlyManager
```


### pullManagement (0x5a96ac0a)

```solidity
function pullManagement() public virtual override
```

