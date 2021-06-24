PUF Based Device ID
===================

Wikipedia ” A physical unclonable function or PUF, is a physical object that for a given input and conditions 
(challenge), provides a physically-defined “digital fingerprint” output that serves as a unique identifier ”

PUF takes advantage of submicron variations that occur naturally during semiconductor fabrication. These variations
occur in the physical parameters such as length, width, thickness, etc of semiconductor materials. a detailed blog is 
posted `here <https://asvin.io/physically-unclonable-functionpuf-introduction/>`_.

For this demo we have used the E1 devlopment board from OKDO. This development board is based on LPC55S69xx microcontroller 
from NXP. The microcontroller contains onboard Physical Unclonable Function (PUF) using dedicated SRAM.
Follow this blog here for a detailed  `setup guide <https://asvin.io/physically-unclonable-function-setup/>`_.

Later on we also describe the process of key generation `here <https://asvin.io/puf-generate-unique-ids/>`_ based on PUF technology.
This generated key can be used in your applications in various ways. 
We at asvin are using the generated ID as a unique device ID while making requests to the asvin BeeHive IoT update platform.
