Account Registration
====================

asvin Beehive provides an interactive dashboard to visualize and manages devices, firmware, and rollouts. It is necessary to create an account 
on the asvin Beehive to use asvin services. The process is quite simple. All you need is a valid email address. Go to the register page, input your
email address, select couple of check boxes and click on Register now. It is shown below.   

.. raw:: html

  <video width="600" autoplay muted>
  <source src="../_static/videos/acc-registration.m4v" type="video/mp4">
  Your browser does not support the video tag.
  </video>

When everything goes well, you will receive an email for setting up password for your account. Click on Account Activation, it will take you to a web
page. There you can create your password. You need to take care of asvin's password guidelines.Your password should contain

* at least 10 characters
* at least one big letter and one small letter
* at least one number
* at least one special character

Once you enter valid password and click on Create a password button, it will land you to the home page of the dashboard. The process is shown below.

.. raw:: html

  <video width="600" autoplay muted>
  <source src="../_static/videos/acc-activation.m4v" type="video/mp4">
  Your browser does not support the video tag.
  </video>

asvin uses access keys to manage unauthorized access to the api end-points. Theses access keys are customer key and device key. The keys are generated
automatically when an account is created for the first time. You can access the keys in My Account -> Settings section as shown in the picture below.

.. image:: ../images/access-keys.png
            :width: 400pt
            :align: center

The keys will be used to get OAUTH token.