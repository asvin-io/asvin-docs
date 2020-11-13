Version Controller APIs
=======================
This section shows the Rest API end-points of Version Controller.

.. contents:: Table of contents
   :local:
   :backlinks: none
   :depth: 3

.. _Register Device:

Register Device
+++++++++++++++

.. http:post:: /api/device/register

   Register a device.

   :reqheader Content-Type: application/json

   **Example request**:

   .. tabs::

      .. code-tab:: bash
 
         $ curl --location --request POST 'https://vc-server/api/device/register' \
          --header 'Content-Type: application/json' \
          --data-raw '{
            "mac": "your-device-mac",
            "firmware_version": "1.0",
            "customer_key": "your-customer-key",
            "device_key": "your-device-key",
            "name": "Hello World",
            "class": "class1",
            "serial_number": "your-device-serial-number",
            "f1": "f1",
            "f2": "f2",
            "f3": "f3",
            "f4": "f4",
            "f5": "f5",
            "f6": "f6",
            "f7": "f7",
            "f8": "f8",
            "f9": "f9",
            "f10": "f10"
          }'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'POST',
           'url': 'https://vc-server/api/device/register',
           'headers': {
             'Content-Type': 'application/json'
           },
           body: JSON.stringify({"mac":"your-device-mac","firmware_version":"1.0","customer_key":"your-customer-key","device_key":"your-device-key","name":"Hello World","class":"class1","serial_number":"your-device-serial-number","f1":"f1","f2":"f2","f3":"f3","f4":"f4","f5":"f5","f6":"f6","f7":"f7","f8":"f8","f9":"f9","f10":"f10"})

         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });

      .. code-tab:: python

         import requests
         url = "https://vc-server/api/device/register"
         payload = "{\n\t\"mac\": \"your-device-mac\",\n\t\"firmware_version\": \"1.0\",\n\t\"customer_key\": \"your-customer-key\",\n\t\"device_key\": \"your-device-key\",\n\t\"name\": \"Hello World\",\n\t\"class\": \"class1\",\n\t\"serial_number\": \"your-device-serial-number\",\n\t\"f1\": \"f1\",\n\t\"f2\": \"f2\",\n\t\"f3\": \"f3\",\n\t\"f4\": \"f4\",\n\t\"f5\": \"f5\",\n\t\"f6\": \"f6\",\n\t\"f7\": \"f7\",\n\t\"f8\": \"f8\",\n\t\"f9\": \"f9\",\n\t\"f10\": \"f10\"\n}"
         headers = {
           'Content-Type': 'application/json'
         }
 
         response = requests.request("POST", url, headers=headers, data = payload)
         print(response.text.encode('utf8'))

      .. code-tab:: php
         
         <?php
         $client = new http\Client;
         $request = new http\Client\Request;
         $request->setRequestUrl('https://vc-server/api/device/register');
         $request->setRequestMethod('POST');
         $body = new http\Message\Body;
         $body->append('{
           "mac": "your-device-mac",
           "firmware_version": "1.0",
           "customer_key": "your-customer-key",
           "device_key": "your-device-key",
           "name": "Hello World",
           "class": "class1",
           "serial_number": "your-device-serial-number",
           "f1": "f1",
           "f2": "f2",
           "f3": "f3",
           "f4": "f4",
           "f5": "f5",
           "f6": "f6",
           "f7": "f7",
           "f8": "f8",
           "f9": "f9",
           "f10": "f10"
         }');
         $request->setBody($body);
         $request->setOptions(array());
         $request->setHeaders(array(
           'Content-Type' => 'application/json'
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();
 
   **Example response**:

   .. sourcecode:: json

      {
        "id": 21,
        "name": "Hello World",
        "macAddress": "your-device-mac",
        "created": "2020-09-11 11:33:46",
        "firmwareVersion": "1.0",
        "workspaceId": 1,
        "deviceGroupId": null,
        "transactionId": null,
        "blackListed": null,
        "customerKey": "your-customer-key",
        "serialNumber": "your-device-serial-number",
        "class": "class1",
        "f1": "f1",
        "f2": "f2",
        "f3": "f3",
        "f4": "f4",
        "f5": "f5",
        "f6": "f6",
        "f7": "f7",
        "f8": "f8",
        "f9": "f9",
        "f10": "f10",
        "deviceKey": null
      }

   :resheader Content-Type: application/json
      
   :statuscode 200: OK
   :statuscode 404: Not Found

.. _Next Rollout:

Next Rollout
++++++++++++

.. http:post:: /api/device/next/rollout

   Check next rollout

   :reqheader Content-Type: application/json

   **Example request**:

   .. tabs::

      .. code-tab:: bash
 
         curl --location --request POST 'https://vc-server/api/device/next/rollout' \
         --header 'Content-Type: application/json' \
         --data-raw '{
           "mac": "your-device-mac",
           "firmware_version": "1.0",
           "customer_key": "your-customer-key",
           "device_key": "your-device-key"
         }'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'POST',
           'url': 'https://vc-server/api/device/next/rollout',
           'headers': {
             'Content-Type': 'application/json'
           },
           body: JSON.stringify({"mac":"your-device-mac","firmware_version":"1.0","customer_key":"your-customer-key","device_key":"your-device-key"})
 
         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });

      .. code-tab:: python

         import requests
         url = "https://vc-server/api/device/next/rollout"
         payload = "{\n\t\"mac\": \"your-device-mac\",\n\t\"firmware_version\": \"1.0\",\n\t\"customer_key\": \"your-customer-key\",\n\t\"device_key\": \"your-device-key\"\n}"
         headers = {
           'Content-Type': 'application/json'
         }
         response = requests.request("POST", url, headers=headers, data = payload)
         print(response.text.encode('utf8'))

      .. code-tab:: php
         
         <?php
         $client = new http\Client;
         $request = new http\Client\Request;
         $request->setRequestUrl('https://vc-server/api/device/next/rollout');
         $request->setRequestMethod('POST');
         $body = new http\Message\Body;
         $body->append('{
           "mac": "your-device-mac",
           "firmware_version": "1.0",
           "customer_key": "your-customer-key",
           "device_key": "your-device-key"
         }');
         $request->setBody($body);
         $request->setOptions(array());
         $request->setHeaders(array(
           'Content-Type' => 'application/json'
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();
 
   **Example response**:

   .. sourcecode:: json

      {
        "id": "35",
        "name": "testrollout",
        "priority": "1",
        "start_date": "2020-09-23 06:07:04",
        "workspace_id": "1",
        "version": "2.0",
        "firmware_id": "4",
        "disabled": "0",
        "available_updates": "76",
        "device_group_id": "4",
        "device_ids": null,
        "device_id": "25"
      }

   :resheader Content-Type: application/json
      
   :statuscode 200: OK
   :statuscode 404: Not Found

.. _Rollout Success:

Rollout Success
+++++++++++++++

.. http:post:: /api/device/success/rollout

   Inform rollout status

   :reqheader Content-Type: application/json

   **Example request**:

   .. tabs::

      .. code-tab:: bash
 
         curl --location --request POST 'https://vc-server/api/device/success/rollout' \
         --header 'Content-Type: application/json' \
         --data-raw '{
           "mac": "your-device-mac",
           "firmware_version": "1.0",
           "customer_key": "your-customer-key",
           "device_key": "your-device-key",
           "rollout_id": "35"
         }'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'POST',
           'url': 'https://vc-server/api/device/success/rollout',
           'headers': {
             'Content-Type': 'application/json'
           },
           body: JSON.stringify({"mac":"your-device-mac","firmware_version":"1.0","customer_key":"your-customer-key","device_key":"your-device-key","rollout_id":"35"})
 
         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });

      .. code-tab:: python

         import requests
         url = "https://vc-server/api/device/success/rollout"
         payload = "{\n\t\"mac\": \"your-device-mac\",\n\t\"firmware_version\": \"1.0\",\n\t\"customer_key\": \"your-customer-key\",\n\t\"device_key\": \"your-device-key\",\n\t\"rollout_id\": \"35\"\n}"
         headers = {
           'Content-Type': 'application/json'
         }
         response = requests.request("POST", url, headers=headers, data = payload)
         print(response.text.encode('utf8'))

      .. code-tab:: php
         
         <?php
         $client = new http\Client;
         $request = new http\Client\Request;
         $request->setRequestUrl('https://vc-server/api/device/success/rollout');
         $request->setRequestMethod('POST');
         $body = new http\Message\Body;
         $body->append('{
           "mac": "your-device-mac",
           "firmware_version": "1.0",
           "customer_key": "your-customer-key",
           "device_key": "your-device-key",
           "rollout_id": "35"
         }');
         $request->setBody($body);
         $request->setOptions(array());
         $request->setHeaders(array(
           'Content-Type' => 'application/json'
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();
 
   **Example response**:

   .. sourcecode:: text

      25 //device id

   :resheader Content-Type: application/json
      
   :statuscode 200: OK
   :statuscode 404: Not Found