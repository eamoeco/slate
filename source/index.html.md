---
title: API Reference

language_tabs:
  - shell: cURL
  - ruby: Ruby
  - php: PHP
  - python: Python

toc_footers:
  - <a href='https://www.travelpayouts.com/'>Sign Up for a Developer Token</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - dataapiv1
  - dataapiv2
  - dataapijson
  - searchapi
  - hotelsdata
  - hotelstatdata
  - hotelssearchapi
  - hotelapierrors

search: true
---

# Moeco API

The API is built on the basis of the HTTP protocol with the exchange of data in the JSON format. Communication between the server and the client is carried out through the interface end-points.

Each server response to a client request is represented by a set of HTTP status (status code) and a set of data of a specific structure:

The meta attribute contains service information and consists of the following attributes:

- total — total number of objects that meet the request criteria;
- count — a number of objects in the current response;
- offset — offset based on the request results in accordance with the total number of results and the current output size;
- error — contains information about the error during the execution of the request:
message — error message;
- details — additional information about the error (e.g., information about unsuccessful validation of request parameters, and etc.).

The **data** attribute directly contains the data obtained from the request and represents an array of objects. The representation of objects in the array may differ both between different interface end-points, and from request to request.

In order for the data to appear in response to requests for transactions, invoices, or payments, you may need to create them in the interface of the gate and the Masternode. How to do it, see the instructions How to check transactions, invoices and payments.

## Main request parameters

Parameter | Default | Description
--------- | ------- | -----------
api_key | 66de8f264ceeae860b8a2decca9d3379 | User API key
hash | 975cb454-72d9-4832-80c5-b7162c215208 | Gate hash
Authorization | Gateway: e0265e2d-b702-490a-96a3-8ea596c4f0aa | Gateway hash

## Verify authorization

GET gate/auth

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.ninja/api/alert \
  --header 'Authorization: Gateway: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
  --header 'api_key: 66de8f264ceeae860b8a2decca9d3379'
```

```ruby
require 'uri'
require 'net/https'

url = URI("https://demo-dashboard.moeco.ninja/api/alert")

https = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["api_key"] = '66de8f264ceeae860b8a2decca9d3379'

response = https.request(request)
puts response.read_body
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://demo-dashboard.moeco.ninja/api/alert",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "api_key: 66de8f264ceeae860b8a2decca9d3379"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

```python
import requests

url = "https://demo-dashboard.moeco.ninja/api/alert"

headers = {'api_key': '66de8f264ceeae860b8a2decca9d3379'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

### Request

GET `https://demo-dashboard.moeco.ninja/api/alert?__order=&__count=20&__offset=&term=`

### Request parameters

Parameter | Default | Description
--------- | ------- | -----------
__order | - | Query order
__count | 20 | Necessary rows count
__offset | - | Offset
name | - | Alert name. Length of string must be less than, or equal to 255. Length of string must be greater than, or equal to 3
device_group_uid | - | Device group UID
sensor_name | - | Sensor name
sensor_params | - | Sensor params
alert_status | 1 | Alert status 0/1


### Response

> The above command returns JSON structured like this:

```json
{
  "name": "Test alert",
  "device_group_uid": "aabbccss",
  "sensor_name": "LOC",
  "sensor_params": "{\"ARRIVES_TO\":[{\"country\":\"RU\",\"region\":\"Moscow\"}]}",
  "alert_status": 1,
  "alert_type": 1,
  "alert_email": "1",
  "alert_phone": "1"
}
```

Parameter |Description
--------- | -----------
 id | Alert ID
 user_id | User ID
 name | Alert name
 device_group_uid | Device group UID
 sensor_name | Sensor name
 sensor_params | Sensor params
 alert_type | Alert type
 alert_email | True if we should send alert to the email
 alert_phone |  True if we should send alert to the phone
 alert_status | Alert status
 created_at | Date and time when alert was create
 updated_at | Date and time when alert was updated
