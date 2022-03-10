what|how
----|----
```address payable``` 2 ```address```|
```address``` 2 ```address payable```|
```uint160 2 ```address```|
```bytes``` 2 ```address```|

*uint==uint256, bytes==byte[]?*

- https://docs.soliditylang.org/en/v0.5.4/types.html#explicit-conversions

### Truncation & Padding
where|from|to
-----|----|-------
```bytes4``` 2 ```bytes2```|```0x12345678```|```0x1234```
```uint32``` 2 ```uint16```|```0x12345678```|```0x5678```
```bytes2``` 2 ```bytes4```|```0x1234```|```0x12340000```
```uint16``` 2 ```uint32```|```0x1234```|```0x00001234```
```pure``` 2 ```view & non-payable```|
```view```2 ```non-payable ```|
```payable```2 ```non-payable``` |