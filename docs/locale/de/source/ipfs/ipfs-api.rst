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
 
         $ curl -X POST 'https://ipfs-server/firmware/download' \
         -H 'x-access-token: <JWT-TOKEN>' \
         --header 'Content-Type: application/json' \
         -d '{
             "cid": "QmWATWQ7fVPP2EFGu71UkfnqhYXDYH566qy47CnJDgvs8u"
         }'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'POST',
           'url': 'https://ipfs-server/firmware/download',
           'headers': {
             'x-access-token': '<JWT-TOKEN>',
             'Content-Type': 'application/json'
           },
           body: JSON.stringify({"cid":"QmWATWQ7fVPP2EFGu71UkfnqhYXDYH566qy47CnJDgvs8u"})

         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });


      .. code-tab:: python

         import requests

         url = "https://ipfs-server/firmware/download"
 
         payload="{\n    \"cid\": \"QmWATWQ7fVPP2EFGu71UkfnqhYXDYH566qy47CnJDgvs8u\"\n}"
         headers = {
           'x-access-token': '<JWT-TOKEN>',
           'Content-Type': 'application/json'
         }
         response = requests.request("POST", url, headers=headers, data=payload)
         print(response.text)
 

      .. code-tab:: php

         <?php
         $client = new http\Client;
         $request = new http\Client\Request;
         $request->setRequestUrl('https://ipfs-server/firmware/download');
         $request->setRequestMethod('POST');
         $body = new http\Message\Body;
         $body->append('{
             "cid": "QmWATWQ7fVPP2EFGu71UkfnqhYXDYH566qy47CnJDgvs8u"
         }');
         $request->setBody($body);
         $request->setOptions(array());
         $request->setHeaders(array(
           'x-access-token' => '<JWT-TOKEN>',
           'Content-Type' => 'application/json'
         ));
         $client->enqueue($request)->send();
         $response = $client->getResponse();
         echo $response->getBody();

 
   **Example response**:

   .. sourcecode:: byte

   :resheader Content-Type: application/json
      
   :statuscode 200: OK
   :statuscode 404: Not Found
