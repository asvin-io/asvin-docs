OAuth APIs
=======================
This section shows the Rest API end-points of OAuth Server.

.. contents:: Table of contents
   :local:
   :backlinks: none
   :depth: 3

.. _login:

Login
+++++

.. http:post:: /auth/login

   Get token

   :reqheader Content-Type: application/json

   **Example request**:

   .. tabs::

      .. code-tab:: bash
 
         $ curl --location --request POST 'https://oauth-server/auth/login' \
          --header 'Content-Type: application/json' \
          --data-raw '{
              "customer_key": "your-customer-key",
              "device_key": "your-device-key"
          }'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'POST',
           'url': 'https://oauth-server/auth/login',
           'headers': {
             'Content-Type': 'application/json'
           },
           body: JSON.stringify({"customer_key":"your-customer-key","device_key":"your-device-key"})
 
         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });

      .. code-tab:: python

         import requests
         url = "https://oauth-server/auth/login"
         payload="{\n\"customer_key\": \"your-customer-key\",\n\"device_key\": \"your-device-key\"\n}"
         headers = {
           'Content-Type': 'application/json'
         }
         response = requests.request("POST", url, headers=headers, data=payload)
         print(response.text)

      .. code-tab:: php
         
         <?php
         $client = new http\Client;
         $request = new http\Client\Request;
         $request->setRequestUrl('https://oauth-server/auth/login');
         $request->setRequestMethod('POST');
         $body = new http\Message\Body;
         $body->append('{
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
        "token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJpYXQiOjE2MDYunDk4ODYsImV4cCI6MTYwNjMxMDQ4Nn0.CCWvzR124OGf5FFOFAObQDPNRlmtI_kaObtu0X-eNFpJUaHv5kfjfGzZl4PUVXTOidSC4SJXFLACqOgyY7gb1UiHI3S47KvhIdCLgte8BvEIyIWLLj4rD4mdWT4NeRkP67-AXUG9IVM7_6XaGB-xmVLD-cLKFimlH7wANeDxO51gOgbcO5CP-1LQKuc2ApYPnDwtJMbkLIcQ-f7k81ouiiOWKOsB-cXq8yqt85WV4BJADhTDbvm3kjAQ5AEOpi7cU_sxh4JG4RaFKz7mNAanvHTw7LbZmP6tcvcf-bvcqTkkb0nkstXCD6300mBe4D44gY-7OehM1HF7xUS6nYpnIw"
      }

   :resheader Content-Type: application/json
      
   :statuscode 200: OK
   :statuscode 404: Not Found