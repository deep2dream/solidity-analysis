- https://applicature.com/blog/blockchain-technology/solidity-interview
- https://i6mi6.medium.com/the-ultimate-collection-of-ethereum-solidity-and-smart-contracts-interview-questions-ef610d250012

### send functions
method|issue
---|---
```(bool sent, ) = msg.sender.call{value: address(this).balance}("");```|vulnerable to selfdestruct call from Attack contract
```(bool sent, ) = msg.sender.call{value: balance}("");```|yes
```msg.sender.send()```|
```msg.sender.tranfer()```|
### All in One
Q|A
----|----
Once contract A is selfdestructed, then you can't access it any more?|
Can contract B call selfdestruct call of A?|