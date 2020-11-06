Blockchain APIs
===============
This section shows the Rest API end-points of Blockchain.

.. contents:: Table of contents
   :local:
   :backlinks: none
   :depth: 3

Get Device
++++++++++

.. http:post:: /device/get

   Get a device.

   :reqheader Content-Type: application/json

   **Example request**:

   .. tabs::

      .. code-tab:: bash
 
         $ curl -X POST 'https://bc-server/device/get' \
         -H 'Content-Type: application/json' \
         -H 'x-access-token: <your-token> \
         -d '{
           "id": "<device-id>"
         }'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'POST',
           'url': 'https://bc-server/device/get',
           'headers': {
             'Content-Type': 'application/json',
             'x-access-token': '<your-token>'
           },
           body: JSON.stringify({"id":"<device-id>"})
 
         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });


      .. code-tab:: python

         import requests

         url = "https://bc-server/device/get"
 
         payload="{\n\t\"id\": \"device-id\"\n}"
         headers = {
           'Content-Type': 'application/json',
           'x-access-token': '<your-token>'
         }
         response = requests.request("POST", url, headers=headers, data=payload)
         print(response.text)
 

      .. code-tab:: php

         <?php
         $client = new http\Client;
         $request = new http\Client\Request;
         $request->setRequestUrl('https://bc-server/device/get');
         $request->setRequestMethod('POST');
         $body = new http\Message\Body;
         $body->append('{
           "id" : "<device-id>"
         }');
         $request->setBody($body);
         $request->setOptions(array());
         $request->setHeaders(array(
           'Content-Type' => 'application/json',
           'x-access-token' => '<your-token>'
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();
 
   **Example response**:

   .. sourcecode:: json

      {
        "valid": true,
        "id": "3",
        "message": "Device with id 3 got successfully",
        "Device": {
            "id": "3",
            "mac": "AC:AC:CC:CC:34:34",
            "type": "ESP",
            "fwId": "3",
            "wsId": "1",
            "description": "3 - asvin demo device"
        }
      }

   :resheader Content-Type: application/json
      
   :statuscode 200: OK
   :statuscode 404: Not Found

Get Firmware
++++++++++++

.. http:post:: /firmware/get

   Get a device.

   :reqheader Content-Type: application/json

   **Example request**:

   .. tabs::

      .. code-tab:: bash
 
         $ curl -X POST 'https://bc-server/device/get' \
         -H 'Content-Type: application/json' \
         -H 'x-access-token: <your-token> \
         -d '{
           "id": "<firmware-id>"
         }'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'POST',
           'url': 'https://bc-server/firmware/get',
           'headers': {
             'Content-Type': 'application/json',
             'x-access-token': '<your-token>'
           },
           body: JSON.stringify({"id":"<firmware-id>"})
 
         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });


      .. code-tab:: python

         import requests

         url = "https://bc-server/firmware/get"
 
         payload="{\n\t\"id\": \"firmware-id\"\n}"
         headers = {
           'Content-Type': 'application/json',
           'x-access-token': '<your-token>'
         }
         response = requests.request("POST", url, headers=headers, data=payload)
         print(response.text)
 

      .. code-tab:: php

         <?php
         $client = new http\Client;
         $request = new http\Client\Request;
         $request->setRequestUrl('https://bc-server/firmware/get');
         $request->setRequestMethod('POST');
         $body = new http\Message\Body;
         $body->append('{
           "id" : "<firmware-id>"
         }');
         $request->setBody($body);
         $request->setOptions(array());
         $request->setHeaders(array(
           'Content-Type' => 'application/json',
           'x-access-token' => '<your-token>'
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();

 
   **Example response**:

   .. sourcecode:: json

      {
        "valid": true,
        "id": "45",
        "message": "Firmware with id 45 got successfully",
        "Firmware": {
            "id": "45",
            "md": "6f5902ac237024bdd0c176cb93063dc4",
            "cid": "QmWATWQ7fVPP2EFGu71UkfnqhYXDYH566qy47CnJDgvs8u",
            "version": "1.9",
            "description": "45 - asvin demo fw"
        }
      } 

   :resheader Content-Type: application/json
      
   :statuscode 200: OK
   :statuscode 404: Not Found

