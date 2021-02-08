=================
Asvin Model
=================

In this section we will see take a brief look at the asvin architecture diagram 
and explain its components briefly. Some related concepts and keywords are also mentioned 
below.

    .. image:: ../images/asvinarchitecture.png
        :width: 800pt
        :align: center



Interplanetary FileSystem
#########################

Interplanetary FileSystem or IPFS is a distributed peer to peer hypermedia protocol designed
for storing and sharing data in a distributed file system. It is one of the core components 
of Asvin architecture. Asvin uses IPFS protocol to store firmware and patches. Check out the
detailed notes on IPFS here.

*Content Identifier*

Data exchanged on decentralised platforms like `IPFS <https://ipfs.io/>`_ depends on content-based addressing rather Then
local addressing to securely locate and identify data. A Content Identifier (CID) is a self describing
content address identifier. CID forms an address based on content itself which is a cryptographic hash
typically SHA-256 which is 32 bytes. An example of a binary image file stored on an IPFS network, the 
CID might be  *QmcRD4wkPPi6dig81r5sLdrtd1gDCL4zgpEj9CfuRrGbzF*.

Blockchain
##########

On the Asvin platform we use the `Hyperledger Fabric <https://www.hyperledger.org/use/fabric>`_ and 
`Hyperledger besu <https://www.hyperledger.org/use/besu>`_ blockchains. It is one of the core componets 
of the asvin platform. The asvin platform uses Blockchain technology to store all transactions executed 
on the asvin.io network: device register, firmware upload, device update, firmware update, user registeration
etc. All these transactions are connected with hashes and stored in blocks which are again linked with a 
secured hash. 

*Distributed Ledger*

Distributed ledger technology (DLT) is a digital system for recording the transaction of assets in which 
the transactions and their details are recorded in multiple places at the same time. Unlike traditional databases,
distributed ledgers have no central data store or administration functionality. The above mentioned Blockchain 
is a type of DLT. 


*Smart Contracts*

A smart contract is a computer program or a transaction protocol which is intended to automatically 
execute, control or document legally relevant events and actions according to the terms of a contract 
or an agreement.The objectives of smart contracts are the reduction of need in trusted intermediators,
arbitrations and enforcement costs, fraud losses, as well as the reduction of malicious and accidental 
exceptions.

Edge Devices
############

The edge devices are end points in the asvin.io architecture. These are the end devices in an
IoT network which are operated to control, manage and solve a physical task for an instance,
smart washing machine in a house, temperature and humidity monitor in a chemical plant, air
quatliy sensor installed in a city etc. These devices have microcontrollers and sensors at their
core. Usually, edge devices have a small footprint and are easy to manage in
remote areas under extreme environmental conditions. Examples for egde devices are industrial process
monitoring sensors, smart meters, Lora nodes, smoke detectors etc.


Customer Platform
#################

Asvin provides a user freindly customer platform to abstract the complexities of the background processes
this customer platform enables users to register devices, setup & schedule firmware rollouts, group actions on
registered devices, blacklisting of devices etc.

The customer platform also displays information of firmware updates and provides version of edge devices.



