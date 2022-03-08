## interview questions for solidity
- https://eattheblocks.com/the-ultimate-collection-of-solidity-interview-questions/
### Modifiers(Decorators)
type|without|with
--------------------|-----------|-----
```Access Control```|```function protectedFunction() external {```<br>```....require(msg.sender == admin, 'only admin');```<br>```....~~~```<br>```}```|```function protectedFunction() external onlyAdmin() {```<br>```....~~~```<br>```}```<br><br>```modifier onlyAdmin() {```<br>```....require(msg.sender == admin, 'only admin');```<br>```...._;```<br>```}```
## Old vs. New
0.4+|0.8+
----|---
```constructor () public {}```|*```constructor () {}``` no visibility(here, public) needed because constructor only called one time when it created.*
```function () public payable {}```|*```fallback() external payable {}``` when no other function matches (not even the receive function). Optionally payable.<br>```receive() external payable {}``` for empty calldata (and any value)*
```sha3```|```keccak256```
```block.blockhash```|```blockhash```
```msg.gas```|```gasleft```
```suicide```|```selfdestruct```
```now```|```block.timestamp```
```uint(address(this))```|```function addr2uint(address a) internal pure returns (uint256) {```<br>```....return uint256(uint160(a));```<br>```}```
```msg.sender.send(amount)```|```payable(msg.sender).send(amount)```
```this.balance```|```address(this).balance```
```uint(-1)```|```type(uint).max```
event:```Transfer(...)```|```emit Transfer(...)```
```chainid```|```chainid()```
## Concepts
### Variable Type
type|expression|description
----|----------|------------
```state```|*aka. **contract member variables**, traits as below <br>1. declared inside a contract<br>2. stored permanently in blockchain storage<br>3. expensive gas operation<br><br>```contract SolidityTest {```<br>```....uint stateData;      // State variable```<br>```....constructor() public {```<br>```........stateData = 40;   // Using State variable```<br>```....}```<br>```}```*
}
```local```|**function variables**
```storage```|**what is storage variable? What's diff with state variables**
```public```|*public variables can be accessiblee from outside*
```private```|*private variables can't be accessble from outside, but it's not really private, all data on blockchain is public*
### Visibility
type|expression|description
----|----------|------------
```public```|*accessible from outside*
```private```|*inaccessible from outside*
```internal```|*prohibit inheritance*
```external```|*allow inheritance*
### Modifiers
type|expression|description
----|----------|------------
pure|
### data types - uint, address, strings
### container types - mapping, arrays
## Q & A
Q|A
---|-----
```state vs. local```|
```private vs. internal```|
```public vs. external```|
