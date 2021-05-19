Asvin Customer Platform
=======================

asvin IoT platform provides secure OTA updates for IoT devices. Let's get started with the platform.

1.  *Register Device*:
        When you start and upload your code on any of the supported boards in the 
        :doc:`../tutorials/tutorials` section, the board will start executing 
        and calling the defined API routes. To Register the device the 
        :ref:`Register Device` API is called.
        After this API is successfully called, your device will appear
        under the *"Lobby"* sub-menu of the platform's *"Devices"* menu. 

        .. image:: ../images/register_edited.png
            :width: 400pt
            :align: center


2.  *Device Groups*:
        asvin's IoT platform provides updates for a group of devices. You can create a group to associate these devices by various categories
        such as, location, customer, deployment etc. You can add the target device to this group. Under *Devices > Device groups* click on 
        *"New Device Group"*. After this navigate back to the *"Just registered"* devices, click device 
        grouping and add the device to the newly created device group.         

3.  *File Groups*:
        Once your devices are assigned to a file group, the file you want to provide as an OTA update can be uploaded. 
        Usually this is *<new_firmware_file_name>.bin* or the type of file associated with the particular devices. 
        Let us show you in this example, the uploading of the esp-ota-blink.bin file to the filegroup ESP_OTA_Test
    
        .. image:: ../images/upload_file.png
            :width: 400pt
            :align: center

4.  *Rollout*:
        -   In this example we will setup a rollout to deliver OTA update of the file specified above to our target ESP8266 device.
            In the rollout section let us start by creating a rollout.
            Fill in the options as shown in the screenshot.
            Choose either batch/immediate update. 
            There is an option to choose a time or issue the update immediately.
            Select the file to be rolled out as update and click *Save*.

            .. image:: ../images/rollout_edited.png
                :width: 400pt
                :align: center

        -   The rollout is now enabled. Next time the defined device queries the  
            :ref:`Next Rollout` API, 
            the rollout will be available and further APIs will be called from that target device.
            The target device will update itself after this with the file we uploaded earlier. 

        -   Once the rollout is completed, the new file will be reflected on the target device. In this example we rolled out a BLink LED file. 
            The target device will call the :ref:`Rollout Success` API,
            which in this example is the part of the file that we uploaded earlier    

        -   The change in the firmware version of the device is also updated on the 
            `asvin platform <https://app.asvin.io/>`_  
    