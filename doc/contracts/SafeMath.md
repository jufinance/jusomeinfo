# SafeMath

## Overview

#### License: AGPL-3.0-or-later

```solidity
library SafeMath
```

Wrappers over Solidity's arithmetic operations with added overflow
checks.

Arithmetic operations in Solidity wrap on overflow. This can easily result
in bugs, because programmers usually assume that an overflow raises an
error, which is the standard behavior in high level programming languages.
`SafeMath` restores this intuition by reverting the transaction when an
operation overflows.

Using this library instead of the unchecked operations eliminates an entire
class of bugs, so it's recommended to use it always.
## Functions info

### add

```solidity
function add(uint256 a, uint256 b) internal pure returns (uint256)
```

Returns the addition of two unsigned integers, reverting on
overflow.

Counterpart to Solidity's `+` operator.

Requirements:

- Addition cannot overflow.
### sub

```solidity
function sub(uint256 a, uint256 b) internal pure returns (uint256)
```

Returns the subtraction of two unsigned integers, reverting on
overflow (when the result is negative).

Counterpart to Solidity's `-` operator.

Requirements:

- Subtraction cannot overflow.
### sub

```solidity
function sub(
    uint256 a,
    uint256 b,
    string memory errorMessage
) internal pure returns (uint256)
```

Returns the subtraction of two unsigned integers, reverting with custom message on
overflow (when the result is negative).

Counterpart to Solidity's `-` operator.

Requirements:

- Subtraction cannot overflow.
### mul

```solidity
function mul(uint256 a, uint256 b) internal pure returns (uint256)
```

Returns the multiplication of two unsigned integers, reverting on
overflow.

Counterpart to Solidity's `*` operator.

Requirements:

- Multiplication cannot overflow.
### div

```solidity
function div(uint256 a, uint256 b) internal pure returns (uint256)
```

Returns the integer division of two unsigned integers. Reverts on
division by zero. The result is rounded towards zero.

Counterpart to Solidity's `/` operator. Note: this function uses a
`revert` opcode (which leaves remaining gas untouched) while Solidity
uses an invalid opcode to revert (consuming all remaining gas).

Requirements:

- The divisor cannot be zero.
### div

```solidity
function div(
    uint256 a,
    uint256 b,
    string memory errorMessage
) internal pure returns (uint256)
```

Returns the integer division of two unsigned integers. Reverts with custom message on
division by zero. The result is rounded towards zero.

Counterpart to Solidity's `/` operator. Note: this function uses a
`revert` opcode (which leaves remaining gas untouched) while Solidity
uses an invalid opcode to revert (consuming all remaining gas).

Requirements:

- The divisor cannot be zero.
### mod

```solidity
function mod(uint256 a, uint256 b) internal pure returns (uint256)
```

Returns the remainder of dividing two unsigned integers. (unsigned integer modulo),
Reverts when dividing by zero.

Counterpart to Solidity's `%` operator. This function uses a `revert`
opcode (which leaves remaining gas untouched) while Solidity uses an
invalid opcode to revert (consuming all remaining gas).

Requirements:

- The divisor cannot be zero.
### mod

```solidity
function mod(
    uint256 a,
    uint256 b,
    string memory errorMessage
) internal pure returns (uint256)
```

Returns the remainder of dividing two unsigned integers. (unsigned integer modulo),
Reverts with custom message when dividing by zero.

Counterpart to Solidity's `%` operator. This function uses a `revert`
opcode (which leaves remaining gas untouched) while Solidity uses an
invalid opcode to revert (consuming all remaining gas).

Requirements:

- The divisor cannot be zero.
### sqrrt

```solidity
function sqrrt(uint256 a) internal pure returns (uint256 c)
```


### percentageAmount

```solidity
function percentageAmount(
    uint256 total_,
    uint8 percentage_
) internal pure returns (uint256 percentAmount_)
```


### substractPercentage

```solidity
function substractPercentage(
    uint256 total_,
    uint8 percentageToSub_
) internal pure returns (uint256 result_)
```


### percentageOfTotal

```solidity
function percentageOfTotal(
    uint256 part_,
    uint256 total_
) internal pure returns (uint256 percent_)
```


### average

```solidity
function average(uint256 a, uint256 b) internal pure returns (uint256)
```

Taken from Hypersonic https://github.com/M2629/HyperSonic/blob/main/Math.sol

Returns the average of two numbers. The result is rounded towards
zero.
### quadraticPricing

```solidity
function quadraticPricing(
    uint256 payment_,
    uint256 multiplier_
) internal pure returns (uint256)
```


### bondingCurve

```solidity
function bondingCurve(
    uint256 supply_,
    uint256 multiplier_
) internal pure returns (uint256)
```

