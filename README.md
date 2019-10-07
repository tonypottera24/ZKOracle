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

> Note: 
> * The address which sends this message all will become the owner of this oracle.

| name | type | detail |
| :-- | :-- | :-- |
| TEE | `bool` | The oracle use trusted execution environment |
| MPC | `bool` | The oracle use multi-party computation |

#### Unregister
Unregister from the oracle list and return the deposits.

`function oracle_unregister() public`

> Note: 
> * Only the owner of the oracle can unregister itself.
> * User cannot sending any computation request after oracle unregistered.
> * The locked deposits will only be returned after user remove the secret.

| name | type | detail |
| :-- | :-- | :-- |

### Secret

#### Save secret
Save a secret into oracles.

`function secret_save(bytes secret, address oracle, bytes proof) public`

| name | type | detail |
| :-- | :-- | :-- |
| secret | `bytes` | The encrypted secret |
| oracle | `address` | The address of the oracle |
| proof | `bytes` | The zero knowledge proof of the encryption |

#### Delete secret
Delete a secret from oracles.

`function secret_delete(bytes32 secret_hash, address oracle) public`

* This function can only be called by the saver of the secret.

| name | type | detail |
| :-- | :-- | :-- |
| secret_hash | `bytes32` | The hash of the secret |
| oracle | `address` | The address of the oracle |

#### Grant access
Grant access of a secret for an user to an oracle.

`function secret_grant_user(bytes32 secret_hash, address user, address oracle) public`

* This function can only be called by the creator of the secret.

| name | type | detail |
| :-- | :-- | :-- |
| secret_hash | `bytes32` | The hash of secret |
| user | `address` | The address of granted user |
| oracle | `address` | The address of granted oracle |

### Circuit

#### Create circuit
Create circuit.

`function circuit_create(bytes circuit) public`

| name | type | detail |
| :-- | :-- | :-- |
| circuit | `bytes` | The circuit |

#### Remove circuit
Remove circuit.

`function circuit_remove(bytes32 circuit_hash) public`

* This function can only be called by the creator of the circuit.

| name | type | detail |
| :-- | :-- | :-- |
| circuit_hash | `bytes32` | The hash of the circuit |

### Compute

#### Compute Request
Request an oracle to compute a circuit based on secrets.

`function compute_request(bytes32 circuit_hash, byte32[] secret_hashes, address oracle) public`

| name | type | detail |
| :-- | :-- | :-- |
| circuit_hash | `bytes32` | The hash of the circuit |
| secret_hashes | `byte32[]` | The array of secret hashes |
| oracle | `address` | The address of oracle |

#### Compute Reply

`function compute_reply(bytes32 circuit_hash, byte32[] secret_hashes, address user, bytes proof, bytes result) public returns (uint8)`

| name | type | detail |
| :-- | :-- | :-- |
| circuit_hash | `bytes32` | The hash of the circuit |
| secret_hashes | `byte32[]` | The array of secret hashes |
| user | `address` | The address of user |
| proof | `bytes` | The zero knowledge proof |
| result | `bytes` | The results |

##### Return

| type | detail |
| :-- | :-- |
| `uint8` | Success or not |

### Return values

| name | detail |
| :-- | :-- |
| SUCCESS | The operation successfully |
| EACCESS |  |
