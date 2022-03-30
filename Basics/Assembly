- https://docs.soliditylang.org/en/latest/assembly.html
- https://www.geeksforgeeks.org/solidity-assembly/
- https://docs.soliditylang.org/en/v0.5.4/assembly.html#solidity-assembly
### syntax
type|expr.
---|----
```default```|```assembly {}```
```memory safe```|```assembly ("memory-safe") {}```
```functional-style opcodes```| ```mul(1, add(2, 3))```
```assembly-local variables```| ```let x := add(2, 3)  let y := mload(0x40)  x := add(x, y)```
```access to external variables```| ```function f(uint x) public { assembly { x := sub(x, 1) } }```
```loops```| ```for { let i := 0 } lt(i, x) { i := add(i, 1) } { y := mul(2, y) }```
```if statements```| ```if slt(x, 0) { x := sub(0, x) }```
```switch statements```| ```switch x case 0 { y := mul(x, 2) } default { y := 0 }```
```function calls```| ```function f(x) -> y { switch x case 0 { y := 1 } default { y := mul(x, f(sub(x, 1))) }   }```
***variable***|
```allocate```|***```let c := add(a, 16)```=```c = a+16```, where c is avalue, not a pointer and a is function input```uint a```***<br>```let d := add(sload(c), 12)```
```deallocate```|*```b := d```<br>```b := add(b, c)```, if you use sload(c), it exists. if not, it's deallocated when inferred in ```add(b,c)```?*
```allocate memory```|*```mstore(0x80, c)```, save c at 0x80*
### func.
func.|expl.
---|----
```let size := extcodesize(_addr)```|*return size of code at address*
```extcodecopy(_addr, add(code, 0x20), 0, size)```
```code = new bytes(size)```|[*equals to *``` code := mload(0x40)```?](https://ethereum.stackexchange.com/questions/9603/understanding-mload-assembly-function) [Read this](https://ethereum.stackexchange.com/questions/9603/understanding-mload-assembly-function)*, different explanation. first ```new bytes(x)``` write it from 0x40?* ->*In solidity, the 0x40 slot in memory is special: it contains the "free memory pointer" which points to the end of the currently allocated memory. When you use inline assembly, you should load the data stored at 0x40 and then only write to addresses after the result. When you're done, if you want to keep that memory allocated, you should overwrite 0x40 with the new value of the free memory pointer.*
**explain with example1**
```sum += _data[i]```|***```sum := add(sum, mload(add(add(_data, 0x20), mul(i, 0x20))))```, where ```uint[] memory _data,uint sume```***
```let len := mload(_data)```|*Load the length (first 32 bytes)*
```let end := add(data, mul(len, 0x20))```|end of _data
```add(_data, 0x20)```|*```_data+0x20```, where _data is pointer value, mload(_data) contains lenth of _data, so skip the value.*
```mul(i, 0x20)```|```i*0x20```, where i is value
``` lt(data, end)```|```if data==end: break```, where data & end are both pointer value
```data := add(data, 0x20)```|```data+0x20```, where data is pointer value
```sum := add(sum, mload(data))```|```sum+*data```, where sum is value and data is pointer value
```r := mul(x, sload(b.slot))```|*, where ```uint b;```outside assembly*
```sload(b.slot)```|
```returndatasize()```|
```returndatacopy(0, 0, returndatasize())```|
```revert(0, returndatasize())```|```

### Q &A
Q|A
---|----
```mload(paddr) vs mstore(paddr,v)```|*where paddr means pointer address in memory. **mload** means read while mstore means **write**<br>```mstore(dest,mload(src))``` this syntax copy content of src to dest by 32byte(256bit) because ```uint dest, uint src``` - no more.*
```add(add(size, 0x20), 0x1f)```!=```add(size, 0x3f)```?|

### [Opcodes](https://docs.soliditylang.org/en/v0.5.4/assembly.html#opcodes)
Instruction|- |-|Explanation
-----------|-|-|-----
stop|-|F|stop execution, identical to return(0,0)
add(x, y)| |F|x + y
sub(x, y)| |F|x - y
mul(x, y)| |F|x * y
div(x, y)| |F|x / y
sdiv(x, y)| |F|x / y, for signed numbers in two’s complement
mod(x, y)| |F|x % y
smod(x, y)| |F|x % y, for signed numbers in two’s complement
exp(x, y)| |F|x to the power of y
not(x)| |F|~x, every bit of x is negated
lt(x, y)| |F|1 if x < y, 0 otherwise
gt(x, y)| |F|1 if x > y, 0 otherwise
slt(x, y)| |F|1 if x < y, 0 otherwise, for signed numbers in two’s complement
sgt(x, y)| |F|1 if x > y, 0 otherwise, for signed numbers in two’s complement
eq(x, y)| |F|1 if x == y, 0 otherwise
iszero(x)| |F|1 if x == 0, 0 otherwise
and(x, y)| |F|bitwise and of x and y
or(x, y)| |F|bitwise or of x and y
xor(x, y)| |F|bitwise xor of x and y
byte(n, x)| |F|nth byte of x, where the most significant byte is the 0th byte
shl(x, y)| |C|logical shift left y by x bits
shr(x, y)| |C|logical shift right y by x bits
sar(x, y)| |C|arithmetic shift right y by x bits
addmod(x, y, m)| |F|(x + y) % m with arbitrary precision arithmetic
mulmod(x, y, m)| |F|(x * y) % m with arbitrary precision arithmetic
signextend(i, x)| |F|sign extend from (i*8+7)th bit counting from least significant
keccak256(p, n)| |F|keccak(mem[p…(p+n)))
jump(label)|-|F|jump to label / code position
jumpi(label, cond)|-|F|jump to label if cond is nonzero
pc| |F|current position in code
pop(x)|-|F|remove the element pushed by x
dup1 … dup16| |F|copy nth stack slot to the top (counting from top)
swap1 … swap16|*|F|swap topmost and nth stack slot below it
mload(p)| |F|mem[p…(p+32))
mstore(p, v)|-|F|mem[p…(p+32)) := v
mstore8(p, v)|-|F|mem[p] := v & 0xff (only modifies a single byte)
sload(p)| |F|storage[p]
sstore(p, v)|-|F|storage[p] := v
msize| |F|size of memory, i.e. largest accessed memory index
gas| |F|gas still available to execution
address| |F|address of the current contract / execution context
balance(a)| |F|wei balance at address a
caller| |F|call sender (excluding delegatecall)
callvalue| |F|wei sent together with the current call
calldataload(p)| |F|call data starting from position p (32 bytes)
calldatasize| |F|size of call data in bytes
calldatacopy(t, f, s)|-|F|copy s bytes from calldata at position f to mem at position t
codesize| |F|size of the code of the current contract / execution context
codecopy(t, f, s)|-|F|copy s bytes from code at position f to mem at position t
extcodesize(a)| |F|size of the code at address a
extcodecopy(a, t, f, s)|-|F|like codecopy(t, f, s) but take code at address a
returndatasize| |B|size of the last returndata
returndatacopy(t, f, s)|-|B|copy s bytes from returndata at position f to mem at position t
extcodehash(a)| |C|code hash of address a
create(v, p, n)| |F|create new contract with code mem[p…(p+n)) and send v wei and return the new address
create2(v, p, n, s)| |C|create new contract with code mem[p…(p+n)) at address keccak256(0xff . this . s . keccak256(mem[p…(p+n))) and send v wei and return the new address, where 0xff is a 8 byte value, this is the current contract’s address as a 20 byte value and s is a big-endian 256-bit value
call(g, a, v, in, insize, out, outsize)| |F|call contract at address a with input mem[in…(in+insize)) providing g gas and v wei and output area mem[out…(out+outsize)) returning 0 on error (eg. out of gas) and 1 on success
callcode(g, a, v, in, insize, out, outsize)| |F|identical to call but only use the code from a and stay in the context of the current contract otherwise
delegatecall(g, a, in, insize, out, outsize)| |H|identical to callcode but also keep caller and callvalue
staticcall(g, a, in, insize, out, outsize)| |B|identical to call(g, a, 0, in, insize, out, outsize) but do not allow state modifications
return(p, s)|-|F|end execution, return data mem[p…(p+s))
revert(p, s)|-|B|end execution, revert state changes, return data mem[p…(p+s))
selfdestruct(a)|-|F|end execution, destroy current contract and send funds to a
invalid|-|F|end execution with invalid instruction
log0(p, s)|-|F|log without topics and data mem[p…(p+s))
log1(p, s, t1)|-|F|log with topic t1 and data mem[p…(p+s))
log2(p, s, t1, t2)|-|F|log with topics t1, t2 and data mem[p…(p+s))
log3(p, s, t1, t2, t3)|-|F|log with topics t1, t2, t3 and data mem[p…(p+s))
log4(p, s, t1, t2, t3, t4)|-|F|log with topics t1, t2, t3, t4 and data mem[p…(p+s))
origin| |F|transaction sender
gasprice| |F|gas price of the transaction
blockhash(b)| |F|hash of block nr b - only for last 256 blocks excluding current
coinbase| |F|current mining beneficiary
timestamp| |F|timestamp of the current block in seconds since the epoch
number| |F|current block number
difficulty| |F|difficulty of the current block
gaslimit| |F|block gas limit of the current block