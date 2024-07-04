Device Registration
===================

At this stage, you have created an account on the Device Security Booster™, received the customer and device keys, and imported asvin api collection on postman
application. It is time to register your first device. Go to you postman collection and open Register Device POST request located in the Version 
Controller folder. In the request, enter desired device name, current firmware version, and valid MAC address. Next, all you have to do is click on
big blue button named Send. You will received device inserted message if the request is accepted. You can go the dashboard and check it in Devices
menu. It will appear under Lobby sub-menu. The process is shown in video below.

.. raw:: html

  <video width="710" autoplay muted loop>
  <source src="../_static/videos/device-registration.m4v" type="video/mp4">
  Your browser does not support the video tag.
  </video>

Next, you need to create a device group and add the device in it to complete the registration. You will not be able to create rollout for the device
until you add it in a device group. Click on New device group button under Devices->Grouped menu to add a device group. Once you have a device group,
go to Lobby, select the device and click on Group to add it in a desired device group. The procedure to add a device group and grouping a device is 
shown below.

.. raw:: html

  <video width="710" autoplay muted loop>
  <source src="../_static/videos/device-group.m4v" type="video/mp4">
  Your browser does not support the video tag.
  </video>

At the end of this task, you will have a device registered, grouped in a device group and stored on distributed ledger.