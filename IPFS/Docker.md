- https://hub.docker.com/r/ipfs/go-ipfs/
### [run ipfs inside docker](https://docs.ipfs.io/how-to/run-ipfs-inside-docker)
```
export ipfs_staging=</absolute/path/to/somewhere/>
export ipfs_data=</absolute/path/to/somewhere_else/>

[start]
docker run -d --name ipfs_host -v $ipfs_staging:/export -v $ipfs_data:/data/ipfs -p 4001:4001 -p 4001:4001/udp -p 127.0.0.1:8080:8080 -p 127.0.0.1:5001:5001 ipfs/go-ipfs:latest
>>>
dcb9389e558979df19081df739252fa3b446160c49b124c5c02a9c42f9fb33bd

[log]
docker logs -f ipfs_host
>>>
Changing user to ipfs
ipfs version 0.9.1
generating ED25519 keypair...done
peer identity: 12D3KooWBN1aJdVSJwfJFQmBB7mi8FYmQZDj2WkAhERjixXo6sbS
initializing IPFS node at /data/ipfs
to get started, enter:

	ipfs cat /ipfs/QmQPeNsJPyVWPFDVHb77w8G42Fvo15z4bG2X8D2GhfbSXc/readme

Initializing daemon...
go-ipfs version: 0.9.1-dc2715a
Repo version: 11
System version: amd64/linux
Golang version: go1.15.2
Swarm listening on /ip4/127.0.0.1/tcp/4001
Swarm listening on /ip4/127.0.0.1/udp/4001/quic
Swarm listening on /ip4/172.17.0.2/tcp/4001
Swarm listening on /ip4/172.17.0.2/udp/4001/quic
Swarm listening on /p2p-circuit
Swarm announcing /ip4/127.0.0.1/tcp/4001
Swarm announcing /ip4/127.0.0.1/udp/4001/quic
Swarm announcing /ip4/172.17.0.2/tcp/4001
Swarm announcing /ip4/172.17.0.2/udp/4001/quic
API server listening on /ip4/0.0.0.0/tcp/5001
WebUI: http://0.0.0.0:5001/webui
Gateway (readonly) server listening on /ip4/0.0.0.0/tcp/8080
Daemon is ready

[run]
docker exec ipfs_host ipfs swarm peers

[add]
cp -r <something> $ipfs_staging
docker exec ipfs_host ipfs add -r /export/<something>
>>>
 910 B / 910 B  100.00%added QmU2oUVxqzySCzbHcLU2LYyFf4AVPfKoUvhqQDz57TJ6CA Makefile

[stop]
docker stop ipfs_host

[IPFS_PROFILE?]
docker run -d --name ipfs_host -e IPFS_PROFILE=server -v $ipfs_staging:/export -v $ipfs_data:/data/ipfs -p 4001:4001 -p 4001:4001/udp -p 127.0.0.1:8080:8080 -p 127.0.0.1:5001:5001 ipfs/go-ipfs:latest

[IPFS_SWARM_KEY_FILE?]
docker run -d --name ipfs_host -e IPFS_SWARM_KEY=<your swarm key> -v $ipfs_staging:/export -v $ipfs_data:/data/ipfs -p 4001:4001 -p 4001:4001/udp -p 127.0.0.1:8080:8080 -p 127.0.0.1:5001:5001 ipfs/go-ipfs:latest
cat your_swarm.key | docker secret create swarm_key_secret -
docker run -d --name ipfs_host --secret swarm_key_secret -e IPFS_SWARM_KEY_FILE=/run/secrets/swarm_key_secret -v $ipfs_staging:/export -v $ipfs_data:/data/ipfs -p 4001:4001 -p 4001:4001/udp -p 127.0.0.1:8080:8080 -p 127.0.0.1:5001:5001 ipfs/go-ipfs:latest

[key rotation?]
# given container named 'ipfs-test' that persists repo at /path/to/persisted/.ipfs
docker run -d --name ipfs-test -v /path/to/persisted/.ipfs:/data/ipfs ipfs/go-ipfs:v0.7.0 
docker stop ipfs-test  

# key rotation works like this (old key saved under 'old-self')
docker run --rm -it -v /path/to/persisted/.ipfs:/data/ipfs ipfs/go-ipfs:v0.7.0 key rotate -o old-self -t ed25519
docker start ipfs-test # will start with the new key
```
