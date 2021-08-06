- https://github.com/ipfs/awesome-ipfs
### browsers enabled
- https://brave.com/
```
sudo apt install apt-transport-https curl
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list
sudo apt update
sudo apt install brave-browser
```
### storage
- https://app.pinata.cloud/pinmanager
```
https://app.pinata.cloud/keys
[API-KEY]
API Key
7b0f993f4fbaf0fcd799

API Secret
020abddc2d136bc633c22b06e45b439057b9e77d6f7afa923eb912f498564d62

JWT
(Secret access token)
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySW5mb3JtYXRpb24iOnsiaWQiOiJiYmQ1NDU4MS03MDhmLTRjMWEtYTJhZS04NjI5NzgyNDdiYjYiLCJlbWFpbCI6Imdhb2p1bnlpbmdAeWFuZGV4LmNvbSIsImVtYWlsX3ZlcmlmaWVkIjp0cnVlLCJwaW5fcG9saWN5Ijp7InJlZ2lvbnMiOlt7ImlkIjoiTllDMSIsImRlc2lyZWRSZXBsaWNhdGlvbkNvdW50IjoxfV0sInZlcnNpb24iOjF9LCJtZmFfZW5hYmxlZCI6ZmFsc2V9LCJhdXRoZW50aWNhdGlvblR5cGUiOiJzY29wZWRLZXkiLCJzY29wZWRLZXlLZXkiOiI3YjBmOTkzZjRmYmFmMGZjZDc5OSIsInNjb3BlZEtleVNlY3JldCI6IjAyMGFiZGRjMmQxMzZiYzYzM2MyMmIwNmU0NWI0MzkwNTdiOWU3N2Q2ZjdhZmE5MjNlYjkxMmY0OTg1NjRkNjIiLCJpYXQiOjE2Mjc4OTYyODd9.pQvqJ9d7jWLzhh72PlCnWO7m0bYSwbQIMCl-bTNkT2s
```
- https://nft.storage/
# Content Market
- [access control](https://docs.openzeppelin.com/contracts/3.x/access-control)
- 
 typ. | short clip|low quality|
------|-----------|---
book  | marketing| none
picture| marketing|marketing
video | marketing|marketing
music | marketing|marketing
## [Why IPFS for NFT?](https://docs.ipfs.io/how-to/mint-nfts-with-ipfs/#how-ipfs-helps)

When an NFT is created and linked to a digital file that lives on some other system, how the data is linked is very important. There are a few reasons why traditional HTTP links aren't a great fit.

With an HTTP address like https://cloud-bucket.provider.com/my-nft.jpeg, anyone can fetch the contents of my-nft.jpeg, as long as the owner of the server pays their bills. However, there's **no way to guarantee that the contents of my-nft.jpeg are the same** as they were when the NFT was created. The server owner can easily replace my-nft.jpeg with something completely different at any time, causing the NFT to change its meaning.

This problem was demonstrated by an artist who pulled the rug (opens new window) on NFTs he created by changing their images after they were minted and sold to others.

IPFS solves this problem thanks to **Content Addressing**. Adding data to IPFS produces a **content identifier (CID)** that's directly **derived from** the data itself and **links to** the data in the IPFS network. Because a CID can only ever refer to one piece of content, we know that **nobody can replace or alter the content without breaking the link**.

Using the CID, *anyone can fetch a copy of the data* from the IPFS network *as long as at least one copy exists on the network*, even if the original provider has disappeared. This makes CIDs perfect for NFT storage. All we need to do is **put the CID into an ipfs:// URI** like ipfs://bafybeidlkqhddsjrdue7y3dy27pu5d7ydyemcls4z24szlyik3we7vqvam/nft-image.png, and we have an *immutable link* from the blockchain to the data for our token.

Of course, there may be some cases in which you do want to change the metadata for an NFT after it's been published. That's no problem! You'll just need to add support to your smart contract for updating the URI for a token after it's been issued. That will let you **change the URI to a new IPFS URI** while **still leaving a record of the initial version in the blockchain's transaction history**. This provides accountability and makes it clear to everyone what was changed, when, and by whom.
### Summary
1. Content Addressing for integrity
```
http://, you pay for the content, but no guarentee for its integrity. It can be replaced or altered by provider.
ipfs://, url is a immutable link with hash(content). The integrity is highly guarenteed.

hash(content), url
[upload]
$ ipfs add nft.jpg
>>>
added QmQ9YxmRtbs2dEppubBtb6rSUpX6ZTUbNPXpDt5EWXk7NT nft.jpg
 294.17 KiB / 294.17 KiB [====================================================================================================================================================================================================] 100.00%

[download]
$ ipfs cat /ipfs/hash(content)
$ wget https://ipfs.io/ipfs/hash(content)
ex:
ipfs cat /ipfs/QmQ9YxmRtbs2dEppubBtb6rSUpX6ZTUbNPXpDt5EWXk7NT > launch.jpg

```
2. Blockchain for accountability, tracing, copyright protection, pay-on-go
```
Tracing: you can change URI for NFT token. But it will be recorded in the blockchain
Accountability: 
Pay-on-Go: you will directly buy ownership or accessibility using blockchain & its cryptocurrency
```
3. TokenURI:=1:1


### [ipfs vs. filecoin](https://docs.ipfs.io/how-to/mint-nfts-with-ipfs/#a-short-introduction-to-nfts)

**Since IPFS isn't a blockchain**, we'll be leveraging the power of the Ethereum blockchain for this guide. However, the steps described here can just as easily be applied to other blockchains.
## ipfs.io
- https://ipfs.io/#install
- https://ipfs.io/#how
### install
- https://docs.ipfs.io/install/command-line/#official-distributions
- https://github.com/ipfs/go-ipfs
- https://docs.ipfs.io/how-to/command-line-quick-start
- https://www.quicknode.com/guides/solidity/how-to-create-and-deploy-an-erc-721-nft
```
wget https://dist.ipfs.io/go-ipfs/v0.9.0/go-ipfs_v0.9.0_linux-amd64.tar.gz
tar -xvzf go-ipfs_v0.9.0_linux-amd64.tar.gz
cd go-ipfs/
./install.sh
ipfs --version
```
### use
```
[init.node]
$ ipfs init
>>>
generating ED25519 keypair...done
peer identity: 12D3KooWBEu3MdyVwW3i49fspVWPUT5dANEj9ZxFNWU2rQSXAYwa
initializing IPFS node at /home/falcon/.ipfs
to get started, enter:

	ipfs cat /ipfs/QmQPeNsJPyVWPFDVHb77w8G42Fvo15z4bG2X8D2GhfbSXc/readme

$ ipfs cat /ipfs/QmQPeNsJPyVWPFDVHb77w8G42Fvo15z4bG2X8D2GhfbSXc/readme
>>>
Hello and Welcome to IPFS!

██╗██████╗ ███████╗███████╗
██║██╔══██╗██╔════╝██╔════╝
██║██████╔╝█████╗  ███████╗
██║██╔═══╝ ██╔══╝  ╚════██║
██║██║     ██║     ███████║
╚═╝╚═╝     ╚═╝     ╚══════╝

If you're seeing this, you have successfully installed
IPFS and are now interfacing with the ipfs merkledag!

 -------------------------------------------------------
| Warning:                                              |
|   This is alpha software. Use at your own discretion! |
|   Much is missing or lacking polish. There are bugs.  |
|   Not yet secure. Read the security notes for more.   |
 -------------------------------------------------------

Check out some of the other files in this directory:

  ./about
  ./help
  ./quick-start     <-- usage examples
  ./readme          <-- this file
  ./security-notes

$ ipfs cat /ipfs/QmQPeNsJPyVWPFDVHb77w8G42Fvo15z4bG2X8D2GhfbSXc/quick-start

$ ipfs daemon
>>>
Initializing daemon...
go-ipfs version: 0.9.0
Repo version: 11
System version: amd64/linux
Golang version: go1.16.5
2021/07/27 16:58:29 failed to sufficiently increase receive buffer size (was: 208 kiB, wanted: 2048 kiB, got: 416 kiB). See https://github.com/lucas-clemente/quic-go/wiki/UDP-Receive-Buffer-Size for details.
Swarm listening on /ip4/10.159.0.62/tcp/4001
Swarm listening on /ip4/10.159.0.62/udp/4001/quic
Swarm listening on /ip4/127.0.0.1/tcp/4001
Swarm listening on /ip4/127.0.0.1/udp/4001/quic
Swarm listening on /ip4/172.17.0.1/tcp/4001
Swarm listening on /ip4/172.17.0.1/udp/4001/quic
Swarm listening on /ip4/192.168.0.148/tcp/4001
Swarm listening on /ip4/192.168.0.148/udp/4001/quic
Swarm listening on /p2p-circuit
Swarm announcing /ip4/10.159.0.62/tcp/4001
Swarm announcing /ip4/10.159.0.62/udp/4001/quic
Swarm announcing /ip4/127.0.0.1/tcp/4001
Swarm announcing /ip4/127.0.0.1/udp/4001/quic
Swarm announcing /ip4/45.135.186.36/udp/4001/quic
API server listening on /ip4/127.0.0.1/tcp/5001
WebUI: http://127.0.0.1:5001/webui
Gateway (readonly) server listening on /ip4/127.0.0.1/tcp/8080
Daemon is ready

[upload]
$ ipfs add image-asset.jpeg
>>>
added QmQ9YxmRtbs2dEppubBtb6rSUpX6ZTUbNPXpDt5EWXk7NT image-asset.jpeg
 294.17 KiB / 294.17 KiB [====================================================================================================================================================================================================] 100.00%
 
$ wget https://ipfs.io/ipfs/QmQ9YxmRtbs2dEppubBtb6rSUpX6ZTUbNPXpDt5EWXk7NT

$ vim nft.json
>>>
{
    "name": "NFT Art",
    "description": "This image shows the true nature of NFT.",
    "image": "https://ipfs.io/ipfs/QmQ9YxmRtbs2dEppubBtb6rSUpX6ZTUbNPXpDt5EWXk7NT",
}

$ ipfs add nft.json
added QmPutrmFkNvCz9bR2UoW3V8BRrm6o81Fi3b91VDJmtXoL1 nft.json
 174 B / 174 B [==============================================================================================================================================================================================================] 100.00%
 
[download]
$ ipfs cat /ipfs/QmQ9YxmRtbs2dEppubBtb6rSUpX6ZTUbNPXpDt5EWXk7NT > nft.jpg
$ ipfs cat /ipfs/QmPutrmFkNvCz9bR2UoW3V8BRrm6o81Fi3b91VDJmtXoL1 > nft.json

[check.peers]
ipfs swarm peers

[check.gateway]
hash=`echo "I <3 IPFS -$(whoami)" | ipfs add -q`
curl "https://ipfs.io/ipfs/$hash"
>>>
curl: (7) Failed to connect to ipfs.io port 443: Connection timed out

[web.console]
localhost:5001/webui

```
