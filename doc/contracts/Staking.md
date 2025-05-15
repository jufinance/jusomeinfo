# Staking

## Overview

#### License: AGPL-3.0-or-later

```solidity
contract Staking is OwnableUpgradeable
```


## Enums info

### CONTRACTS

```solidity
enum CONTRACTS {
	 DISTRIBUTOR,
	 LOCKER
}
```


## Structs info

### Epoch

```solidity
struct Epoch {
	uint256 length;
	uint256 number;
	uint256 endBlockTime;
	uint256 distribute;
}
```


### Claim

```solidity
struct Claim {
	uint256 deposit;
	uint256 gons;
	uint256 expiry;
	bool lock;
}
```


## Events info

### Staked

```solidity
event Staked(uint256 indexed uid, address indexed staker, uint256 amount)
```


### Unstaked

```solidity
event Unstaked(uint256 indexed uid, address indexed staker, uint256 unstakeAmount)
```


### Principal

```solidity
event Principal(uint256 indexed uid, address indexed staker, uint256 principal)
```


### EventStartClaimInterest

```solidity
event EventStartClaimInterest(uint256 indexed uid, address indexed staker, uint256 amount)
```


### EventRebase

```solidity
event EventRebase(uint256 curEpochNumber, uint256 profit, uint256 nextProfit, uint256 stakingTOKENBalance, uint256 sTOKENCirculatingSupply)
```

rebase数据


Parameters:

| Name                    | Type    | Description             |
| :---------------------- | :------ | :---------------------- |
| curEpochNumber          | uint256 | 当前epoch序号               |
| profit                  | uint256 | 本次rebase总发放收益           |
| nextProfit              | uint256 | 下次rebase预计发放收益          |
| stakingTOKENBalance     | uint256 | 当前Staking中TOKEN的存量      |
| sTOKENCirculatingSupply | uint256 | 当前sTOKEN的circulation供应量 |

## State variables info

### RELEASE_POOL (0x0119d777)

```solidity
contract IReleasePool immutable RELEASE_POOL
```


### PAIR_TOKEN_USDT (0x1a515a6a)

```solidity
address immutable PAIR_TOKEN_USDT
```


### JUC (0x8ee675ae)

```solidity
address immutable JUC
```


### TOKEN (0x82bfefc8)

```solidity
address immutable TOKEN
```


### sTOKEN (0x726ed7c4)

```solidity
address immutable sTOKEN
```


### epoch (0x900cf0cf)

```solidity
struct Staking.Epoch epoch
```


### distributor (0xbfe10928)

```solidity
address distributor
```


### locker (0xd7b96d4e)

```solidity
address locker
```


### totalBonus (0xa8dd07dc)

```solidity
uint256 totalBonus
```


### principals (0x767f06f1)

```solidity
mapping(uint256 => mapping(address => uint256)) principals
```


### isDestructionToken (0x4382af3e)

```solidity
mapping(address => bool) isDestructionToken
```


## Functions info

### constructor

```solidity
constructor(
    address _TOKEN,
    address _sTOKEN,
    address _JUC,
    address _releasePool,
    address _pairTOKENUSDT
)
```


### initialize (0x80d85911)

```solidity
function initialize(
    uint256 _epochTimeLength,
    uint256 _firstEpochNumber,
    uint256 _firstEpochBlockTime
) public initializer
```


### getNextRebaseTime (0xec2f448f)

```solidity
function getNextRebaseTime() external view returns (uint256)
```

获取下次rebase时间


Return values:

| Name | Type    | Description |
| :--- | :------ | :---------- |
| [0]  | uint256 | 下次rebase时间  |

### getEpochNumber (0x9a7b3be7)

```solidity
function getEpochNumber() external view returns (uint256)
```

获取当前epoch number


Return values:

| Name | Type    | Description  |
| :--- | :------ | :----------- |
| [0]  | uint256 | epoch number |

### getStakeInfo (0x5cb7d00b)

```solidity
function getStakeInfo(
    uint256 _uid,
    address _user
) external view returns (uint256 principalAmt, uint256 interest)
```

获取质押信息


Parameters:

| Name  | Type    | Description |
| :---- | :------ | :---------- |
| _uid  | uint256 | 项目id        |
| _user | address | 用户地址        |


Return values:

| Name         | Type    | Description |
| :----------- | :------ | :---------- |
| principalAmt | uint256 | 质押本金        |
| interest     | uint256 | 收益          |

### getStakeAmount (0x0c2eb403)

```solidity
function getStakeAmount(address _user) public view returns (uint256)
```

获取质押数量
### getStakeTokenWorth (0x9248f8d3)

```solidity
function getStakeTokenWorth(
    uint256 _uid,
    address _user
) public view returns (uint256)
```

获取已质押TOKEN的USD价值
### getStakedAmountList (0xc2e5ed92)

```solidity
function getStakedAmountList(
    uint256 _uid,
    address[] calldata _accountList
) external view returns (uint256[] memory amountList_)
```


### stake (0x7628a37d)

```solidity
function stake(
    uint256 _uid,
    uint256 _amount,
    address _recipient
) external returns (bool)
```

质押TOKEN


Parameters:

| Name       | Type    | Description         |
| :--------- | :------ | :------------------ |
| _uid       | uint256 | 项目id                |
| _amount    | uint256 | 质押数量                |
| _recipient | address | TOKEN的owner @return |

### unstake (0x5b64f391)

```solidity
function unstake(uint256 _uid, bool _trigger, uint256 _amount) external
```

unstake 本金


Parameters:

| Name     | Type    | Description   |
| :------- | :------ | :------------ |
| _uid     | uint256 | 项目id          |
| _trigger | bool    | 是否尝试触发rebase  |
| _amount  | uint256 | unstake的数量    |

### claimInterest (0xed88c2bd)

```solidity
function claimInterest(
    uint256 _uid,
    bool _trigger,
    uint256 _amount,
    address _burnToken,
    uint256 _burnAmt,
    uint256 _releaseLevel
) external
```

开始释放Staking收益。


Parameters:

| Name          | Type    | Description       |
| :------------ | :------ | :---------------- |
| _uid          | uint256 | 项目id              |
| _trigger      | bool    | 是否尝试触发rebase      |
| _burnToken    | address | 释放的币种             |
| _amount       | uint256 | 释放的收益数量           |
| _burnAmt      | uint256 | 释放收益所需要销毁的数量      |
| _releaseLevel | uint256 | 释放等级。1~5对应150天到7天 |

### index (0x2986c0e5)

```solidity
function index() public view returns (uint256)
```

returns the sTOKEN index, which tracks rebase growth


Return values:

| Name | Type    | Description          |
| :--- | :------ | :------------------- |
| [0]  | uint256 | uint256 sTOKEN的index |

### rebase (0xaf14052c)

```solidity
function rebase() public
```

trigger rebase if epoch over
### contractBalance (0x8b7afe2e)

```solidity
function contractBalance() public view returns (uint256)
```

returns contract TOKEN holdings, including bonuses provided


Return values:

| Name | Type    | Description |
| :--- | :------ | :---------- |
| [0]  | uint256 | uint 合约余额   |

### giveLockBonus (0x03c23670)

```solidity
function giveLockBonus(uint256 _amount) external
```

provide bonus to locked staking contract


Parameters:

| Name    | Type    | Description |
| :------ | :------ | :---------- |
| _amount | uint256 | uint        |

### returnLockBonus (0xf62ae76a)

```solidity
function returnLockBonus(uint256 _amount) external
```

reclaim bonus from locked staking contract


Parameters:

| Name    | Type    | Description |
| :------ | :------ | :---------- |
| _amount | uint256 | uint        |

### setContract (0x865e6fd3)

```solidity
function setContract(
    Staking.CONTRACTS _contract,
    address _address
) external onlyOwner
```

sets the contract address for LP staking
        @param _contract address
### updateEpoch (0x53fdfab0)

```solidity
function updateEpoch(
    uint256 _epochLength,
    uint256 _endBlockTime
) external onlyOwner
```


### setDestructionToken (0xc5ab6c3e)

```solidity
function setDestructionToken(address token_, bool state_) external onlyOwner
```

