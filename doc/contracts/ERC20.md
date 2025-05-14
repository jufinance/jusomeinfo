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

Returns the name of the token.
### symbol (0x95d89b41)

```solidity
function symbol() public view returns (string memory)
```

Returns the symbol of the token, usually a shorter version of the
name.
### decimals (0x313ce567)

```solidity
function decimals() public pure virtual override returns (uint8)
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
### totalSupply (0x18160ddd)

```solidity
function totalSupply() public view override returns (uint256)
```

See {IERC20-totalSupply}.
### balanceOf (0x70a08231)

```solidity
function balanceOf(
    address account
) public view virtual override returns (uint256)
```

See {IERC20-balanceOf}.
### transfer (0xa9059cbb)

```solidity
function transfer(
    address recipient,
    uint256 amount
) public virtual override returns (bool)
```

See {IERC20-transfer}.

Requirements:

- `recipient` cannot be the zero address.
- the caller must have a balance of at least `amount`.
### allowance (0xdd62ed3e)

```solidity
function allowance(
    address owner,
    address spender
) public view virtual override returns (uint256)
```

See {IERC20-allowance}.
### approve (0x095ea7b3)

```solidity
function approve(
    address spender,
    uint256 amount
) public virtual override returns (bool)
```

See {IERC20-approve}.

Requirements:

- `spender` cannot be the zero address.
### transferFrom (0x23b872dd)

```solidity
function transferFrom(
    address sender,
    address recipient,
    uint256 amount
) public virtual override returns (bool)
```

See {IERC20-transferFrom}.

Emits an {Approval} event indicating the updated allowance. This is not
required by the EIP. See the note at the beginning of {ERC20}.

Requirements:

- `sender` and `recipient` cannot be the zero address.
- `sender` must have a balance of at least `amount`.
- the caller must have allowance for ``sender``'s tokens of at least
`amount`.
### increaseAllowance (0x39509351)

```solidity
function increaseAllowance(
    address spender,
    uint256 addedValue
) public virtual returns (bool)
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
) public virtual returns (bool)
```

Atomically decreases the allowance granted to `spender` by the caller.

This is an alternative to {approve} that can be used as a mitigation for
problems described in {IERC20-approve}.

Emits an {Approval} event indicating the updated allowance.

Requirements:

- `spender` cannot be the zero address.
- `spender` must have allowance for the caller of at least
`subtractedValue`.