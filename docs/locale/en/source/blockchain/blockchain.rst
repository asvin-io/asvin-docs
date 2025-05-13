===========
Blockchain
===========

In this section we will take a brief look at the **Blockchain** component of 
asvin architecture and explain it briefly. 

    .. image:: ../images/asvinarchitecture-bc.png
        :width: 800pt
        :align: center

Blockchain is a type of Distributed Ledger Technology (DLT) which contains a growing list 
of records known as **blocks**. Each block contains the 
`cryptographic hash <https://en.wikipedia.org/wiki/Cryptographic_hash_function>`_ 
of the previous block. By design, blockchains are resistant to modification of the data stored on them.

In the asvin architecture, we have built the blockchain network based on 
`Hyperledger Fabric <https://www.hyperledger.org/use/fabric>`_ and 
`Hyperledger besu <https://www.hyperledger.org/use/besu>`_. Customers can choose to use either of the two
blockchains for their deployments. These blockchain networks provide a ledger that stores all transactions 
executed on the Device Security Booster network, e.g: device register, firmware upload, device update, firmware update, 
and user registration. Each of these transactions are paired with unique hashes and are stored in blocks which are again 
linked with a secured hash. This process provides security and immutability to the ledger. 
The Device Security Booster is designed for unlimited scalability with a cluster of servers which runs 
Fabric & Besu networks to administer the requirements to maintain functionality to millions of IoT devices.

Hyperledger Fabric
##################

The pluggable modules of the Fabric network allow maximum flexibility to Device Security Booster infrastructure, 
enabling Device Security Booster to develop bespoke solutions for its IoT customers. The cluster is developed using `Docker swarm <https://www.docker.com/>`_.

**The fabric has following modules and services:**

1. Peer: an entity in the Fabric network which receives request from applications, runs a chaincode, 
   validates transactions and maintains ledger.
2. Orderer: This service orders all the transactions happening in the Fabric network and forward them to peers to be validated
3. MSP: provides digital identities to every member of the Fabric network.
4. Storage: Fabric network uses CouchDB to store the current state of ledger data.

Hyperledger Besu
################

Hyperledger Besu is an open source Ethereum client. It can be run on the Ethereum public network or on 
private permissioned networks. 

**Hyperledger Besu’s features include:** 

1. The Ethereum Virtual Machine (EVM) is the Turing complete virtual machine that allows the deployment 
   and execution of smart contracts via transactions within an Ethereum blockchain.
2. Consensus Algorithms are involved in transaction validation, block validation, and block production (i.e., mining in Proof of Work). 
3. RocksDB key-value database to persist chain data locally is used for storage.  
4. P2P networking via Ethereum’s devp2p network protocols for inter-client communication and an additional sub-protocol for IBFT2.
5. User-facing mainnet Ethereum and EEA JSON-RPC APIs over HTTP and WebSocket protocols as well as a GraphQL API.  
6. Node performance is monitored using Prometheus or the debug_metrics JSON-RPC API method. 
   Network Performance is monitored with Alethio tools such as Block Explorer and EthStats Network Monitor.
7. Privacy in Hyperledger Besu refers to the ability to keep transactions private between the involved parties. 
   Other parties cannot access the transaction content, sending party, or list of participating parties. 
   Besu uses a Private Transaction Manager to implement privacy. 
8. A permissioned network allows only specified nodes and accounts to participate by enabling 
   node permissioning and/or account permissioning on the network.


The operating system level virtualization is achieved on blockchain server using docker. Each service
in the network runs in a separate docker container and these containers are hosted on multiple
machines on the cluster. The communication among containers is achieved using docker swarm. The whole 
blockchain network is developed and run using docker swarm technology.
