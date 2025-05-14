# FeeReceiver

## Overview

#### License: GPL-3.0

```solidity
contract FeeReceiver is AccessControlUpgradeable
```


## Events info

### EventTriggerSwap

```solidity
event EventTriggerSwap(uint256 csmAmount, uint256 usdtAmount)
```


## Constants info

### PRECISION (0xaaf5eb68)

```solidity
uint256 constant PRECISION = 100
```


### PARTNER (0xebebcf3d)

```solidity
uint256 constant PARTNER = 30
```


### RUNNER (0x66d7c8ca)

```solidity
uint256 constant RUNNER = 70
```


## State variables info

### UNISWAPV2ROUTER (0xa8b62f7b)

```solidity
contract IUniswapV2Router immutable UNISWAPV2ROUTER
```


### USDT (0xc54e44eb)

```solidity
address immutable USDT
```


### rewardIsSend (0x558da71b)

```solidity
mapping(uint256 => bool) rewardIsSend
```


### partnerWallet (0x1ed7830e)

```solidity
address partnerWallet
```


### runnerWallet (0x5d77e6c7)

```solidity
address runnerWallet
```


## Modifiers info

### onlyManager

```solidity
modifier onlyManager()
```


## Functions info

### constructor

```solidity
constructor(address USDT_, address uniswapV2Router_)
```


### initialize (0x485cc955)

```solidity
function initialize(
    address partnerWallet_,
    address runnerWallet_
) public initializer
```


### triggerSwap (0xf8e5884b)

```solidity
function triggerSwap(uint256 amount_) external
```


### transferTokenOut (0xc15ded67)

```solidity
function transferTokenOut(
    address token_,
    address addr_,
    uint256 amount
) external onlyManager
```


### transferTokenOut (0x002e0ae7)

```solidity
function transferTokenOut(
    address payable account_,
    uint256 amount_
) external onlyManager
```


### setPartnerWallet (0xaab80ba1)

```solidity
function setPartnerWallet(address partnerWallet_) external onlyManager
```


### setRunnerWallet (0x1f7cfc2c)

```solidity
function setRunnerWallet(address runnerWallet_) external onlyManager
```

