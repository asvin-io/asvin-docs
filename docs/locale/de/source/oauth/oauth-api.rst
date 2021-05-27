OAuth APIs
==========

Dieser Abschnitt zeigt die Rest-API-Endpunkte von OAuth Server.

.. contents:: Inhaltsübersicht
   :local:
   :backlinks: none
   :depth: 3

.. _Login:

Login
+++++

Dieser API-Endpunkt gibt ein Token zurück, das dem **x-access-token** Header für alle anderen API-Anfragen hinzugefügt werden sollte.

.. http:post:: /auth/login

   Der :code:`device_key` und der :code:`customer_key` werden aus dem asvin Dashboard bezogen. Der The :code:`timestamp` 
   ist eine Unix-Epoche, die :code:`device_signature` ist `HMAC-SHA256 <https://en.wikipedia.org/wiki/HMAC/>`_. 
   Der Abschnitt Gerätesignatur enthält Details zur Berechnung.

   :reqheader Content-Type: application/json

   **Example request**:

   .. tabs::

      .. code-tab:: bash cURL
 
         $ curl --location --request POST 'https://oauth-server/auth/login' \
          --header 'Content-Type: application/json' \
          --data-raw '{
              "device_key": "your-device-key",
              "timestamp": 1620045991
              "device_signature": "your-device-signature"
          }'

      .. code-tab:: js

         var request = require('request');
         var options = {
           'method': 'POST',
           'url': 'https://oauth-server/auth/login',
           'headers': {
             'Content-Type': 'application/json'
           },
           body: JSON.stringify({"device_key":"your-device-key","timestamp": 1620045991,"device_signature":"your-device-signature"})
 
         };
         request(options, function (error, response) {
           if (error) throw new Error(error);
           console.log(response.body);
         });

      .. code-tab:: python

         import requests
         url = "https://oauth-server/auth/login"
         payload="{\"device_key\":\"your-device-key\",\"timestamp\":1620045991,\"device_signature\":\"your-device_signature\"}"
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
             "device_key": "your-device-key",
             "timestamp": 1620045991,
             "device-signature": "your-device_signature",
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
   :resheader X-RateLimit-Limit: 10
   :resheader X-RateLimit-Remaining: 9 
   :resheader X-RateLimit-Reset: 1617352926
      
   :statuscode 200: OK
   :statuscode 429: Zu viele Anfragen im gewünschten Zeitraum
   :statuscode 500: Error on Server
   
   