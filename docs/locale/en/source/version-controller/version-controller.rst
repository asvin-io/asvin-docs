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
host identical web services. Each node in the cluster is fully functional web server and can serve a request
independently. Each node has different IP adress, but they are not visible for the edge devices. An abstraction 
layer is used on top of the cluster to hide this complexity. The abstraction makes use of round-robin DNS2
technique for load balancing, fault tolerance and load distribution. The server accepts DNS requests and 
responds to them by forwarding it to a computing machine in the cluster. A machine from the cluster is then 
chosen in round-robin fashion.

The key features of the version controller server are following.

**High-availability**

The two layers architecture of the version controller server provides defense against single point failure. Even 
if a node in the cluster goes down because of hardware or software problem the asvin.io framework stays functional.

**Scalability**

It is easy to install a new node in the cluster to enhance performance of the version controller server. The cluster
is highly scalable and provides stability.

**Efficiency**

The workload is distributed among multiple web server in the cluster that gives boost to the network performance, 
reduce collision and avoid congestion during high demand.

The Version controller provides resilience to the asvin.io network. The server performs following
tasks.

1. **Response to Edge Devices**

The edge devices poll the version controller to check for new update. The server responds to edge device with information 
of a valid firmware.

2. **Latest Firmware Version List**

It maintains real time information of different versions of firmware available on data storage servers. The version
controller has a list of available firmware on asvin.io plat form for all edge devices. It keeps the list updated by
interacting with Customer plat form server.