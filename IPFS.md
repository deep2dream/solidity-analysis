## ipfs.io
- https://ipfs.io/#install
- https://ipfs.io/#how
### install
- https://docs.ipfs.io/install/command-line/#official-distributions
- https://github.com/ipfs/go-ipfs
- https://docs.ipfs.io/how-to/command-line-quick-start
- https://www.quicknode.com/guides/solidity/how-to-create-and-deploy-an-erc-721-nft
```
wget	https://dist.ipfs.io/go-ipfs/v0.9.0/go-ipfs_v0.9.0_linux-amd64.tar.gz
tar	-xvzf	go-ipfs_v0.9.0_linux-amd64.tar.gz
cd	go-ipfs/
./install.sh
sudo	./install.sh
ipfs --version
```
### use
```
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

$ ipfs cat /ipfs/QmYwAPJzv5CZsnA625s3Xf2nemtYgPpHdWEz79ojWnPbdG/quick-start

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
```
