Great! You've created your NFT, but it's only available to other people as long as you have your IPFS node running. 
If you shut down your computer or you lose your internet connection, then no one else will be able to view your NFT! 
To get around this issue, you should pin it to a pinning service.
### RUN
```
git clone https://github.com/yusefnapora/minty
cd minty
npm install
npm link
./start-local-environment.sh
minty deploy
touch ~/flight-to-the-moon.txt
>>>
THE INTERPLANETARY TRAVEL COMPANY
---------------------------------
Departing: Cape Canaveral, Earth
Arriving: Base 314, The Moon
Boarding time: 17:30 UTC
Seat number: 1A
Baggage allowance: 5kg 

minty mint ~/flight-to-the-moon.txt --name "Moon Flight #1" --description "This ticket serves as proof-of-ownership of a first-class seat on a flight to the moon."

> 🌿 Minted a new NFT:
> Token ID:              1
> Metadata URI:          ipfs://bafybeic3ui4dj5dzsvqeiqbxjgg3fjmfmiinb3iyd2trixj2voe4jtefgq/metadata.json
> Metadata Gateway URL:  http://localhost:8080/ipfs/bafybeic3ui4dj5dzsvqeiqbxjgg3fjmfmiinb3iyd2trixj2voe4jtefgq/metadata.json
> Asset URI:             ipfs://bafybeihhii26gwp4w7b7w7d57nuuqeexau4pnnhrmckikaukjuei2dl3fq/flight-to-the-moon.txt
> Asset Gateway URL:     http://localhost:8080/ipfs/bafybeihhii26gwp4w7b7w7d57nuuqeexau4pnnhrmckikaukjuei2dl3fq/flight-to-the-moon.txt
> NFT Metadata:
> {
>   "name": "Moon Flight #1",
>   "description": "This ticket serves as proof-of-ownership of a first-class seat on a flight to the moon.",
>   "image": "ipfs://bafybeihhii26gwp4w7b7w7d57nuuqeexau4pnnhrmckikaukjuei2dl3fq/flight-to-the-moon.txt"
> }
```
### PIN for Speed
```
cd github.com/yusefnapora/minty
cp config/pinata.env.example config/.env
vim config/.env
>>>
PINNING_SERVICE_KEY="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySW5mb3JtYXRpb24iOnsia..."


```
