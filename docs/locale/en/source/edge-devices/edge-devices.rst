====================
Edge Devices
====================

Following is a brief explanation of the **Edge Devices** component of asvin architecture.  

    .. image:: ../images/asvinarchitecture-edgedevice.png
        :width: 800pt
        :align: center


The edge devices are end points in the asvin.io architecture and, in an IoT network, 
are tasked to control, manage and solve a physical task. Usually, many edge devices shall 
have a small footprint and must be easy to manage in remote areas under often extreme 
environmental conditions. For example: industrial process monitoring sensors, smart meters, 
Lora node etc. asvin provides libraries for a wide range of edge devices to facilitate the 
technical requirements necessary to interact with the asvin.io infrastructure securely and 
efficiently. The asvin libraries act as an interface between the edge devices and the asvin.io platform. 
The asvin.io SDK makes it easy to use APIs to interact with the asvin.io update infrastructure. 
The SDKs are developer friendly and allow for new IoT devices to connect with asvin.io 
infrastructure quickly to take direct advantage of a ready-to-run, update distribution network.
The key features of asvin SDK is that It is a generic solution and not limited to any specific
hardware platform e.g. Arduino, ESP, STM, Arm Cortex-M3, M4 etc. and software protocols.


**The asvin.io libraries installed on edge device provides following functionalities:**

1. **Device Update Management**
    - Securely register devices on asvin.io platform
2. **Check for Firmware Updates**
    - Regularly poll for updates in configurable time intervals
3. **Download and Install Firmware**
    - Download and store updated versions of firmware
    - Install the firmware based on traffic and availability of edge device
4. **Collect Health Statistics**
    - Send timely health updates of edge device on asvin.io platform e.g. firmware version in use
    - asvin.io platform generates insights from the data which can be used to extend life cycle of IoT devices and for preventive maintenance.