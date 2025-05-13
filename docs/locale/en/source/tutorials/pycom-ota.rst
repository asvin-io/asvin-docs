==========================================
Over the air updates with Pycom Gpy boards
==========================================

In this tutorial we will see the demonstration of OTA updates using the Device Security Booster and the *Gpy* board from Pycom. 

.. image:: ../images/OTA_wb_pycom.jpg
    :width: 400pt
    :align: center
    :alt: pycomOTA


Requirements
############

1. Pycom `Gpy board <https://pycom.io/product/gpy/>`_
2. Pycom `Expansion board <https://pycom.io/product/expansion-board-3-0/>`_ 
3. Micro USB cable
4. Device Security Booster subscription 
5. `Pymakr <https://marketplace.visualstudio.com/items?itemName=pycom.Pymakr>`_ VScode extension 


Getting started
###############

To get started head to `asvin's Github repository <https://github.com/asvin-io/asvin-tutorials>`_ and clone it. Open the *pycom-ota-updates*
folder in VScode. Make sure to have the updated firmware on your Pycom *Gpy* as well as the *expansion* board. 

1.  *Description of Files*:
    
    This repository contains few python sketches. Below is a brief descrption of them

    *lib/OTA.py*
        This library enables OTA updates. It is discussed in detail below.
    
    *connect_wifi.py*
        This script is a wrapper around the pycom Wlan() library
    
    *asvin.py*
        This file contains functions to call various API's from the platform.
    
    *config.py*
        This file contains various user configuration options and are discussed in the next section.

2.  To proceed further you will need to edit a few of the parameters in the config.py file.

    - Open the config.py file in the editor and add credentials for your device

    .. image:: ../images/configpy.jpg
        :width: 400pt
        :align: center
        :alt: configpy

    - Under the asvin Credentials populate the following fields
        - customer_key:     Enter your Customer key from the platform 
        - device_key:       Enter your Device key from platform 
      
    - Under WiFi Credentials, fill in the SSID and password.
    - Optionally, you can also set the LED color for various funtions from the config file.

    

3.  After this step, upload the project on the Pycom Board.

4.  The code goes through the following steps:
        - Connect to WiFi.
        - Check if the previous *rollout* was successful.
        - Next it will register the device by calling the :ref:`Register Device` API.
        - Then the code will check if a rollout exists 
        - If a rollout exists the code will try to download and perform the update
 
        
5.  **Setting up OTA**


    Follow the steps below along with the :doc:`../getting-started/customer-platform` guide. 
    
    1.  *Register Device*:
            The device will be automatically registered on booting

    2.  *Device Groups*:
            Setup a device group on the Device Security Booster.

    3.  *File Groups*:
            In the case of Pycom target devices, there are certain modifications to be done to files before uploading them to
            a filegroup for rollout. Users must add the following two lines at the start of every file they want to upload 
            over the air.


            ::

                path="/flash/config.py"
                version = "0.0.1"
                """
                asvin OTA Config File
                """

                
                          
            
            In this case the *Path* variable is the path of the variable inside the Pycom's filesystem. The *version* is the user defined
            version number of the existing file.

    4.  *Rollout*:
            Setup the rollout as mentioned in the `Getting Started <https://asvin.readthedocs.io/en/latest/getting-started/getting-started.html>`_ guide.
            In this case it is important to follow the guidelines mentioned under *File Groups*.

Thus we have successfully completed the OTA rollout for the Pycom Gpy board. The Complete code and files can be found
at asvin's Github repository `Github repository <https://github.com/asvin-io/asvin-tutorials>`_  