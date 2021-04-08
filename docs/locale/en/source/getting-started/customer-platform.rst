Asvin Customer Platform
=======================

Asvin IoT platform provides secure OTA updates for IoT devices. Lets us get started with using the platform.

1.  *Register Device*:
        When you start and upload your code on any of the supported boards in the 
        :doc:`../tutorials/tutorials` section, the board will start executing 
        and calling the defined API routes. To Register the device the 
        :ref:`Register Device` API is called.
        After this API is sucessfully called, you will see your device appear
        under the "Just Registered devices" section of the platfomr under devices. 

        .. image:: ../images/register_edited.jpg
            :width: 400pt
            :align: center


2.  *Device Groups*:
        Asvin's IoT platform provides updates for a group of devices. We can create a group to associate these devices by various categories
        such as, location, customer, deployment etc. We can add our target device to this group. Under Devices > Device groups click on 
        *"New Device Group"*. After this navigate back to the "Just registered" devices, click device 
        grouping and add the device to the newly created device group.         

3.  *File Groups*:
        Once our devics are assigned to a file group. We can upload a file we want to provide as an OTA 
        update. Usually this is *<somefile_name>.bin* or the type of file associated with our particular devices. 
        Let us in this example upload the esp-ota-blink.bin file to the filegroup ESP_OTA_Test
    
        .. image:: ../images/upload_file.png
            :width: 400pt
            :align: center

4.  *Rollout*:
        -   In this example we will setup a rollout to deliver OTA update of the file specified above to our target ESP8266 device.
            In the rollout section let us start by creating a rollout.
            Fill in the options as shown in the screenshot.
            Choose either batch/immediate update. 
            There is an option to choose a time or do an update immediately.
            Select the file to be rolled out as update and click *Save* 

            .. image:: ../images/rollout_edited.jpg
                :width: 400pt
                :align: center

        -   The rollout is now enabled. Next time our device queries the  
            :ref:`Next Rollout` API, 
            the rollout will be avaliable and further API's will be called from our target device.
            The target device will update itself after this with the file we uploaded earlier. 

        -   Once the rollout is completed the new file will be refelected on the target device. In this example we rolled out a BLink LED file. 
            The target device will call the :ref:`Rollout Success` API,
            which in this example is the part of the file that we uploaded earlier    

        -   The change in the firmware version of the device is also updated on the 
            `Asvin platform <https://app.asvin.io/>`_  
    