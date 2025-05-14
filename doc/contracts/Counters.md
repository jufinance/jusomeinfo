# Counters

## Overview

#### License: AGPL-3.0-or-later

```solidity
library Counters
```


## Structs info

### Counter

```solidity
struct Counter {
	uint256 _value;
}
```


## Functions info

### current

```solidity
function current(
    Counters.Counter storage counter
) internal view returns (uint256)
```


### increment

```solidity
function increment(Counters.Counter storage counter) internal
```


### decrement

```solidity
function decrement(Counters.Counter storage counter) internal
```

