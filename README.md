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

##### Parameters

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

`function secret_create(string secret_key, byte32 secret_hash, address oracle, bytes proof) public`

* The address which sends this message will become the owner of this secret.

##### Parameters

| name | type | detail |
| :-- | :-- | :-- |
| secret_key | `string` | The key to access the encrypted secret |
| secret_hash | `bytes32` | The hash of the secret |
| oracle | `address` | The address of the oracle |
| proof | `bytes` | The zero knowledge proof of the encryption |

#### Remove secret
Remove a secret from an oracle.

`function secret_remove(bytes32 secret_hash, address oracle) public`

* This function can only be called by the owner of the secret.

##### Parameters

| name | type | detail |
| :-- | :-- | :-- |
| secret_hash | `bytes32` | The hash of the secret |
| oracle | `address` | The address of the oracle |

#### Grant access
Grant access of a secret for an user on an oracle.

`function secret_grant_user(bytes32 secret_hash, address user, address oracle) public`

* This function can only be called by the owner of the secret.

##### Parameters

| name | type | detail |
| :-- | :-- | :-- |
| secret_hash | `bytes32` | The hash of the secret |
| user | `address` | The address of granted user |
| oracle | `address` | The address of granted oracle |

### Circuit

#### Create circuit
Create a circuit on an oracle.

`function circuit_create(string circuit_key, byte32 circuit_hash, address oracle) public`

* The address which sends this message will become the owner of this circuit.

##### Parameters

| name | type | detail |
| :-- | :-- | :-- |
| circuit_key | `string` | The key to access the encrypted circuit |
| circuit_hash | `bytes32` | The hash of the circuit |
| oracle | `address` | The address of the oracle |

#### Remove circuit
Remove a circuit from an oracle.

`function circuit_remove(bytes32 circuit_hash, address oracle) public`

* This function can only be called by the owner of the circuit.

##### Parameters

| name | type | detail |
| :-- | :-- | :-- |
| circuit_hash | `bytes32` | The hash of the circuit |
| oracle | `address` | The address of the oracle |

### Computation

#### Computation Request
Request an oracle to compute a circuit based on secrets.

`function computation_request(bytes32 circuit_hash, byte32[] secret_hashes, uint32[] public_inputs, address oracle) public returns (bytes32)`

##### Parameters

| name | type | detail |
| :-- | :-- | :-- |
| circuit_hash | `bytes32` | The hash of the circuit |
| secret_hashes | `bytes32[]` | The hashes of the secrets |
| public_inputs | `uint32[]` | The public inputs |
| oracle | `address` | The address of oracle |

##### Return Value

| type | detail |
| :-- | :-- |
| `bytes32` | The request key |

#### Computation Reply

`function computation_reply(byte32 request_key, string result_key, byte32 result_hash, bytes proof) public`

##### Parameters

| name | type | detail |
| :-- | :-- | :-- |
| request_key | `bytes32` | The request key |
| result_key | `string` | The key to access the encrypted result |
| result_hash | `bytes32` | The hash of the result |
| proof | `bytes` | The zero knowledge proof |

<!--
### Return values

| name | detail |
| :-- | :-- |
| SUCCESS | The operation successfully |
| EACCESS |  |

##### Return Value

| type | detail |
| :-- | :-- |
| `uint8` | Success or not |
-->
