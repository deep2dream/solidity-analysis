## interview questions for solidity
- https://eattheblocks.com/the-ultimate-collection-of-solidity-interview-questions/
### Modifiers(Decorators)
type|without|with
--------------------|-----------|-----
```Access Control```|```function protectedFunction() external {```<br>```....require(msg.sender == admin, 'only admin');```<br>```....~~~```<br>```}```|```function protectedFunction() external onlyAdmin() {```<br>```....~~~```<br>```}```<br><br>```modifier onlyAdmin() {```<br>```....require(msg.sender == admin, 'only admin');```<br>```...._;```<br>```}```

## Concepts
### Variable Type
type|expression|description
----|----------|------------
```state```|
```local```|
```public```|
```private```|**private variables not really private, all data on blockchain is public*
```internal```|
```external```|
### data types - uint, address, strings
### container types - mapping, arrays
## Q & A
Q|A
---|-----
```state vs. local```|
```private vs. internal```|
```public vs. external```|
