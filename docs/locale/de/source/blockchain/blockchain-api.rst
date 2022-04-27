Blockchain APIs
===============
This section shows the Rest API end-points of Blockchain.

.. contents:: Table of contents
   :local:
   :backlinks: none
   :depth: 3

Get Device
++++++++++

.. http:get:: /device/:id

   Get a device.

   :reqheader Content-Type: application/json
   :reqheader X-Access-Token: JWT-TOKEN

   **Example request**:

   .. tabs::

      .. code-tab:: bash cURL
 
         $ curl 'https://bc-server/device/:id' \
         -H 'Content-Type: application/json' \
         -H 'X-Access-Token: <JWT-TOKEN>

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'GET',
           'url': 'https://bc-server/device/:id',
           'headers': {
             'X-Access-Token': '<JWT-TOKEN>'
           },
           body: JSON.stringify({"id":"<device-id>"})
 
         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });


      .. code-tab:: python

         import requests

         url = "https://bc-server/device/:id"
 
         headers = {
           'X-Access-Token': '<JWT-TOKEN>'
         }
         response = requests.request("GET", url, headers=headers)
 

      .. code-tab:: php

         <?php
         $client = new http\Client;
         $request = new http\Client\Request;
         $request->setRequestUrl('https://bc-server/device/:id');
         $request->setRequestMethod('GET');
         
         $request->setOptions(array());
         $request->setHeaders(array(
           'X-Access-Token' => '<JWT-TOKEN>'
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();
 
   **Example response**:

   .. sourcecode:: json

      {
        "mac": "AC:AC:CC:CC:34:34",
        "fwId": "3",
        "dType": "ESP"
      }

   :resheader Content-Type: application/json
      
   :statuscode 200: OK
   :statuscode 404: Not Found

Get Firmware
++++++++++++

.. http:get:: /firmware/:id

   Get a device.

   :reqheader Content-Type: application/json
   :reqheader X-Access-Token: JWT-TOKEN

   **Example request**:

   .. tabs::

      .. code-tab:: bash cURL
 
         $ curl 'https://bc-server/device/:id' \
         -H 'X-Access-Token: <JWT-TOKEN> 

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'GET',
           'url': 'https://bc-server/firmware/:id',
           'headers': {
             'X-Access-Token': '<JWT-TOKEN>'
           })
 
         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });


      .. code-tab:: python

         import requests

         url = "https://bc-server/firmware/:id"
 
         headers = {
           'X-Access-Token': '<JWT-TOKEN>'
         }
         response = requests.request("GET", url, headers=headers)
         print(response.text)
 

      .. code-tab:: php

         <?php
         $client = new http\Client;
         $request = new http\Client\Request;
         $request->setRequestUrl('https://bc-server/firmware/:id');
         $request->setRequestMethod('GET');
         $request->setOptions(array());
         $request->setHeaders(array(
           'X-Access-Token' => '<JWT-TOKEN>'
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();

 
   **Example response**:

   .. sourcecode:: json

      {
        "md": "6f5902ac237024bdd0c176cb93063dc4",
        "cid": "QmWATWQ7fVPP2EFGu71UkfnqhYXDYH566qy47CnJDgvs8u",
        "version": "1.9",
      } 

   :resheader Content-Type: application/json
      
   :statuscode 200: OK
   :statuscode 404: Not Found

