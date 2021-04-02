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
   :reqheader X-Access-Token: JWT-TOKEN

   **Example request**:

   .. tabs::

      .. code-tab:: bash cURL
 
         $ curl --location --request POST 'https://vc-server/api/device/register' \
          --header 'Content-Type: application/json' \
          --header 'X-Access-Token: <JWT-TOKEN>' \
          --data-raw '{
            "mac": "your-device-mac",
            "firmware_version": "1.0",
            "name": "device-name",
          }'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'POST',
           'url': 'https://vc-server/api/device/register',
           'headers': {
             'Content-Type': 'application/json',
             'X-Access-Token': '<JWT-TOKEN>'
           },
           body: JSON.stringify({"mac":"your-device-mac","firmware_version":"1.0","name":"device-name"})

         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });

      .. code-tab:: python

         import requests
         url = "https://vc-server/api/device/register"
         payload = "{\n\t\"mac\": \"your-device-mac\",\n\t\"firmware_version\": \"1.0\",\n\t\"name\": \"device-name\"\n}"
         headers = {
           'Content-Type': 'application/json',
           'X-Access-Token': '<JWT-TOKEN>'
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
           "name": "device-name",
         }');
         $request->setBody($body);
         $request->setOptions(array());
         $request->setHeaders(array(
           'Content-Type' => 'application/json',
           'X-Access-Token': '<JWT-TOKEN>'
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();
 
   **Example response**:

   .. sourcecode:: json

      {
        "message": "Device inserted!"
      }

   .. sourcecode:: json

      {
        "message": "Device exists!"
      }

   :resheader Content-Type: application/json
      
   :statuscode 200: No error
   :statuscode 404: Not Found
   :statuscode 401: JWT is not valid

.. _Next Rollout:

Next Rollout
++++++++++++

.. http:post:: /api/device/next/rollout

   Check next rollout

   :reqheader Content-Type: application/json
   :reqheader X-Access-Token: JWT-TOKEN

   **Example request**:

   .. tabs::

      .. code-tab:: bash cURL
 
         curl --location --request POST 'https://vc-server/api/device/next/rollout' \
         --header 'Content-Type: application/json' \
         --header 'X-Access-Token: <JWT-TOKEN>' \
         --data-raw '{
           "mac": "your-device-mac",
           "firmware_version": "1.0"
         }'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'POST',
           'url': 'https://vc-server/api/device/next/rollout',
           'headers': {
             'Content-Type': 'application/json',
             'X-Access-Token': '<JWT-TOKEN>'
           },
           body: JSON.stringify({"mac":"your-device-mac","firmware_version":"1.0"})
 
         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });

      .. code-tab:: python

         import requests
         url = "https://vc-server/api/device/next/rollout"
         payload = "{\n\t\"mac\": \"your-device-mac\",\n\t\"firmware_version\": \"1.0\"\n}"
         headers = {
           'Content-Type': 'application/json',
           'X-Access-Token': '<JWT-TOKEN>'
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
           "firmware_version": "1.0"
         }');
         $request->setBody($body);
         $request->setOptions(array());
         $request->setHeaders(array(
           'Content-Type' => 'application/json',
           'X-Access-Token': '<JWT-TOKEN>'
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();
 
   **Example response**:

   .. sourcecode:: json

      {
        "rollout_id": "84",
        "rollout_name": "new-demo-rollout",
        "priority": "1",
        "start_date": "2021-04-02 09:30:00",
        "version": "2.0",
        "firmware_id": "11"
      }

   .. sourcecode:: json

      {}   

   :resheader Content-Type: application/json
      
   :statuscode 200: No error
   :statuscode 404: Not Found
   :statuscode 401: JWT is not valid

.. _Rollout Success:

Rollout Success
+++++++++++++++

.. http:post:: /api/device/success/rollout

   Inform rollout status

   :reqheader Content-Type: application/json
   :reqheader X-Access-Token: JWT-TOKEN

   **Example request**:

   .. tabs::

      .. code-tab:: bash cURL
 
         curl --location --request POST 'https://vc-server/api/device/success/rollout' \
         --header 'Content-Type: application/json' \
         --header 'X-Access-Token: <JWT-TOKEN>' \
         --data-raw '{
           "mac": "your-device-mac",
           "firmware_version": "2.0"
           "rollout_id": "84"
         }'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'POST',
           'url': 'https://vc-server/api/device/success/rollout',
           'headers': {
             'Content-Type': 'application/json',
             'X-Access-Token': '<JWT-TOKEN>'
           },
           body: JSON.stringify({"mac":"your-device-mac","firmware_version":"2.0","rollout_id":"84"})
 
         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });

      .. code-tab:: python

         import requests
         url = "https://vc-server/api/device/success/rollout"
         payload = "{\n\t\"mac\": \"your-device-mac\",\n\t\"firmware_version\": \"2.0\",\n\t\"rollout_id\": \"84\"\n}"
         headers = {
           'Content-Type': 'application/json',
           'X-Access-Token': '<JWT-TOKEN>'
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
           "firmware_version": "2.0",
           "rollout_id": "84"
         }');
         $request->setBody($body);
         $request->setOptions(array());
         $request->setHeaders(array(
           'Content-Type' => 'application/json',
           'X-Access-Token': '<JWT-TOKEN>'
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();
 
   **Example response**:

   .. sourcecode:: json

      {
        "message": "Successfully inserted!"
      }

   .. sourcecode:: json

      {
        "message": "Existing Record"
      }

   :resheader Content-Type: application/json
      
   :statuscode 200: No error
   :statuscode 404: Not Found
   :statuscode 401: JWT is not valid