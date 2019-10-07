# ZKOracle
An oracle framework with zero knowledge proof

## Features

* 

## Dependencies

* Truffle >=
* Solidity >=

## APIs
### Secret
#### Create secret

`function secret_create(bytes secret) public returns (bytes32)`

|name|type|detail|
|:--:|:--:|:--:|
| secret | bytes | The secret |
| return | bytes32 | `keccak256(secret)` |

#### Remove secret 

`function secret_remove(bytes32 secret_hash) public returns (uint8)`

* This function can only be called by the creator of the secret.

| name | type | detail |
| :--: | :--: | :--: |
| secret_hash | bytes32 | The hash of the secret |
| return | uint8 |  |

#### Grant access 

`function secret_grant(bytes32 secret_hash, address user) public returns (uint8)`

* This function can only be called by the creator of the secret.

| name | type | detail |
| :--: | :--: | :--: |
| secret_hash | bytes32 | The hash of the secret |
| user | address | The address of the granted user |
| return | uint8 | Success or not |

### Circuit
#### Create circuit 

`function circuit_create(bytes circuit) public returns (bytes32)`

| name | type | detail |
| :--: | :--: | :--: |
| circuit | bytes | The circuit |
| return | bytes32 | `keccak256(circuit)` |

#### Remove circuit 

`function circuit_remove(bytes32 circuit_hash) public returns (uint8)`

* This function can only be called by the creator of the circuit.

| name | type | detail |
| :--: | :--: | :--: |
| circuit_hash | bytes32 | The hash of the circuit |
| return | uint8 | Success or not |

#### Grant access 

`function circuit_grant(bytes32 secret_hash, address user) public returns (uint8)`

* This function can only be called by the creator of the circuit.

| name | type | detail |
| :--: | :--: | :--: |
| circuit_hash | bytes32 | The hash of the circuit |
| user | address | The address of the granted user |
| return | uint8 | Success or not |

### Return value

| name | detail |
| :--: | :--: |
| SUCCESS | The operation successfully |
| EACCESS |  |
