# DepositHelper

## Overview

#### License: AGPL-3.0-or-later

```solidity
contract DepositHelper is Initializable
```


## Events info

### EventDepositHelper

```solidity
event EventDepositHelper(uint256 indexed uid, address indexed sender, uint256 amount, uint256 amountUSDTLast, uint256 amountUSDTSwapIn, uint256 amountActualA, uint256 amountActualB, uint256 liquidity)
```


## State variables info

### UNISWAPV2ROUTER (0xa8b62f7b)

```solidity
contract IUniswapV2Router immutable UNISWAPV2ROUTER
```


### JUB (0xc0bc725e)

```solidity
address immutable JUB
```


### USDT (0xc54e44eb)

```solidity
address immutable USDT
```


### BONDDEPOSITORY_LP (0x6d3a7f53)

```solidity
address immutable BONDDEPOSITORY_LP
```


### PAIR_JUB_USDT (0x7c53a349)

```solidity
address immutable PAIR_JUB_USDT
```


## Functions info

### constructor

```solidity
constructor(
    address _BONDDEPOSITORY_LP,
    address _JUB,
    address _USDT,
    address _PAIR_JUB_USDT,
    address _uniswapV2Router
)
```


### initialize (0x8129fc1c)

```solidity
function initialize() public initializer
```


### depositHelper (0x891cc685)

```solidity
function depositHelper(
    uint256 uid_,
    uint256 amount_,
    uint256 maxPrice_,
    address token_
) external
```


### estimateGetTOKEN (0x767eb88f)

```solidity
function estimateGetTOKEN(uint256 _amount) public view returns (uint256 payout)
```

获取Bond的预估购买到JUB数量


Parameters:

| Name    | Type    | Description |
| :------ | :------ | :---------- |
| _amount | uint256 | token的数量    |


Return values:

| Name   | Type    | Description |
| :----- | :------ | :---------- |
| payout | uint256 | JUB的数量      |
