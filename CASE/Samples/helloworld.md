- https://asvin.io/develop-test-and-deploy-your-first-ethereum-smart-contract/
### Install
tool|cmd
----|----
```nvm(nodejs)```|```curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh \| bash```<br>```nvm install 12.18.1```
```truffle```|```npm install -g truffle```
```ganache cli```|```npm install -g ganache-cli```
```helloworld```|```git clone https://github.com/b-rohit/hello-world-smart-contract.git```<br>```cd dapp-hello-world```
### Run
```
ganache-cli
truffle console
> compile
> migrate

[interactive]
truffle develop
> compile
> migrate

[truffle.functions]
truffle test
truffle compile

[test.contracts]
$ truffle console
truffle(develop)> compile
truffle(develop)> migrate
truffle(development)> let instance = await MyStatus.deployed()
truffle(development)> await instance.getStatus()
truffle(development)> await instance.setStatus("Available")
```
