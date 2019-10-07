# ZKOracle
An oracle framework with zero knowledge proof

## Features

* 

## Dependencies

* Truffle

## APIs
### Secret
#### Create secret

`function secret_create(bytes secret) public returns (bytes32)`

|name|type|detail|
|:--:|:--:|:--:|
| secret | bytes | The secret |
| return | bytes32 | `keccak256(secret)` |

#### Remove secret 

`function secret_remove(bytes32 secret_hash) public returns (bool)`

* This function can only be called by the creator of the secret.

| name | type | detail |
| :--: | :--: | :--: |
| secret_hash | bytes32 | The hash of the secret |
| return | bool | Success or not |

#### Grant access 

`function secret_grant(bytes32 secret_hash, address user) public returns (bool)`

* This function can only be called by the creator of the secret.

| name | type | detail |
| :--: | :--: | :--: |
| secret_hash | bytes32 | The hash of the secret |
| user | address | The address of the granted user |
| return | bool | Success or not |

### Circuit
#### Create circuit 

`function circuit_create() public`

| name | type | detail |
| :--: | :--: | :--: |

#### Remove circuit 

`function circuit_remove(bytes32 circuit_hash) public returns (bool)`

* This function can only be called by the creator of the circuit.

| name | type | detail |
| :--: | :--: | :--: |
| circuit_hash | bytes32 | The hash of the circuit |
| return | bool | Success or not |

#### Grant access 

`function circuit_grant(bytes32 secret_hash, address user) public returns (bool)`

* This function can only be called by the creator of the circuit.

| name | type | detail |
| :--: | :--: | :--: |
| circuit_hash | bytes32 | The hash of the circuit |
| user | address | The address of the granted user |
| return | bool | Success or not |
