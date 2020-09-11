Version Controller APIs
=======================
This section shows the basic entity requests used in the APIs of the Version Controller.

.. contents:: Table of contents
   :local:
   :backlinks: none
   :depth: 3

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
            "mac": "AC:12:CC:22:34:D3",
            "firmware_version": "1.0",
            "customer_key": "3c2ecv57d6d3ee718ec4e4695ae271ad",
            "device_key": "9db3e154bv1788db1acb158f9cca20f47e1dd3b2c669365fcd19333118bc65fa",
            "name": "Hello World",
            "class": "class1",
            "serial_number": "12212112212",
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
           body: JSON.stringify({"mac":"AC:12:CC:22:34:D3","firmware_version":"1.0","customer_key":"3c2eb557d6d3ee718ec4e4695ae271ad","device_key":"9db3e1546c1788db1acb158f9cca20f47e1dd3b2c669365fcd19333118bc65fa","name":"Hello World","class":"class1","serial_number":"12212112212","f1":"f1","f2":"f2","f3":"f3","f4":"f4","f5":"f5","f6":"f6","f7":"f7","f8":"f8","f9":"f9","f10":"f10"})

         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });

      .. code-tab:: python

         import requests
         url = "https://vc-server/api/device/register"
         payload = "{\n\t\"mac\": \"AC:12:CC:22:34:D3\",\n\t\"firmware_version\": \"1.0\",\n\t\"customer_key\": \"3c2eb557d6d3ee718ec4e4695ae271ad\",\n\t\"device_key\": \"9db3e1546c1788db1acb158f9cca20f47e1dd3b2c669365fcd19333118bc65fa\",\n\t\"name\": \"Hello World\",\n\t\"class\": \"class1\",\n\t\"serial_number\": \"12212112212\",\n\t\"f1\": \"f1\",\n\t\"f2\": \"f2\",\n\t\"f3\": \"f3\",\n\t\"f4\": \"f4\",\n\t\"f5\": \"f5\",\n\t\"f6\": \"f6\",\n\t\"f7\": \"f7\",\n\t\"f8\": \"f8\",\n\t\"f9\": \"f9\",\n\t\"f10\": \"f10\"\n}"
         headers = {
           'Content-Type': 'application/json'
         }
 
         response = requests.request("POST", url, headers=headers, data = payload)
         print(response.text.encode('utf8'))

      .. code-tab:: php
         
         <?php
         $client = new http\Client;
         $request = new http\Client\Request;
         $request->setRequestUrl('https://vcstage.asvin.io/api/device/register');
         $request->setRequestMethod('POST');
         $body = new http\Message\Body;
         $body->append('{
           "mac": "AC:12:CC:22:34:D3",
           "firmware_version": "1.0",
           "customer_key": "3c2eb557d6d3ee718ec4e4695ae271ad",
           "device_key": "9db3e1546c1788db1acb158f9cca20f47e1dd3b2c669365fcd19333118bc65fa",
           "name": "Hello World",
           "class": "class1",
           "serial_number": "12212112212",
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
        "macAddress": "AC:12:CC:22:34:D3",
        "created": "2020-09-11 11:33:46",
        "firmwareVersion": "1.0",
        "workspaceId": 1,
        "deviceGroupId": null,
        "transactionId": null,
        "blackListed": null,
        "customerKey": "3c2eb557d6d3ee718ec4e4695ae271ad",
        "serialNumber": "12212112212",
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