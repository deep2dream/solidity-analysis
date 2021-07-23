- https://asvin.io/develop-test-and-deploy-your-first-ethereum-smart-contract/
### follow the steps
- node
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
nvm install 12.18.1
```
- truffle
```
npm install -g truffle
```
- Ganache cli
```
npm install -g ganache-cli
```
- helloworld
```
git clone https://github.com/b-rohit/hello-world-smart-contract.git 
cd dapp-hello-world

[run.]
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
