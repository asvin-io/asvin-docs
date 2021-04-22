============
Introduction
============

There was a time when making coffee required a broad scope of tasks. 
First you would go to the market to buy freshly roasted, aromatic coffee beans, 
then grind them and while the coffee was brewing you would retrieve the newspaper 
from the front door and start your day while waiting for the coffee to ‘catch up’. 
Fast-forward to 2021 and our “smart” coffee machine monitors our armband to determine 
if we are awake so that by the time we reach the kitchen our artisanal coffee beans 
have been freshly roasted, ground and brewed to our exact preferences whilst we make 
our way down to the coveted first cup. Additionally, that coffee maker can now monitor 
how much coffee remains in the hopper, can order our favorite beans from a preferred seller, 
and automatically makes the payment using credit card details saved on the machine.

We are surrounded by many smart devices such as our coffee machine. Equipped with wireless 
communication protocols such WiFi, Bluetooth, NFC, LoRaWAN, etc. these smart devices talk 
to one another and are connected to the internet and are referred to as Internet for Things 
(IoT) devices. IoT devices are now ubiquitous to our lives, whether found in our homes, cities, 
workplaces, or in hospitals. We live in a time where smart devices communicate and interact 
with us more often than other human beings. By 2030, the number of IoT devices and IoT market 
size are projected to reach 125 billion and 1.3 trillion USD respectively.

.. image:: images/iot-devices.png
    :alt: IoT Devices

IoT devices simplify processes and make our lives more convenient, on the other hand, these 
devices are vulnerable to cyber-security threats. For instance, if someone hacks our benign-looking 
smart coffee machine it could reveal our WLAN credentials, credit card details, sleeping patterns 
and much more personal data but it can also be used as a bot to launch cyber security attacks on 
other digital resources. By example, Mirai-2016 turned over six million network connected devices 
to a botnet to launch DDoS attacks. These types of attacks have been outpacing the exponential growth 
of IoT devices for a myriad of reasons including using default or weak passwords, small encryption keys, 
or failing to download security patches and softwares updates.

One of the major security concerns is that IoT devices do not have built-in Over-the-Air (OTA) 
firmware update mechanisms. IoT devices are manufactured and managed with a set and forget policy, 
meaning IoT devices are configured at the beginning of their lifecycle and then left alone to defend 
against security attacks. Technologies are evolving so fast that it is paramount to have a well-defined, 
secure process to continuously assess the threat landscape of IoT devices and update the firmware regularly with latest security patches.

In the last couple of years, there have been major developments in the area of update platforms for IoT devices. 
Some solutions, such as Eclipse hawkBit, Mbed, and Mender, address the existing problem but their solutions 
are limited to a specific  microcontroller architecture, software stacks, and industries are designed and 
developed as centralized solutions which are prone to single point failure and do not scale very well. 
The following sections describe how the asvin platform differentiates itself from other IoT update solutions.

Asvin Platform
##############

asvin platform is an enterprise-grade, cloud platform designed with Distributed Ledger Technology (DLT) 
to cascade security patches and generate a chain of trust for IoT devices. The asvin platform is powered 
by **distributed** and **decentralized** technologies and utilizes Interplanetary Filesystem (IPFS) to 
store and manage the firmware files of IoT devices. All firmware files and patches are distributed across 
multiple IPFS nodes while the respective devices’ critical metadata information is saved on an immutable 
distributed ledger (DL) as is each event taking place on the asvin platform. These technologies increase 
the fault tolerance of the platform making it both more accessible as well as offering greater resiliency.

It is one thing to have a working prototype of an IoT product and another to administer and update millions 
of smart devices. The most desirable feature of any IoT solution is scalability, and asvin delivers - effectively and efficiently.

The asvin platform has a highly **customizable** and **modular** architecture and has been designed and 
developed to support IoT applications in  diverse industries  with its pluggable modules optimized according to the specific use case.

Unlike other FUOTA solutions the asvin platform is a **universal** solution, it is not restrictive in 
nature for any hardware and software stack. asvin enables the innovation and versatility of any IoT application 
built with Atmel AVR to ARM Cortex M7 ranging in applications from agriculture to financial services.
