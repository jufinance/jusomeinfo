# ERC20Permit

## Overview

#### License: AGPL-3.0-or-later

```solidity
abstract contract ERC20Permit is ERC20, IERC2612Permit
```


## Constants info

### PERMIT_TYPEHASH (0x30adf81f)

```solidity
bytes32 constant PERMIT_TYPEHASH = 0x6e71edae12b1b97f4d1f60370fef10105fa2faae0126114a169c64845d6126c9
```


## State variables info

### DOMAIN_SEPARATOR (0x3644e515)

```solidity
bytes32 DOMAIN_SEPARATOR
```


## Functions info

### permit (0xd505accf)

```solidity
function permit(
    address owner,
    address spender,
    uint256 amount,
    uint256 deadline,
    uint8 v,
    bytes32 r,
    bytes32 s
) public virtual override
```

See {IERC2612Permit-permit}.
### nonces (0x7ecebe00)

```solidity
function nonces(address owner) public view override returns (uint256)
```

See {IERC2612Permit-nonces}.