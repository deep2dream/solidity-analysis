## interview questions for solidity
- https://eattheblocks.com/the-ultimate-collection-of-solidity-interview-questions/
### Access Control
- with modifier
```solidity
  function protectedFunction() external onlyAdmin() {
    ...
  }

  modifier onlyAdmin() {
    require(msg.sender == admin, 'only admin');
    _;
  }
```
- without modifier
```solidity
  function protectedFunction() external {
    require(msg.sender == admin, 'only admin');
    ...
  }
```
### state variables vs. local variables
```
[state variables]
public variables vs. private variables

[private variables]
private variables not really private, all data on blockchain is public
```
### data types - uint, address, strings
### container types - mapping, arrays
### private vs. internal
### public vs. external
