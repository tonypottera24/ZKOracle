# ZKOracle
An oracle framework with zero knowledge proof

## Features

* 

## APIs
### Secret
* Create secret

`function secret_create(secret, ) public returns ()`

|args|detail|
|:--:|:--:|
|secret|encrypted secret|

return: `hash(secret)`

* Remove secret 

`function secret_remove() public`

|arg|detail|
|:--:|:--:|

#### Priviledge
* Grant access 

`function secret_grant() public`

|arg|detail|
|:--:|:--:|

### Circuit
* Create circuit 

`function circuit_create() public`

|arg|detail|
|:--:|:--:|

* Remove circuit 

`function circuit_remove() public`

|arg|detail|
|:--:|:--:|

#### Priviledge
* Grant access 

`function circuit_grant() public`

|arg|detail|
|:--:|:--:|
