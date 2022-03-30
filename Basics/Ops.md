- https://docs.soliditylang.org/en/v0.5.4/types.html

case|expl.
---|----
```0**0```|```1```
```~int256(0)```|```int256(-1)```
```-x```|```(T(0) - x)``` 
```uint256(0) - uint256(1)```|```2**256 - 1```
```x << y```|```x * 2**y```
```-x << y```|```?```
```-x >> y```|```?```
```int x = -2**255;```|```assert(-x == x);```*This means that even if a number is negative, you cannot assume that its negation will be positive.*
```-a / n```|```-(abs(a)/n)```
```a % -n```|```a % n)```?
```-a % n```|```-(abs(a) % n)```