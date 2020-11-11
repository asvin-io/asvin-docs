========================================================
Over the air updates with Pycom Gpy boards
========================================================

In this tutorial we will see the demonstration of OTA updates using Asvin 
IoT platform and the *Gpy* board from Pycom. 

    .. image:: ../images/OTA_wb_pycom.jpg
        :width: 400pt
        :align: center


Requirements:

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
        - Next it will register the device by calling the `Register device <https://asvin.readthedocs.io/en/latest/version-controller/version-controller-api.html#register-device>`_ API 
        - Then the code will check if a rollout exists 
        - If a rollout exists the the code will try to download and perform the update
 
        




5.  **Setting up OTA**



    Asvin IoT platform provides secure OTA updates for IoT devices. Lets see how we can setup OTA updates

    1.  *Register Device*:
        When you start and uplod your sketch on the ESP8266 board, the board will start executing 
        and calling the defined API routes. The first API it calls is 
        `Register device <https://asvin.readthedocs.io/en/latest/version-controller/version-controller-api.html#register-device>`_ 
        After this API is sucessfully called, you will see your device appear
        under the "Just Registered devices" section of the platfomr under devices. 

        .. image:: ../images/register_edited.jpg
            :width: 400pt
            :align: center


    2.  *Device Groups*:
        Asvin's IoT platform provides updates for a group of devices. Let us create a group called
        OTA test. We can add our ESP device to this group . Under Devices > Device groups click on 
        *"New Device Group"*. After this navigate back to the "Just registered" devices, click device 
        grouping and add the device to the newly created device group.         
    
    3.  *File Groups*:
        Once our device is assigned to a file group. Let us upload a file we want to provide as an OTA 
        update. Usually this is *<somefile_name>.bin*. Let us upload esp-ota-blink.bin file to the filegroup 
        ESP_OTA_Test
    
        .. image:: ../images/upload_file.png
            :width: 400pt
            :align: center

    4.  *Rollout*:
        In this step we will setup a rollout to deliver OTA update of the file specified above to our 
        ESP8266 device.
        In the rollout section let us start by creating a rollout.
        Fill in the options as shown in the screenshot.
        Choose either batch/immediate update. 
        There is an option to choose a time or do an update immediately.
        Select the file to be rolled out as update and click *Save* 

        .. image:: ../images/rollout_edited.jpg
            :width: 400pt
            :align: center

    5.  The rollout is now enabled. Next time our device queries the  
        `checkrollout API <https://asvin.readthedocs.io/en/latest/version-controller/version-controller-api.html#next-rollout>`_ , 
        the rollout will be avaliable and further API's will be called inside the ESP device.
        The ESP device will update itself after this with the file we uploaded earlier. In this case we will see the 
        LED blinking on our ESP board

    6.  Once the rollout is completed the new file will be running on the board. In this case we rolled out a BLink LED file. 
        The board will call the  `checkrolloutsuccess API <https://asvin.readthedocs.io/en/latest/version-controller/version-controller-api.html#rollout-success>`_ ,
        which is the part of the esp-ota-blink.bin file that we uploaded earlier    

    7.  The change in the firmware version of the device is also updated on the 
        `Asvin platform <https://app.asvin.io/>`_  
         


Thus we have sucessfully completed the OTA rollout. The Complete code and files can be found
at Asvin's github repository `Github repository <https://github.com/Asvin-io/tutorials>`_  