========================================================
Over the air updates with Pycom Gpy boards
========================================================

In this tutorial we will see the demonstration of OTA updates using Asvin 
IoT platform and the `Gpy <https://pycom.io/product/gpy/>`_ board from Pycom. 

    .. image:: ../images/OTA_wb.jpg
        :width: 400pt
        :align: center

Requirements:

1. nodemcu esp8266 board
2. micro USB cable
3. Asvin platform subscription 
4. platformIO VScode extension


Getting started
###############

To get started head to `Asvin's github repository <https://github.com/Asvin-io/tutorials>`_ and clone it. 
The code is writen under platformIO. Import the project using VScode's PlatformIO extenstion.


1.  To proceed further you will need to edit few of the parameters in the code.

    - Open the credentials.h file in the editor and add credentials for your device

        .. image:: ../images/keys_edited.jpg
           :width: 400pt
           :align: center
            
    - Device & Customer keys: This will be found on the asvin platform under the settings tab
    - email & password: Use the same email ID & password you use to login to asvin web platform 
    


2.  After this step, upload the sketch on the ESP8266 board

3.  This sketch uses the popular `WifiManager library <https://github.com/tzapu/WiFiManager>`_ to 
    manage WiFi credentials. On boot the ESP8266 will start a WiFi hotspot with name "AutoConectAP". User should connect to it with   
    cellphone/laptop and enter in the credentials. These credentials will be stored in the ESP flash 
    memory and will be stored as default. These credentials can be changed later on.

4. **Setting up OTA**

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