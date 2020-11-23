==========================================
Over the air updates with Pycom Gpy boards
==========================================

In this tutorial we will see the demonstration of OTA updates using Asvin 
IoT platform and the *Gpy* board from Pycom. 

    .. image:: ../images/OTA_wb_pycom.jpg
        :width: 400pt
        :align: center


Requirements
############

1. Pycom `Gpy board <https://pycom.io/product/gpy/>`_
2. Pycom `Expansion board <https://pycom.io/product/expansion-board-3-0/>`_ 
3. micro USB cable
4. Asvin platform subscription 
5. `Pymakr <https://marketplace.visualstudio.com/items?itemName=pycom.Pymakr>`_ VScode extension 


Getting started
###############

To get started head to `Asvin's github repository <https://github.com/Asvin-io/tutorials>`_ and clone it. Open the *pycom-ota-updates*
folder in VScode. Make sure to have the updated firmware on your Pycom *Gpy* as well as the *expansion* board. 

1.  *Description of Files*:
    
    This repository contains few python sketches. Below is a brief descrption of them

    *lib/OTA.py*
        This library enables OTA updates. It is discussed in detail below.
    
    *connect_wifi.py*
        This script is a wrapper around pycom Wlan() library
    
    *asvin.py*
        This file contains funtions to call various API's from the Asvin Platform.
    
    *config.py*
        This file contains various user configuration options and are dicussed in the next section

2.  To proceed further you will need to edit few of the parameters in the config.py file.

    - Open the config.py file in the editor and add credentials for your device

        .. image:: ../images/configpy.jpg
            :width: 400pt
            :align: center
            
    - Under the Asvin Credentials populate the following fields
        - customer_key:     Enter Customer key from Asvin platform 
        - device_key:       Enter Device key from Asvin platform 
        - platformemail:    Enter email address registerd on Asvin platform 
        - platformpassword: Enter password registerd on Asvin platform 

    - Under Wifi Credentials fill in the SSID and password.
    - Optionaly you can also set the LED color for various funtions from the config file.

    

3.  After this step, upload the project on the Pycom Board.

4.  The code goes through the following steps:
        - Connect to Wifi
        - Check if the previos *rollout* was successful
        - Next it will register the device by calling the :ref:`Register Device` API 
        - Then the code will check if a rollout exists 
        - If a rollout exists the the code will try to download and perform the update
 
        
5.  **Setting up OTA**


    Follow the steps below along with the :doc:`../getting-started/customer-platform` guide. 
    
    1.  *Register Device*:
            The device will be automatically registered on boot

    2.  *Device Groups*:
            Setup a device group on the Asvin IoT platform.

    3.  *File Groups*:
            In case of pycom target devices there are certain modifications to be done to files before uploading them to
            a filegroup for rollout. Users must add the following two lines at the start of every file they want to upload 
            over the air.


            ::

                path="/flash/config.py"
                version = "0.0.1"
                """
                Asvin OTA Config File
                """

                
                          
            
            In this case the *Path* variable is the path of the variable inside the pycom's filesystem. The *version* is the user defined
            version number of the existing file.

    4.  *Rollout*:
            Setup the rollout as mentioned in the `Getting Started <https://asvin.readthedocs.io/en/latest/getting-started/getting-started.html>`_ guide.
            In this case it is important to follow the guidelines mentioned under *File Groups*.

Thus we have sucessfully completed the OTA rollout for the Pycom Gpy board. The Complete code and files can be found
at Asvin's github repository `Github repository <https://github.com/Asvin-io/tutorials>`_  