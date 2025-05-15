# BondDepository

## Overview

#### License: AGPL-3.0-or-later

```solidity
contract BondDepository is OwnableUpgradeable
```

一个Bond是一个TOKEN的线性释放。购买一个Bond，可能需要价值n个TOKEN，这个n就是BondPrice。
购买一个Bond之后，它立刻就会线性释放一个TOKEN。
## Enums info

### PARAMETER

```solidity
enum PARAMETER {
	 VESTING,
	 PAYOUT,
	 FEE,
	 DEBT,
	 Ratio,
	 MINIMUM_PRICE
}
```


## Structs info

### Terms

```solidity
struct Terms {
	uint256 controlVariable;
	uint256 vestingTerm;
	uint256 minimumPrice;
	uint256 maxPayout;
	uint256 fee;
	uint256 maxDebt;
}
```


### Bond

```solidity
struct Bond {
	address owner;
	uint256 id;
	uint256 payout;
	uint256 vesting;
	uint256 lastBlockTime;
	uint256 pricePaid;
}
```


### Adjust

```solidity
struct Adjust {
	bool add;
	uint256 rate;
	uint256 target;
	uint256 buffer;
	uint256 lastBlock;
}
```


### RetBondInfo

```solidity
struct RetBondInfo {
	uint256 id;
	address owner;
	uint256 payout;
	uint256 vesting;
	uint256 claimable;
	uint256 pricePaid;
}
```


## Events info

### BondDeposit

```solidity
event BondDeposit(uint256 indexed uid, address indexed account, address indexed token, uint256 value)
```


### BondCreated

```solidity
event BondCreated(uint256 indexed uid, uint256 deposit, uint256 indexed payout, uint256 indexed expires, uint256 priceInUSD)
```


### BondRedeemed

```solidity
event BondRedeemed(uint256 indexed uid, address indexed recipient, uint256 payout, uint256 remaining)
```


### BondPriceChanged

```solidity
event BondPriceChanged(uint256 indexed uid, uint256 indexed priceInUSD, uint256 indexed internalPrice, uint256 debtRatio)
```


### ControlVariableAdjustment

```solidity
event ControlVariableAdjustment(uint256 initialBCV, uint256 newBCV, uint256 adjustment, bool addition)
```


## State variables info

### TOKEN (0x82bfefc8)

```solidity
address immutable TOKEN
```


### principle (0x016a4284)

```solidity
address immutable principle
```


### treasury (0x61d027b3)

```solidity
address immutable treasury
```


### DAO (0x98fabd3a)

```solidity
address immutable DAO
```


### sTOKEN (0x726ed7c4)

```solidity
address immutable sTOKEN
```


### isLiquidityBond (0xd7969060)

```solidity
bool immutable isLiquidityBond
```


### bondCalculator (0xc5332b7c)

```solidity
address immutable bondCalculator
```


### ContributionPool (0xbd254dc2)

```solidity
contract IContributionPool immutable ContributionPool
```


### Community (0x93dd9443)

```solidity
contract ICommunity immutable Community
```


### staking (0x4cf088d9)

```solidity
address staking
```


### stakingHelper (0x77b81895)

```solidity
address stakingHelper
```


### useHelper (0x2f3f470a)

```solidity
bool useHelper
```


### terms (0xd5025625)

```solidity
struct BondDepository.Terms terms
```


### adjustment (0x451ee4a1)

```solidity
struct BondDepository.Adjust adjustment
```


### bondInfo (0x10fc6172)

```solidity
mapping(uint256 => struct BondDepository.Bond) bondInfo
```


### bondInfoData (0x14244472)

```solidity
mapping(uint256 => mapping(address => struct BondDepository.Bond[])) bondInfoData
```


### totalDebt (0xfc7b9c18)

```solidity
uint256 totalDebt
```


### lastDecay (0xf5c2ab5b)

```solidity
uint256 lastDecay
```


### inviteRatio (0x13200659)

```solidity
uint256 inviteRatio
```


### needStakeAmount (0x3e4ad9da)

```solidity
uint256 needStakeAmount
```


### inviteBond (0xe37f9703)

```solidity
mapping(uint256 => mapping(address => struct BondDepository.Bond)) inviteBond
```


## Functions info

### constructor

```solidity
constructor(
    address _TOKEN,
    address _principle,
    address _treasury,
    address _DAO,
    address _bondCalculator,
    address _sTOKEN,
    address _contributionPool,
    address _community
)
```


### initialize (0x8129fc1c)

```solidity
function initialize() public initializer
```


### initializeBondTerms (0xe3b8d97f)

```solidity
function initializeBondTerms(
    uint256 _controlVariable,
    uint256 _vestingTerm,
    uint256 _minimumPrice,
    uint256 _maxPayout,
    uint256 _fee,
    uint256 _maxDebt,
    uint256 _initialDebt,
    uint256 _needStakeAmount,
    uint256 _inviteRatio
) external onlyOwner
```

initializes bond parameters


Parameters:

| Name             | Type    | Description |
| :--------------- | :------ | :---------- |
| _controlVariable | uint256 | uint        |
| _vestingTerm     | uint256 | uint        |
| _minimumPrice    | uint256 | uint        |
| _maxPayout       | uint256 | uint        |
| _fee             | uint256 | uint        |
| _maxDebt         | uint256 | uint        |
| _initialDebt     | uint256 | uint        |

### setBondTerms (0x1e321a0f)

```solidity
function setBondTerms(
    BondDepository.PARAMETER _parameter,
    uint256 _input
) external onlyOwner
```

set parameters for new bonds


Parameters:

| Name       | Type                          | Description |
| :--------- | :---------------------------- | :---------- |
| _parameter | enum BondDepository.PARAMETER | PARAMETER   |
| _input     | uint256                       | uint        |

### setAdjustment (0x1a3d0068)

```solidity
function setAdjustment(
    bool _addition,
    uint256 _increment,
    uint256 _target,
    uint256 _buffer
) external onlyOwner
```

set control variable adjustment


Parameters:

| Name       | Type    | Description |
| :--------- | :------ | :---------- |
| _addition  | bool    | bool        |
| _increment | uint256 | uint        |
| _target    | uint256 | uint        |
| _buffer    | uint256 | uint        |

### setStaking (0xd4d863ce)

```solidity
function setStaking(address _staking, bool _helper) external onlyOwner
```

set contract for auto stake


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| _staking | address | address     |
| _helper  | bool    | bool        |

### setNeedStakeAmount (0x32a93339)

```solidity
function setNeedStakeAmount(uint256 amount) public onlyOwner
```


### getBondInfoData (0xd140935e)

```solidity
function getBondInfoData(
    uint256 _uid,
    address _addr
) public view returns (BondDepository.Bond[] memory)
```


### getBondInfoDataLength (0x6ccc0012)

```solidity
function getBondInfoDataLength(
    uint256 _uid,
    address _addr
) public view returns (uint256 _length)
```


### deposit (0xfad3cc4b)

```solidity
function deposit(
    uint256 _uid,
    uint256 _amount,
    uint256 _maxPrice,
    address _depositor
) external returns (uint256)
```

deposit bond


Parameters:

| Name       | Type    | Description |
| :--------- | :------ | :---------- |
| _uid       | uint256 | 项目id        |
| _amount    | uint256 | uint        |
| _maxPrice  | uint256 | uint        |
| _depositor | address | address     |


Return values:

| Name | Type    | Description |
| :--- | :------ | :---------- |
| [0]  | uint256 | uint        |

### redeem (0x4547c642)

```solidity
function redeem(
    uint256 _uid,
    address _recipient,
    uint256 _id,
    bool _stake
) external returns (uint256)
```

redeem bond for user


Parameters:

| Name       | Type    | Description |
| :--------- | :------ | :---------- |
| _uid       | uint256 | 项目id        |
| _recipient | address | address     |
| _id        | uint256 | id of bond  |
| _stake     | bool    | bool        |


Return values:

| Name | Type    | Description |
| :--- | :------ | :---------- |
| [0]  | uint256 | uint        |

### redeemForInviteBond (0x2952d976)

```solidity
function redeemForInviteBond(
    uint256 _uid,
    address _recipient
) public returns (uint256)
```

redeem invite bond for user


Parameters:

| Name       | Type    | Description |
| :--------- | :------ | :---------- |
| _uid       | uint256 | 项目id        |
| _recipient | address | address     |


Return values:

| Name | Type    | Description |
| :--- | :------ | :---------- |
| [0]  | uint256 | uint        |

### getBondBuyInfo (0x69a6cabc)

```solidity
function getBondBuyInfo()
    public
    view
    returns (
        uint256 _bondPriceInTOKEN,
        uint256 _bondPriceInU,
        uint256 _maxQuantity,
        uint256 _debtRatio,
        uint256 _vestionTerm
    )
```

获取购买bond时的信息


Return values:

| Name              | Type    | Description                                    |
| :---------------- | :------ | :--------------------------------------------- |
| _bondPriceInTOKEN | uint256 | bond的TOKEN价格                                   |
| _bondPriceInU     | uint256 | bond的USDT价格,roi = token price / _bondPriceInU  |
| _maxQuantity      | uint256 | 最大可购买的TOKEN数量                                  |
| _debtRatio        | uint256 | DebtRatio，精度9                                  |
| _vestionTerm      | uint256 | 线性释放块数                                         |

### getBondSoldInfo (0x7ce0b651)

```solidity
function getBondSoldInfo()
    public
    view
    returns (
        uint256 _bondPriceInTOKEN,
        uint256 _bondPriceInU,
        uint256 _totalDebt,
        uint256 _maxDebt
    )
```

获取bond售卖时的信息


Return values:

| Name              | Type    | Description                                    |
| :---------------- | :------ | :--------------------------------------------- |
| _bondPriceInTOKEN | uint256 | bond的TOKEN价格                                   |
| _bondPriceInU     | uint256 | bond的USDT价格,roi = token price / _bondPriceInU  |
| _totalDebt        | uint256 | 当前已购买数量                                        |
| _maxDebt          | uint256 | 购买上限                                           |

### getBondInfoList (0xb234c8b4)

```solidity
function getBondInfoList(
    uint256 _uid,
    address _user
) public view returns (BondDepository.RetBondInfo[] memory _infoList)
```

获取用户的bond列表


Parameters:

| Name  | Type    | Description |
| :---- | :------ | :---------- |
| _uid  | uint256 | 项目id        |
| _user | address | 用户地址        |


Return values:

| Name      | Type                                | Description                                                                                                                                                                                                                                                         |
| :-------- | :---------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| _infoList | struct BondDepository.RetBondInfo[] | bond列表，元素是RetBondInfo。 struct RetBondInfo { uint256 id; // id of bond depositor address owner; // address of bond depositor uint256 payout; // pending uint256 vesting; // 还剩多少秒 uint256 claimable;  // 可领取数量 uint256 pricePaid; // In USD, for front end viewing } |

### getInviteBondInfo (0x10a50cf9)

```solidity
function getInviteBondInfo(
    uint256 _uid,
    address _user
) public view returns (BondDepository.RetBondInfo[] memory _inviteBondInfos)
```

获取用户的invite bond数据


Parameters:

| Name  | Type    | Description |
| :---- | :------ | :---------- |
| _uid  | uint256 | 项目id        |
| _user | address | 用户地址        |


Return values:

| Name             | Type                                | Description                                                                                                                                                                                                                                                           |
| :--------------- | :---------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| _inviteBondInfos | struct BondDepository.RetBondInfo[] | bond数据，类型是RetBondInfo[]。 struct RetBondInfo { uint256 id; // id of bond depositor address owner; // address of bond depositor uint256 payout; // pending uint256 vesting; // 还剩多少块 uint256 claimable;  // 可领取数量 uint256 pricePaid; // In USD, for front end viewing } |

### estimateGetTOKEN (0x767eb88f)

```solidity
function estimateGetTOKEN(uint256 _amount) public view returns (uint256 payout)
```

获取Bond的预估购买到TOKEN数量


Parameters:

| Name    | Type    | Description |
| :------ | :------ | :---------- |
| _amount | uint256 | token的数量    |


Return values:

| Name   | Type    | Description |
| :----- | :------ | :---------- |
| payout | uint256 | TOKEN的数量    |

### getMembers (0xcc1a380f)

```solidity
function getMembers(
    uint256 _uid,
    address _depositor
) public view returns (address)
```


### maxPayout (0xe0176de8)

```solidity
function maxPayout() public view returns (uint256)
```

当前最大可购买数量


Return values:

| Name | Type    | Description |
| :--- | :------ | :---------- |
| [0]  | uint256 | uint        |

### payoutFor (0x7927ebf8)

```solidity
function payoutFor(uint256 _value) public view returns (uint256)
```

calculate interest due for new bond

BondExecutingPrice_toTOKEN = ( Value / Premium )
                    = (value * 1e18 / (premium percent * 100)) / 1e18 * 100
             总共TOKEN的数量为_value, 一个bond可以换`bondPrice()`个TOKEN，返回可以换到多少TOKEN。


Parameters:

| Name   | Type    | Description |
| :----- | :------ | :---------- |
| _value | uint256 | uint        |


Return values:

| Name | Type    | Description |
| :--- | :------ | :---------- |
| [0]  | uint256 | uint        |

### bondPrice (0xd7ccfb0b)

```solidity
function bondPrice() public view returns (uint256 price_)
```

calculate current bond premium, 一个bond价值几个TOKENM， 1个？or price个。

price = premium = 100% + (debtRadio * BCV)
             = (1e9 + (tokenDebt/tokenSupply * 1e9 * BCV)) / 1e7
             = 100 + (tokenDebt/tokenSupply* BCV) * 100
             101% premium == premium% == premium percent * 100


Return values:

| Name   | Type    | Description |
| :----- | :------ | :---------- |
| price_ | uint256 | uint        |

### bondPriceInUSD (0x844b5c7c)

```solidity
function bondPriceInUSD() public view returns (uint256 price_)
```

converts bond price to DAI value


Return values:

| Name   | Type    | Description |
| :----- | :------ | :---------- |
| price_ | uint256 | uint        |

### getNewBCV (0xe2cdbeae)

```solidity
function getNewBCV(uint256 _price) public view returns (uint256 _newbcv)
```

get new bvc

(BCV * debtRatio) + 1， 表示1个bond值几个TOKEN。


Parameters:

| Name   | Type    | Description                                                          |
| :----- | :------ | :------------------------------------------------------------------- |
| _price | uint256 | uint 一个Bond的USD价值，markdown为一个TOKEN的USD价值。_price/markdown = 几个TOKEN。  |


Return values:

| Name    | Type    | Description                              |
| :------ | :------ | :--------------------------------------- |
| _newbcv | uint256 | uint 控制Bond的未释放比例，对一个bond可以兑换的TOKEN数量的影响 |

### getNewPrice (0x6e5bf8e7)

```solidity
function getNewPrice(uint256 _bcv) public view returns (uint256 _newPrice)
```

calculate new price for bond


Parameters:

| Name | Type    | Description |
| :--- | :------ | :---------- |
| _bcv | uint256 | uint        |


Return values:

| Name      | Type    | Description       |
| :-------- | :------ | :---------------- |
| _newPrice | uint256 | uint 一个bond的USD价格 |

### debtRatio (0xcea55f57)

```solidity
function debtRatio() public view returns (uint256 debtRatio_)
```

calculate current ratio of debt to TOKEN supply


Return values:

| Name       | Type    | Description |
| :--------- | :------ | :---------- |
| debtRatio_ | uint256 | uint        |

### standardizedDebtRatio (0x904b3ece)

```solidity
function standardizedDebtRatio() external view returns (uint256)
```

debt ratio in same terms for reserve or liquidity bonds


Return values:

| Name | Type    | Description |
| :--- | :------ | :---------- |
| [0]  | uint256 | uint        |

### currentDebt (0x759076e5)

```solidity
function currentDebt() public view returns (uint256)
```

calculate debt factoring in decay


Return values:

| Name | Type    | Description |
| :--- | :------ | :---------- |
| [0]  | uint256 | uint        |

### debtDecay (0xe392a262)

```solidity
function debtDecay() public view returns (uint256 decay_)
```

amount to decay total debt by


Return values:

| Name   | Type    | Description |
| :----- | :------ | :---------- |
| decay_ | uint256 | uint        |

### percentVestedFor (0x763f27c7)

```solidity
function percentVestedFor(
    uint256 _uid,
    address _depositor,
    uint256 _id,
    bool _invite
) public view returns (uint256 percentVested_)
```

calculate how far into vesting a depositor is


Parameters:

| Name       | Type    | Description          |
| :--------- | :------ | :------------------- |
| _uid       | uint256 | 项目id                 |
| _depositor | address | address              |
| _id        | uint256 | uint256 bond id      |
| _invite    | bool    | bool is invite bond  |


Return values:

| Name           | Type    | Description |
| :------------- | :------ | :---------- |
| percentVested_ | uint256 | uint        |

### pendingPayoutFor (0xd38a6cb3)

```solidity
function pendingPayoutFor(
    uint256 _uid,
    address _depositor,
    uint256 _id,
    bool _invite
) external view returns (uint256 pendingPayout_)
```

calculate amount of TOKEN available for claim by depositor


Parameters:

| Name       | Type    | Description          |
| :--------- | :------ | :------------------- |
| _depositor | address | address              |
| _id        | uint256 | uint256 bond id      |
| _invite    | bool    | bool is invite bond  |


Return values:

| Name           | Type    | Description |
| :------------- | :------ | :---------- |
| pendingPayout_ | uint256 | uint        |

### recoverLostToken (0xb4abccba)

```solidity
function recoverLostToken(address _token) external returns (bool)
```

allow anyone to send lost tokens (excluding principle or TOKEN) to the DAO


Return values:

| Name | Type | Description |
| :--- | :--- | :---------- |
| [0]  | bool | bool        |
