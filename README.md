# ZKOracle
An oracle framework with zero knowledge proof

## Features

* 

## Dependencies

* Truffle >=
* Solidity >=

## Usages

### Oracle

#### Register
Register as an oracle with deposit.

`function oracle_register(bool TEE, bool MPC) public`

* The address which sends this message will become the owner of this oracle.

| name | type | detail |
| :-- | :-- | :-- |
| TEE | `bool` | The oracle use trusted execution environment |
| MPC | `bool` | The oracle use multi-party computation |

#### Unregister
Unregister from the oracle list and return the deposits.

`function oracle_unregister() public`

* This function can only be called by the owner of the oracle.
* User cannot sending any computation request after oracle unregistered.
* The locked deposits will only be returned after user remove the secret.

### Secret

#### Create secret
Create a secret on an oracle.

`function secret_create(bytes secret, address oracle, bytes proof) public`

* The address which sends this message will become the owner of this secret.

| name | type | detail |
| :-- | :-- | :-- |
| secret | `bytes` | The encrypted secret |
| oracle | `address` | The address of the oracle |
| proof | `bytes` | The zero knowledge proof of the encryption |

#### Remove secret
Remove a secret from an oracle.

`function secret_remove(bytes32 secret_key, address oracle) public`

* This function can only be called by the owner of the secret.

| name | type | detail |
| :-- | :-- | :-- |
| secret_key | `bytes32` | The keccak256 hash of the secret |
| oracle | `address` | The address of the oracle |

#### Grant access
Grant access of a secret for an user on an oracle.

`function secret_grant_user(bytes32 secret_key, address user, address oracle) public`

* This function can only be called by the owner of the secret.

| name | type | detail |
| :-- | :-- | :-- |
| secret_key | `bytes32` | The keccak256 hash of the secret |
| user | `address` | The address of granted user |
| oracle | `address` | The address of granted oracle |

### Circuit

#### Create circuit
Create a circuit on an oracle.

`function circuit_create(bytes32 circuit_key, address oracle) public`

* The address which sends this message will become the owner of this circuit.

| name | type | detail |
| :-- | :-- | :-- |
| circuit_key | `bytes32` | The keccak256 hash of the circuit |
| oracle | `address` | The address of the oracle |

#### Remove circuit
Remove a circuit from an oracle.

`function circuit_remove(bytes32 circuit_key, address oracle) public`

* This function can only be called by the owner of the circuit.

| name | type | detail |
| :-- | :-- | :-- |
| circuit_key | `bytes32` | The keccak256 hash of the circuit |
| oracle | `address` | The address of the oracle |

### Computation

#### Compute Request
Request an oracle to compute a circuit based on secrets.

`function compute_request(bytes32 circuit_hash, byte32[] secret_keys, uint32[] public_input, address oracle) public returns (bytes32)`

| name | type | detail |
| :-- | :-- | :-- |
| circuit_key | `bytes32` | The keccak256 hash of the circuit |
| secret_keys | `bytes32[]` | The keccak256 hashes of the secrets |
| oracle | `address` | The address of oracle |

##### Return

| type | detail |
| :-- | :-- |
| `bytes32` | The request key |

#### Compute Reply

`function compute_reply(byte32 request_key, bytes result, bytes proof) public`

| name | type | detail |
| :-- | :-- | :-- |
| request_key | `bytes32` | The request key |
| result | `bytes` | The result |
| proof | `bytes` | The zero knowledge proof |

<!--
### Return values

| name | detail |
| :-- | :-- |
| SUCCESS | The operation successfully |
| EACCESS |  |

##### Return

| type | detail |
| :-- | :-- |
| `uint8` | Success or not |
-->
