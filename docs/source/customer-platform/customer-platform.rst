=========================
Customer Platform 
=========================

In this section we will see take a brief look at the **Customer Platform** component of 
asvin architecture and explain it briefly. 

    .. image:: ../images/asvinarchitecture-customerplatform.png
        :width: 800pt
        :align: center

At asvin, we believe in a simple and user-friendly solutions. 
asvin.io customer platform provides an abstraction layer to hide the complexities and sophistication of the Distributed Ledger technology. 
This abstraction is facilitated using a cluster of servers backed with database server. 
To cope up with gigantic number of IoT devices a load balancer is installed. 
The load balancer streamlines the connection from customers and IoT edge devices to the server.

The customer Platform delivers following functions:

1. Service Dashboard
    It is a portal for the IoT device Operators to directly in
    teract and control the update and patch status of their edge devices.
    The portal has functionalities to upload firmware, delete firmware, manage edge
    devices, check health statistics of edge devices etc.

2. Upload Firmware
    Uploads firmware provided by customer to IPFS Server.

3. Update Ledger
    Interacts with Hyperledger blockchain server to update firmware database.

4. Update Version Control Server
    It keeps version control server updated with information of latest firmware.