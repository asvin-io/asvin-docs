IPFS APIs
=========
This section shows the Rest API end-points of IPFS.

.. contents:: Table of contents
   :local:
   :backlinks: none
   :depth: 3

Download Firmware 
+++++++++++++++++

.. http:get:: /firmware:id

   Get a device.

   :reqheader Content-Type: application/json
   :reqheader x-access-token: JWT-TOKEN

   **Example request**:

   .. tabs::

      .. code-tab:: bash cURL
 
         $ curl -X GET 'https://ipfs-server/firmware/:cid' \
         -H 'x-access-token: <JWT-TOKEN>' \
         --header 'Content-Type: application/json'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'GET',
           'url': 'https://ipfs-server/firmware/:cid',
           'headers': {
             'x-access-token': '<JWT-TOKEN>',
           },
         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });


      .. code-tab:: python

         import requests

         url = "https://ipfs-server/firmware/:cid"
 
         headers = {
           'x-access-token': '<JWT-TOKEN>',
         }
         response = requests.request("GET", url, headers=headers)
         print(response.text)
 

      .. code-tab:: php

         <?php
         $client = new http\Client;
         $request = new http\Client\Request;
         $request->setRequestUrl('https://ipfs-server/firmware/:cid');
         $request->setRequestMethod('GET');
         $body = new http\Message\Body;
         
         $request->setOptions(array());
         $request->setHeaders(array(
           'x-access-token' => '<JWT-TOKEN>',
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();

 
   **Example response**:

   .. sourcecode:: byte

   :resheader Content-Type: application/json
      
   :statuscode 200: OK
   :statuscode 404: Not Found
