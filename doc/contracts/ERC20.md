# ERC20

## Overview

#### License: AGPL-3.0-or-later

```solidity
abstract contract ERC20 is IERC20
```


## Functions info

### name (0x06fdde03)

```solidity
function name() public view returns (string memory)
```


### symbol (0x95d89b41)

```solidity
function symbol() public view returns (string memory)
```


### decimals (0x313ce567)

```solidity
function decimals() public view returns (uint8)
```


### totalSupply (0x18160ddd)

```solidity
function totalSupply() public view override returns (uint256)
```

Returns the amount of tokens in existence.
### balanceOf (0x70a08231)

```solidity
function balanceOf(
    address account
) public view virtual override returns (uint256)
```

Returns the amount of tokens owned by `account`.
### transfer (0xa9059cbb)

```solidity
function transfer(
    address recipient,
    uint256 amount
) public virtual override returns (bool)
```

Moves `amount` tokens from the caller's account to `recipient`.

Returns a boolean value indicating whether the operation succeeded.

Emits a {Transfer} event.
### allowance (0xdd62ed3e)

```solidity
function allowance(
    address owner,
    address spender
) public view virtual override returns (uint256)
```

Returns the remaining number of tokens that `spender` will be
allowed to spend on behalf of `owner` through {transferFrom}. This is
zero by default.

This value changes when {approve} or {transferFrom} are called.
### approve (0x095ea7b3)

```solidity
function approve(
    address spender,
    uint256 amount
) public virtual override returns (bool)
```

Sets `amount` as the allowance of `spender` over the caller's tokens.

Returns a boolean value indicating whether the operation succeeded.

IMPORTANT: Beware that changing an allowance with this method brings the risk
that someone may use both the old and the new allowance by unfortunate
transaction ordering. One possible solution to mitigate this race
condition is to first reduce the spender's allowance to 0 and set the
desired value afterwards:
https://github.com/ethereum/EIPs/issues/20#issuecomment-263524729

Emits an {Approval} event.
### transferFrom (0x23b872dd)

```solidity
function transferFrom(
    address sender,
    address recipient,
    uint256 amount
) public virtual override returns (bool)
```

Moves `amount` tokens from `sender` to `recipient` using the
allowance mechanism. `amount` is then deducted from the caller's
allowance.

Returns a boolean value indicating whether the operation succeeded.

Emits a {Transfer} event.
### increaseAllowance (0x39509351)

```solidity
function increaseAllowance(
    address spender,
    uint256 addedValue
) public virtual returns (bool)
```


### decreaseAllowance (0xa457c2d7)

```solidity
function decreaseAllowance(
    address spender,
    uint256 subtractedValue
) public virtual returns (bool)
```

