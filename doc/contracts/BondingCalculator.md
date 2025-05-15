# BondingCalculator

## Overview

#### License: AGPL-3.0-or-later

```solidity
contract BondingCalculator is Initializable
```


## State variables info

### TOKEN (0x82bfefc8)

```solidity
address immutable TOKEN
```


## Functions info

### constructor

```solidity
constructor(address _token)
```


### initialize (0x8129fc1c)

```solidity
function initialize() public initializer
```


### getKValue (0x490084ef)

```solidity
function getKValue(address _pair) public view returns (uint256 k_)
```


### getTotalValue (0x68637549)

```solidity
function getTotalValue(address _pair) public view returns (uint256 _value)
```


### valuation (0x4249719f)

```solidity
function valuation(
    address _pair,
    uint256 amount_
) external view returns (uint256 _value)
```


### markdown (0x32da80a3)

```solidity
function markdown(address _pair) external view returns (uint256)
```

根据LP的RFV，计算一个TOKEN的USD价值。