# sToken

## Overview

#### License: AGPL-3.0-or-later

```solidity
contract sToken is ERC20Permit, Ownable
```


## Structs info

### Rebase

```solidity
struct Rebase {
	uint256 epoch;
	uint256 rebase;
	uint256 totalStakedBefore;
	uint256 totalStakedAfter;
	uint256 amountRebased;
	uint256 index;
	uint256 blockNumberOccured;
}
```


## Events info

### LogSupply

```solidity
event LogSupply(uint256 indexed epoch, uint256 timestamp, uint256 totalSupply)
```


### LogRebase

```solidity
event LogRebase(uint256 indexed epoch, uint256 rebase, uint256 index)
```


### LogStakingContractUpdated

```solidity
event LogStakingContractUpdated(address stakingContract)
```


### TransferGons

```solidity
event TransferGons(address indexed from, address indexed to, uint256 gons)
```


## State variables info

### stakingContract (0xee99205c)

```solidity
address stakingContract
```


### initializer (0x9ce110d7)

```solidity
address initializer
```


### rebases (0x73c69eb7)

```solidity
struct sToken.Rebase[] rebases
```


### INDEX (0x2df75cb1)

```solidity
uint256 INDEX
```


## Modifiers info

### onlyStakingContract

```solidity
modifier onlyStakingContract()
```


## Functions info

### constructor

```solidity
constructor(
    string memory name_,
    string memory symbol_
) ERC20(name_, symbol_) ERC20Permit()
```


### decimals (0x313ce567)

```solidity
function decimals() public pure override returns (uint8)
```

Returns the number of decimals used to get its user representation.
For example, if `decimals` equals `2`, a balance of `505` tokens should
be displayed to a user as `5,05` (`505 / 10 ** 2`).

Tokens usually opt for a value of 18, imitating the relationship between
Ether and Wei. This is the value {ERC20} uses, unless {_setupDecimals} is
called.

NOTE: This information is only used for _display_ purposes: it in
no way affects any of the arithmetic of the contract, including
{IERC20-balanceOf} and {IERC20-transfer}.
### initialize (0xc4d66de8)

```solidity
function initialize(address stakingContract_) external returns (bool)
```


### setIndex (0x40a5737f)

```solidity
function setIndex(uint256 _INDEX) external onlyManager returns (bool)
```


### rebase (0x058ecdb4)

```solidity
function rebase(
    uint256 profit_,
    uint256 epoch_
) public onlyStakingContract returns (uint256)
```

increases sToken supply to increase staking balances relative to profit_
        @param profit_ uint256
        @return uint256
### balanceOf (0x70a08231)

```solidity
function balanceOf(address who) public view override returns (uint256)
```


### gonsForBalance (0x1bd39674)

```solidity
function gonsForBalance(uint256 amount) public view returns (uint256)
```


### balanceForGons (0x7965d56d)

```solidity
function balanceForGons(uint256 gons) public view returns (uint256)
```


### circulatingSupply (0x9358928b)

```solidity
function circulatingSupply() public view returns (uint256)
```


### index (0x2986c0e5)

```solidity
function index() public view returns (uint256)
```


### transfer (0xa9059cbb)

```solidity
function transfer(address to, uint256 value) public override returns (bool)
```


### allowance (0xdd62ed3e)

```solidity
function allowance(
    address owner_,
    address spender
) public view override returns (uint256)
```


### transferFrom (0x23b872dd)

```solidity
function transferFrom(
    address from,
    address to,
    uint256 value
) public override returns (bool)
```


### approve (0x095ea7b3)

```solidity
function approve(address spender, uint256 value) public override returns (bool)
```


### increaseAllowance (0x39509351)

```solidity
function increaseAllowance(
    address spender,
    uint256 addedValue
) public override returns (bool)
```

Atomically increases the allowance granted to `spender` by the caller.

This is an alternative to {approve} that can be used as a mitigation for
problems described in {IERC20-approve}.

Emits an {Approval} event indicating the updated allowance.

Requirements:

- `spender` cannot be the zero address.
### decreaseAllowance (0xa457c2d7)

```solidity
function decreaseAllowance(
    address spender,
    uint256 subtractedValue
) public override returns (bool)
```

Atomically decreases the allowance granted to `spender` by the caller.

This is an alternative to {approve} that can be used as a mitigation for
problems described in {IERC20-approve}.

Emits an {Approval} event indicating the updated allowance.

Requirements:

- `spender` cannot be the zero address.
- `spender` must have allowance for the caller of at least
`subtractedValue`.