=========================
Interplanetary FileSystem 
=========================

In this section we will see take a brief look at the **Interplanetary FileSystem (IPFS)** component of 
asvin architecture and explain it briefly. 

    .. image:: ../images/asvinarchitecture-ipfs.png
        :width: 800pt
        :align: center

Device Security Booster uses Interplanetary File System protocol to store firmware and patches. 
IPFS is a content-addressable peer to peer method for storing and sharing hypermedia
in a distributed file system while eliminating duplicate files and redundancy. 
It uses a network infrastructure that enables Device Security Booster to store unalterable firmware data.
When a firmware file is stored on the network a hash is generated based on content of
the firmware and stored on blockchain network. Later on, the same hash is used by
edge devices to pull the firmware from data storage. This forms a generalized Merkle
directed acyclic graph(DAG). Each node of Merkle DAG is connected with a secured Hash. 
When a node is added in the DAG, its hash is computed based on hash of its local content 
and hashes of its children’s name instead of their content. Once it is created, it is 
impossible to alter a node in the network. IPFS has no single point of failure. Device Security Booster 
provides a distributed content delivery system which provides an extra layer of security 
and prevents DDoS attacks. Device Security Booster's SDK, which is run on edge devices, enables the functionality 
to interact with data storage servers. Once an edge device gets information from the version
controller regarding the newly available firmware, it uses this information to download 
appropriate firmware from the distributed CDN.