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
## [Grammar](https://docs.soliditylang.org/en/latest/grammar.html)
### Variable Type
type|expression|description
----|----------|------------
```state```|*aka. **contract member variables**, traits as below <br>1. declared inside a contract<br>2. stored permanently in blockchain storage<br>3. expensive gas operation<br><br>```contract SolidityTest {```<br>```....uint stateData;      // State variable```<br>```....constructor() public {```<br>```........stateData = 40;   // Using State variable```<br>```....}```<br>```}```*
}
```local```|**function variables**
```storage```|**what is storage variable? What's diff with state variables**
```public```|*public variables can be accessiblee from outside*
```private```|*private variables can't be accessble from outside, but it's not really private, all data on blockchain is public*
### [Global Variables](https://docs.soliditylang.org/en/latest/cheatsheet.html#global-variables)
### [Visibility](https://docs.soliditylang.org/en/latest/cheatsheet.html#function-visibility-specifiers)
type|expression|description
----|----------|------------
```public```|*accessible from outside*
```private```|*inaccessible from outside*
```internal```|*prohibit inheritance*
```external```|*allow inheritance*
### [Modifiers](https://docs.soliditylang.org/en/latest/cheatsheet.html#modifiers)
type|applied to|description
----|----------|--
```pure```|```function```|***Disallow** modification or access of state*
```view```|```function```|***Disallow** modification of state*
```payable```|```function```|***Allows** them to receive Ether together with a call*
```constant```|```state variable```|***Disallows** assignment (except initialisation), **does not occupy storage slot.***
```immutable```|```state variable```|*Allows exactly one assignment at construction time and is constant afterwards. **Is stored in code. What's diff? constant vs. immutable***
```anonymous```|```for events:```|***Does not** store event signature as topic.*
```indexed```|```for event parameters:```|*Stores the parameter as topic.*
```virtual```|```for functions and modifiers:```|***Allows** the function’s or modifier’s behaviour **to be changed in derived contracts.***
```override```|```function, modifier or public state variable```| *changes the behaviour of a function or modifier in a **base contract**. **virtual vs. override***
### data types - uint, address, strings
type|expl.
----|---
```fixed sized array```|```bytes1, bytes2, bytes3, …, bytes32```*If x is of type bytesI, then x[k] for 0 <= k < I returns the k th byte (read-only).*
```dynamic-sized array```|```bytes``` & ```string```

### container types - mapping, arrays
## Q & A
Q|A
---|-----
```state vs. local```|*it depends where it is defined.*
```local variable can be public?```|```state can be public or private```
```private vs. internal```|
```public vs. external```|
```constant vs. immutable```|
```virtual vs. override```|
```type(C).creationCode vs. type(C).runtimeCode```|
```string vs. string memory```|
```bytes vs. bytes memory```|
```address -> address payable```|
```this -> address```|
```this -> address payable```|
```addr.send vs. addr.transfer```|*this -> addr, where this is contract addr.* 
```floating point vs. fixed point```
```storage vs. memory```|```bytes memory a;``` vs. ```bytes storage a;```
```call```vs.<br>```delegatecall```vs.<br>```staticcall```<br>|```(bool success, bytes memory returnData) = address(nameReg).call(payload);```
```abi.encode```vs.<br>```abi.encodePacked```vs.<br>```abi.encodeWithSelector```vs.<br>```abi.encodeWithSignature```|```bytes memory payload = abi.encodeWithSignature("register(string)", "MyName");```
```byte[] vs bytes```
[assert vs. require](https://docs.soliditylang.org/en/latest/control-structures.html#panic-via-assert-and-error-via-require)|
### [Storage vs. Memory](https://docs.soliditylang.org/en/latest/internals/layout_in_memory.html#differences-to-layout-in-storage)
type|storage|memory
----|-------|-----
```uint8[4] a;```|```32byte(8*4)```|```128byte(32*4)```
```struct S {```<br>....```uint a;```<br>....```uint b;```<br>....```uint8 c;```<br>....```uint8 d;``````}```|```96byte(32*2+32)```|128byte(32*4)


