# AccessControl

## Overview

#### License: AGPL-3.0-or-later

```solidity
abstract contract AccessControl is Context
```

Contract module that allows children to implement role-based access
control mechanisms.

Roles are referred to by their `bytes32` identifier. These should be exposed
in the external API and be unique. The best way to achieve this is by
using `public constant` hash digests:

```
bytes32 public constant MY_ROLE = keccak256("MY_ROLE");
```

Roles can be used to represent a set of permissions. To restrict access to a
function call, use {hasRole}:

```
function foo() public {
    require(hasRole(MY_ROLE, msg.sender));
    ...
}
```

Roles can be granted and revoked dynamically via the {grantRole} and
{revokeRole} functions. Each role has an associated admin role, and only
accounts that have a role's admin role can call {grantRole} and {revokeRole}.

By default, the admin role for all roles is `DEFAULT_ADMIN_ROLE`, which means
that only accounts with this role will be able to grant or revoke other
roles. More complex role relationships can be created by using
{_setRoleAdmin}.

WARNING: The `DEFAULT_ADMIN_ROLE` is also its own admin: it has permission to
grant and revoke this role. Extra precautions should be taken to secure
accounts that have been granted it.
## Structs info

### RoleData

```solidity
struct RoleData {
	EnumerableSet.AddressSet members;
	bytes32 adminRole;
}
```


## Events info

### RoleAdminChanged

```solidity
event RoleAdminChanged(bytes32 indexed role, bytes32 indexed previousAdminRole, bytes32 indexed newAdminRole)
```

Emitted when `newAdminRole` is set as ``role``'s admin role, replacing `previousAdminRole`

`DEFAULT_ADMIN_ROLE` is the starting admin for all roles, despite
{RoleAdminChanged} not being emitted signaling this.

_Available since v3.1._
### RoleGranted

```solidity
event RoleGranted(bytes32 indexed role, address indexed account, address indexed sender)
```

Emitted when `account` is granted `role`.

`sender` is the account that originated the contract call, an admin role
bearer except when using {_setupRole}.
### RoleRevoked

```solidity
event RoleRevoked(bytes32 indexed role, address indexed account, address indexed sender)
```

Emitted when `account` is revoked `role`.

`sender` is the account that originated the contract call:
- if using `revokeRole`, it is the admin role bearer
- if using `renounceRole`, it is the role bearer (i.e. `account`)
## Constants info

### DEFAULT_ADMIN_ROLE (0xa217fddf)

```solidity
bytes32 constant DEFAULT_ADMIN_ROLE = 0x00
```


## Functions info

### hasRole (0x91d14854)

```solidity
function hasRole(bytes32 role, address account) public view returns (bool)
```

Returns `true` if `account` has been granted `role`.
### getRoleMemberCount (0xca15c873)

```solidity
function getRoleMemberCount(bytes32 role) public view returns (uint256)
```

Returns the number of accounts that have `role`. Can be used
together with {getRoleMember} to enumerate all bearers of a role.
### getRoleMember (0x9010d07c)

```solidity
function getRoleMember(
    bytes32 role,
    uint256 index
) public view returns (address)
```

Returns one of the accounts that have `role`. `index` must be a
value between 0 and {getRoleMemberCount}, non-inclusive.

Role bearers are not sorted in any particular way, and their ordering may
change at any point.

WARNING: When using {getRoleMember} and {getRoleMemberCount}, make sure
you perform all queries on the same block. See the following
https://forum.openzeppelin.com/t/iterating-over-elements-on-enumerableset-in-openzeppelin-contracts/2296[forum post]
for more information.
### getRoleAdmin (0x248a9ca3)

```solidity
function getRoleAdmin(bytes32 role) public view returns (bytes32)
```

Returns the admin role that controls `role`. See {grantRole} and
{revokeRole}.

To change a role's admin, use {_setRoleAdmin}.
### grantRole (0x2f2ff15d)

```solidity
function grantRole(bytes32 role, address account) public virtual
```

Grants `role` to `account`.

If `account` had not been already granted `role`, emits a {RoleGranted}
event.

Requirements:

- the caller must have ``role``'s admin role.
### revokeRole (0xd547741f)

```solidity
function revokeRole(bytes32 role, address account) public virtual
```

Revokes `role` from `account`.

If `account` had been granted `role`, emits a {RoleRevoked} event.

Requirements:

- the caller must have ``role``'s admin role.
### renounceRole (0x36568abe)

```solidity
function renounceRole(bytes32 role, address account) public virtual
```

Revokes `role` from the calling account.

Roles are often managed via {grantRole} and {revokeRole}: this function's
purpose is to provide a mechanism for accounts to lose their privileges
if they are compromised (such as when a trusted device is misplaced).

If the calling account had been granted `role`, emits a {RoleRevoked}
event.

Requirements:

- the caller must be `account`.