===================
Version Controller
===================

In this section we will see take a brief look at the **Version Controller** component of asvin architecture 
and explain it briefly. Version Controller (VC) maintains updated information of firmware avaliable for 
a particular edge device or device group on the asvin.io platform. It is one of the core components of the 
Asvin architecture.

    .. image:: ../images/asvinarchitecture-vc.png
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

