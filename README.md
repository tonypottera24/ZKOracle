# ZKOracle
An oracle framework with zero knowledge proof

## Features

* 

## Dependencies

* Truffle >=
* Solidity >=

## Usages

### Secret

#### Create secret

`function secret_create(bytes secret, address[] oracle) public returns (uint8, bytes32)`

| name | type | detail |
| :--: | :--: | :--: |
| secret | `bytes` | The secret |
| oracle | `address[]` | The address of the granted oracle |

##### Return

| type | detail |
| :--: | :--: |
| `uint8` | errno |
| `bytes32` | `keccak256(secret)` |

#### Remove secret 

`function secret_remove(bytes32 secret_hash, address[] oracle) public returns (uint8)`

* This function can only be called by the creator of the secret.

| name | type | detail |
| :--: | :--: | :--: |
| secret_hash | `bytes32` | The hash of the secret |
| oracle | `address[]` | The address of the granted oracle |

##### Return

| type | detail |
| :--: | :--: |
| `uint8` | errno |

#### Grant access

`function secret_grant_user(bytes32 secret_hash, address[] user, address[] oracle) public returns (uint8)`

* This function can only be called by the creator of the secret.

| name | type | detail |
| :--: | :--: | :--: |
| secret_hash | `bytes32` | The hash of the secret |
| user | `address[]` | The address of the granted user |
| oracle | `address[]` | The address of the granted oracle |

##### Return

| type | detail |
| :--: | :--: |
| `uint8` | errno |

### Circuit

#### Create circuit 

`function circuit_create(bytes circuit) public returns (uint8, bytes32)`

| name | type | detail |
| :--: | :--: | :--: |
| circuit | `bytes` | The circuit |

##### Return

| type | detail |
| :--: | :--: |
| `uint8` | errno |
| `bytes32` | `keccak256(circuit)` |

#### Remove circuit 

`function circuit_remove(bytes32 circuit_hash) public returns (uint8)`

* This function can only be called by the creator of the circuit.

| name | type | detail |
| :--: | :--: | :--: |
| circuit_hash | `bytes32` | The hash of the circuit |

##### Return

| type | detail |
| :--: | :--: |
| `uint8` | errno |

### Compute

#### Compute

`function compute(bytes32 circuit_hash, byte32[] secret_hashes) public returns (uint8)`

| name | type | detail |
| :--: | :--: | :--: |
| circuit_hash | `bytes32` | The hash of the circuit |
| secret_hashes | `byte32[]` | The array of secret hashes |

##### Return

| type | detail |
| :--: | :--: |
| `uint8` | Success or not |

### Oracle

#### Register

`function oracle_register() public returns (uint8)`

| name | type | detail |
| :--: | :--: | :--: |

##### Return

| type | detail |
| :--: | :--: |
| `uint8` | errno |

#### Retire

`function oracle_retire() public returns (uint8)`

| name | type | detail |
| :--: | :--: | :--: |

##### Return

| type | detail |
| :--: | :--: |
| `uint8` | errno |

### Return values

| name | detail |
| :--: | :--: |
| SUCCESS | The operation successfully |
| EACCESS |  |
