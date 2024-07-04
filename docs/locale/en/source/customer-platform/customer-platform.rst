=========================
Customer Platform 
=========================

In this section we briefly explain the **Customer Platform** component of asvin architecture. 

    .. image:: ../images/asvinarchitecture-customerplatform.png
        :width: 800pt
        :align: center

At asvin, we believe in a simple and user-friendly solutions. 
The asvin.io customer platform provides an abstraction layer to hide the complexities and sophistication of the Distributed Ledger Technology. 
This abstraction is facilitated using a cluster of servers backed with a database server. 
A load balancer ensures that the volume of IoT devices being maintained on the asvin.io 
platform encounter no latency in the connection between the customer’s network and their IoT edge devices to the asvin.io server.

**Device Security Booster™** - The customer Platform delivers following functions:

1. Service Dashboard
    It serves as a portal for the IoT device operators to directly interact and 
    control the update and patch status of their edge devices.
    The portal drives the functionalities to upload firmware, delete firmware, manage edge
    devices, check health statistics of edge devices etc.

2. Upload Firmware
    Uploads firmware provided by customer to IPFS Server.

3. Update Ledger
    Interacts with Hyperledger blockchain server to update firmware database.

4. Update Version Control Server
    It keeps version control server updated with information of latest firmware.