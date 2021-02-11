===========
Blockchain
===========

In this section we will see take a brief look at the **Blockchain** component of 
asvin architecture and explain it briefly. 

    .. image:: ../images/asvinarchitecture-bc.png
        :width: 800pt
        :align: center

Blockchain is a type of Distributed Ledger Technology (DLT) which contains a growing list 
of records known as **blocks**. Each block contains the 
`cryptographic hash <https://en.wikipedia.org/wiki/Cryptographic_hash_function>`_ 
of the previous block. Blockchains by design are resistant to modification of its data.

In the Asvin architecture, we have build the blockchain network based on 
`Hyperledger Fabric <https://www.hyperledger.org/use/fabric>`_ and 
`Hyperledger besu <https://www.hyperledger.org/use/besu>`_. Customers can choose to use any of the two
blockchains in their deployments. These blockchain networks provide a ledger that stores all transactions 
executed on the asvin.io network E.g: device register, firmware upload, device update, firmware update, 
user register etc. All these transactions are connected with hashes and stored in blocks which are again 
linked with a secured hash. This process provides security and immutability to the ledger. The asvin.io 
platform is backed with a cluster of servers which runs fabric & besu networks to maintain millions of IoT
devices. asvin.io has built this cluster in such a way that it can be scaled up multifold to support 
increasing demand of edge devices. 

Hyperledger Fabric
##################

The fabric network is constructed of different pluggable modules which allow asvin.io infrastructure
to be more flexible. This modular and pluggable approach enables asvin.io to develop tailored solutions 
for IoT customers. The cluster is formed using docker swarm. 

**The fabric has following modules and services:**

1. Peer: It is an entity in the fabric network which receives request from applications, runs a chaincode, 
validates transactions and maintains ledger.
2. Orderer: This service orders all the transactions happening in the fabric network and forward them to peers to be validated
3. MSP: It takes care of providing digital identities to every member of the fabric network.
4. Storage: Fabric network uses CouchDB to store the current state of ledger data.

Hyperledger Besu
################

Hyperledger Besu is an open source Ethereum client. It can be run on the Ethereum public network or on 
private permissioned networks. 

**Hyperledger Besu’s features include:** 

1. The Ethereum Virtual Machine (EVM): The EVM is the Turing complete virtual machine that allows the deployment 
and execution of smart contracts via transactions within an Ethereum blockchain.
2. Consensus Algorithms: Hyperledger Besu implements various consensus algorithms which are involved in transaction
validation, block validation, and block production (i.e., mining in Proof of Work). 
3. Storage: Hyperledger Besu uses a RocksDB key-value database to persist chain data locally.  
4. P2P networking: Hyperledger Besu implements Ethereum’s devp2p network protocols for inter-client communication 
and an additional sub-protocol for IBFT2.
5. User-facing APIs: Hyperledger Besu provides mainnet Ethereum and EEA JSON-RPC APIs over HTTP and WebSocket protocols 
as well as a GraphQL API.  
6. Monitoring: Hyperledger Besu allows you to monitor node and network performance.
Node performance is monitored using Prometheus or the debug_metrics JSON-RPC API method. 
Network Performance is monitored with Alethio tools such as Block Explorer and EthStats Network Monitor.
7. Privacy: Privacy in Hyperledger Besu refers to the ability to keep transactions private between the involved parties. 
Other parties cannot access the transaction content, sending party, or list of participating parties. 
Besu uses a Private Transaction Manager to implement privacy. 
8. Permissioning: A permissioned network allows only specified nodes and accounts to participate by enabling 
node permissioning and/or account permissioning on the network.



The operating system level virtualization is achieved on blockchain server using docker. Each service
in the network runs in a separate docker container. These docker containers are hosted on multiple
machines on the cluster. The communication among containers is achieved using docker swarm. The whole 
blockchain network is developed, deploy and run using docker swarm technology.
