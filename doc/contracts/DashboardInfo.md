# DashboardInfo

## Overview

#### License: GPL-3.0

```solidity
contract DashboardInfo is OwnableUpgradeable
```


## Enums info

### CONTRACTS

```solidity
enum CONTRACTS {
	 USDT,
	 TOKEN,
	 STOKEN,
	 LP_TOKEN_USDT,
	 STAKING,
	 RELEASEPOOL,
	 TREASURY,
	 DISTRIBUTOR,
	 BONDCALCULATOR
}
```


## Constants info

### PRECISION (0xaaf5eb68)

```solidity
uint256 constant PRECISION = 1e4
```


### RATE_PRECISION (0x2b3ba681)

```solidity
uint256 constant RATE_PRECISION = 1e6
```


## State variables info

### USDT (0xc54e44eb)

```solidity
address USDT
```


### TOKEN (0x82bfefc8)

```solidity
address TOKEN
```


### sTOKEN (0x726ed7c4)

```solidity
address sTOKEN
```


### LP_TOKEN_USDT (0x6f7b0850)

```solidity
address LP_TOKEN_USDT
```


### staking (0x4cf088d9)

```solidity
address staking
```


### releasePool (0x23f7f407)

```solidity
address releasePool
```


### treasury (0x61d027b3)

```solidity
address treasury
```


### distributor (0xbfe10928)

```solidity
address distributor
```


### bondCalculator (0xc5332b7c)

```solidity
address bondCalculator
```


## Functions info

### initialize (0xf5e95acb)

```solidity
function initialize(
    address _USDT,
    address _TOKEN,
    address _sTOKEN,
    address _LP_TOKEN_USDT,
    address _staking,
    address _releasePool,
    address _treasury,
    address _distributor,
    address _bondCalculator
) public initializer
```


### overview (0x3a2056f1)

```solidity
function overview()
    external
    view
    returns (
        uint256 amountTOKEN,
        uint256 priceTOKEN,
        uint256 circulatingTOKEN,
        uint256 stakedTOKEN,
        uint256 bondUSDT,
        uint256 bondLPWorth
    )
```

Dashboard基本信息.


Return values:

| Name             | Type    | Description                         |
| :--------------- | :------ | :---------------------------------- |
| amountTOKEN      | uint256 | Total Minting Amount(NVB), 精度9.     |
| priceTOKEN       | uint256 | TOKEN Price, 精度4.                   |
| circulatingTOKEN | uint256 | Circulating supply xxx TOKEN, 精度9.  |
| stakedTOKEN      | uint256 | Staked xxx TOKEN, 精度9.              |
| bondUSDT         | uint256 | Bond USDT$xxxx, 精度4.                |
| bondLPWorth      | uint256 | Bond LP$xxxx, 精度4.                  |

### getChartsInfo (0x9b72aea1)

```solidity
function getChartsInfo()
    external
    view
    returns (
        uint256 circulatingWorthTOKEN,
        uint256 treasuryRFV,
        uint256 treasuryLPRatio,
        uint256 stakedTOKENRatio,
        uint256 runwayDay,
        uint256 treasuryAssetTotal,
        uint256 totalTOKENBurning
    )
```

获取图标信息


Return values:

| Name                  | Type    | Description                                    |
| :-------------------- | :------ | :--------------------------------------------- |
| circulatingWorthTOKEN | uint256 | Total value of sTOKEN circulating supply, 精度4  |
| treasuryRFV           | uint256 | Risk Free Value of Treasury Assets, 精度4        |
| treasuryLPRatio       | uint256 | Protocol Owned Liquidity TOKEN-USDT, 精度4       |
| stakedTOKENRatio      | uint256 | TOKEN Staked, 精度4                              |
| runwayDay             | uint256 | Runway Available, 精度4                          |
| treasuryAssetTotal    | uint256 | Market Value of Treasury Assets, 精度4           |
| totalTOKENBurning     | uint256 | Total TOKEN Burning, 精度9                       |

### setContract (0x865e6fd3)

```solidity
function setContract(
    DashboardInfo.CONTRACTS _contract,
    address _address
) external onlyOwner
```


### getCirculatingWorthTOKEN (0x0f410427)

```solidity
function getCirculatingWorthTOKEN()
    external
    view
    returns (uint256 circulatingWorthTOKEN)
```


### getTreasuryRFV (0x9f61a73a)

```solidity
function getTreasuryRFV() external view returns (uint256 treasuryRFV)
```


### getTreasuryLPRatio (0xeeeee4d4)

```solidity
function getTreasuryLPRatio() external view returns (uint256)
```


### getStakedTOKENRatio (0x229940be)

```solidity
function getStakedTOKENRatio() external view returns (uint256)
```


### getRunway (0x5b6f9455)

```solidity
function getRunway() external view returns (uint256)
```


### getTotalTOKENBurning (0x7758a9b3)

```solidity
function getTotalTOKENBurning() external view returns (uint256)
```


### getTreasuryAssetTotal (0x4ed3648a)

```solidity
function getTreasuryAssetTotal()
    external
    view
    returns (uint256 treasuryAssetTotal)
```

