==============================
Over-The-Air update of ESP32
==============================

This tutorial demonstrates the process of securely updating ESP32 device firmware Over-The-Air with Device Security Booster.

Requirements
############

1. ESP32 board
2. Micro USB cable
3. Device Security Booster subscription 
4. PlatformIO VScode extension

Setup
#####

To get started head to `asvin's Github repository <https://github.com/asvin-io/asvin-tutorials>`_ and clone it. 
Open the folder ESP32-OTA in Visual Studio code. The code is writen under PlatformIO.

1. Rename credentials_copy.h to credentials.h in the src folder.
2. Update customer_key, device_key which can be obtained from platform as shown below.
   
    .. image:: ../images/keys_edited.jpg
            :width: 400pt
            :align: center
3. Then build the application and flash it to ESP32.
4. This sketch uses the popular `WifiManager library <https://github.com/tzapu/WiFiManager>`_ to manage WiFi credentials. 
   Upon booting the ESP32 will start a WiFi hotspot with the name "AutoConectAP". 
   The user should connect to it with cellphone/laptop and enter in their WiFi credentials. 
   These credentials will be stored in the ESP flash memory and will be stored as the default. These credentials can be changed later on.

OTA update procedure
####################
The Device Security Booster provides secure OTA updates for IoT devices. The user can follow the below easy steps to update their IoT edge devices.

1. *Register Device*:
   When you upload your sketch on the ESP32 board and start it, the device will start executing and calling set of defined API routes.
   The device first obtains the oauth token from the asvin `oauth API <https://asvin.readthedocs.io/en/latest/oauth/oauth-api.html>`_. 
   This token will be valid for next 10 mins. After obtaining the oauth token, the device calls the API :ref:`Register Device`, 
   Once this API call is successful, you will see your device appear under the "Lobby" subsection of the "Devices" section in the platform. 

    .. image:: ../images/register_edited.png
            :width: 400pt
            :align: center

2. *Device Groups*: 
   asvin's IoT platform provides updates for a group of devices. Let us create a group called ESP32Devices. 
   We can add our ESP device to this group . Under *Devices -> Grouped* click on *"New Device Group"*. Then give the group name and save it. 
   After this navigate back to the "Lobby", click Device Grouping and add the device to the newly created device group.         

3. *File Groups*: 
   Now we have to upload the file we want to provide as an OTA update. Usually this is *<file_name>.bin*. 
   Let us upload esp-ota-blink.bin file to the filegroup ESP_OTA_Test.

    .. image:: ../images/upload_file.png
            :width: 400pt
            :align: center

4. *Rollout*: 
   In this step we will setup a rollout to deliver OTA update of the file specified above to our ESP32 device. 
   In the *Rollouts* section let's start by creating a rollout. Fill in the options as shown in the below figure. 
   Choose either batch or immediate update. There is an option to choose a time or to do an update immediately. 
   Select the file to be rolled out as an update and click *Save*. 

    .. image:: ../images/rollout_edited.png
            :width: 400pt
            :align: center

5. The rollout is now enabled. Next time our device queries the :ref:`Next Rollout` API, 
   the rollout will be available and further API's will be called inside the ESP device. 
   The ESP device will update itself by downloading the file from asvin IPFS server. 
   After successful update, we will see the LED blinking on the ESP board.

6. Once the rollout is completed the new application will be running on the board. 
   In this case we rolled out a Blink LED application. The board will call the :ref:`Rollout Success` API, 
   which is the part of the esp-ota-blink.bin file that we uploaded earlier.    

7. The change in the firmware version of the device is also updated on the `Device Security Booster <https://app.asvin.io/>`_  .

Thus we have sucessfully completed the OTA rollout. The Complete code and files can be found
at asvin's Github repository `Github repository <https://github.com/asvin-io/tutorials>`_  