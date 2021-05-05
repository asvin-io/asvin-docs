==================
Version Controller
==================

In this section we will take a brief look at the **Version Controller** component of asvin architecture. 
Version Controller (VC) maintains updated information of firmware avaliable for a particular 
edge device or device group on the asvin.io platform.

.. image:: ../images/asvinarchitecture-vc.png
        :alt: asvin VC 
        :width: 800pt
        :align: center


To manage billions of IoT edge devices asvin.io.io employs a distributed service cluster infrastructure.
For edge devices this complexity is invisible, and they interact with the cluster as they would do with a
single machine. The version controller server consists of multiple nodes which have copy of web server and
host identical web services. Each node in the cluster is a fully functional web server with a unique 
IP address and can service any request independently but they are not visible to the edge devices. 
An abstraction layer consisting of a round-robin DNS2 technique for load balancing, fault tolerance and 
load distribution is used on top of the cluster to hide this complexity. The server accepts DNS requests and 
responds by forwarding them on to a computing machine in the cluster. 
A machine from the cluster is then chosen in round-robin fashion.

The key features of the version controller server are following.

**High-availability**

The two layers architecture of the version controller server provides defense against single point failure. 
In the event a node in the cluster malfunctions the asvin.io framework remains operational.

**Scalability**

The cluster is highly scalable and stable making it easy to install a new node in the cluster 
to enhance the performance of the VC server. 

**Efficiency**

The VC provides resilience to the asvin.io network and distributes the workload across multiple web servers 
in the cluster improving network performance, reducing latency and collisions during periods of high demand. 
The Version controller provides resilience to the asvin.io network. 

The server performs following tasks.

1. **Response to Edge Devices**

The edge devices poll the version controller to check for new update and the server responds to edge device with information 
of a valid firmware.

2. **Latest Firmware Version List**

The Version Controller maintains real time information of different versions of firmware available on data storage servers. 
It also has a list of available firmware on asvin.io platform for all edge devices. It keeps the list updated by
interacting with Customer platform server.