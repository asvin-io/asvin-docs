API Endpoint Security
=====================

asvin components expose their services using RESTful API endpoints. They are secured using Jason Web Token(JWT). It is required to obtain a JWT from
OAuth server. Only thereafter the endpoints can accessed successfully. The :ref:`Login` API endpoint is used to get JWT from OAuth. 

.. _Device Signature:

Device Signature
################
The :code:`device_signature` used in the The :ref:`Login` API is a hashed-based message authentication code (MAC). It consists of cryptographic hash 
function (HMAC-SHA256) and secret key. In psuedocode, it can be illustrated as :code:`HMAC-SHA256(key, message)`. Here, message is :code:`timestamp+device_key` and key is :code:`customer_key`. So, the 
:code:`device_signature` is calculated as::

  device_signature = HMAC-SHA256(customer_key, timestamp+device_key)

The customer_key and device_key are acquired from `Customer Platform <https://app.asvin.io>`_. One needs to make a account there. The code block below
shows the :code:`device_signature` generation.

.. tabs::

  .. code-tab:: bash 

     #!/bin/bash
     customer_key="my-customer-key"
     device_key="my-device-key"
     timestamp=$(date +%s)
     device_signature=$(echo -n $timestamp$device_key | openssl dgst -sha256 -hmac $customer_key)
     echo $device_signature
 
  .. code-tab:: python

     import hmac
     import hashlib
     from time import time
     customer_key = "my-customer-key"
     device_key = "my-device-key"
     timestamp = str(math.floor(time()))
     device_signature = hmac.new(customer_key, msg=timestamp+device_key, digestmod=hashlib.sha256).hexdigest().upper()
     print device_signature
  

  .. code-tab:: js

     const CryptoJS = require("crypto-js");
     const dateNow = new Date();
     const customerKey = "my-customer-key";
     const deviceKey =  "my-device-key";
     const timestamp = Math.floor(dateNow.getTime() / 1000);
     const deviceSignature = CryptoJS.HmacSHA256(timestamp + deviceKey, customerKey).toString(CryptoJS.digest);
     console.log(deviceSignature)