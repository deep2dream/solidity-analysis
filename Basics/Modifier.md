- https://docs.soliditylang.org/en/v0.5.4/structure-of-a-contract.html#function-modifiers

what|how
---|----
```definition```|```modifier onlyOwner() { ```<br>....```require(msg.sender == owner,"Only owner can call this.");```<br>....```_;```<br>```}```
```usage```|```function abort() public view onlyOwner { // Modifier usage// ...}```