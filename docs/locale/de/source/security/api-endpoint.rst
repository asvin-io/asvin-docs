API Endpoint Security
=====================


asvin-Komponenten stellen ihre Dienste über RESTful-API-Endpunkte zur Verfügung. 
Sie werden mit Jason Web Token (JWT) gesichert. Es ist erforderlich, ein JWT vom 
OAuth-Server zu erhalten. Erst danach kann auf die Endpunkte erfolgreich zugegriffen 
werden. Der :ref:`Login` -API-Endpunkt wird verwendet, um JWT von OAuth zu erhalten.


.. _Device Signature:

Geräte-Signatur
################

Die in der Die :ref:`Login` -API verwendete :code:`device_signature` ist ein hashed-basierter 
Message Authentication Code (MAC). Er besteht aus einer kryptografischen Hash-Funktion 
(HMAC-SHA256) und einem geheimen Schlüssel. Im Pseudocode kann er als :code:`HMAC-SHA256(key, message)`. 
dargestellt werden. Hier ist die Nachricht :code:`timestamp+device_key` 
und der Schlüssel ist :code:`customer_key`. Die :code:`device_signature` wird also berechnet als

.. code-block::

   device_signature = HMAC-SHA256(customer_key, timestamp+device_key)

The customer_key and device_key are acquired from `Customer Platform <https://app.asvin.io>`_. One needs to make a account there. The code block below
shows the :code:`device_signature` generation.

Der customer_key und device_key werden von der `Customer Platform <https://app.asvin.io>`_ bezogen. 
Man muss dort ein Konto anlegen. Der Codeblock unten zeigt die Erzeugung der :code:`device_signature`

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