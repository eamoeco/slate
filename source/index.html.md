---
title: API Reference

language_tabs:
  - shell: cURL

toc_footers:
  - <a href='https://moeco.io'>About Moeco</a>
  - <a href='https://moecodocs.zendesk.com/hc/en-us'>Moeco Documentation</a>

includes:
  - errors

search: true
---

# Moeco API

The API is built on the basis of the HTTP protocol with the exchange of data in the JSON format. Communication between the server and the client is carried out through the interface end-points.

Each server response to a client request is represented by a set of HTTP status (status code) and a set of data of a specific structure:

The **meta** attribute contains service information and consists of the following attributes:

- total — total number of objects that meet the request criteria;
- count — a number of objects in the current response;
- offset — offset based on the request results in accordance with the total number of results and the current output size;
- error — contains information about the error during the execution of the request:
message — error message;
- details — additional information about the error (e.g., information about unsuccessful validation of request parameters, and etc.).

The **data** attribute directly contains the data obtained from the request and represents an array of objects. The representation of objects in the array may differ both between different interface end-points, and from request to request.

In order for the data to appear in response to requests for transactions, invoices, or payments, you may need to create them in the interface of the gate and the Masternode. How to do it, see the instructions How to check transactions, invoices and payments.

## Main request parameters

Parameter | Type | Default | Description
--------- | ------- | ----------- | -----------
authorization | string | - | Authorization token

You should use authorization token in all requests that you send.

## Verify authorization

POST /api/auth

Return an access token for other API endpoints.

> Example of a request:

```shell
curl -X POST "https://demo-dashboard.moeco.ninja/api/auth" -H "accept: application/json" -H "Content-Type: application/json" -d "{ "email": "test@me.com", "password": "123"}"
```

### Request

POST `https://demo-dashboard.moeco.ninja/api/auth`

### Request parameters

Parameter | Default | Description
--------- | ------- | -----------
email| - | The user email address
password| - | The user password

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 2523,
      "token_type": "bearer",
      "user_id": 1,
      "expires_at": "2020-08-12T12:29:20.408Z",
      "created_at": "2020-07-13T12:29:20.408Z",
      "updated_at": "2020-07-13T12:29:20.408Z",
      "access_token": "1dbb71a55488a16f60608ffece8777d8",
      "ip_address": null
    }
  ]
}
```

Parameter |Description
--------- | -----------
 id | Alert ID
 user_id | User ID
 token_type | Token type (bearer)
 access_token | Access token
 expires_at | Date and time when the token will expire
 created_at | Date and time when the token was create
 updated_at | Date and time when the token was updated
 ip_address | The user IP address

## Package list

GET /api/package

Return a package with information about alerts, devices and transactions.

> Example of a request:

```shell
curl -X GET "https://demo-dashboard.moeco.ninja/api/package?__count=20&__offset=0&only_active=true" -H "accept: application/json" -H "authorization: bearer 1dbb71a55488a16f60608ffece8777d8"
```

### Request

GET `https://demo-dashboard.moeco.io/api/package?count=20&offset=0&only_active=true`

### Request parameters

Parameter | Default | Description
--------- | ------- | -----------
count | 20 | Necessary rows count
offset | - | Offset
only_active| - | Get packages from actived sensors 

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 865,
      "user_id": 1,
      "device_hash": "33399974187546814930",
      "device_uid": "bb13d97189392984",
      "device_group_uid": "0b71c58eaf52a5e6",
      "status": 1,
      "destination": null,
      "created_at": "2020-06-02T08:17:49.033Z",
      "updated_at": "2020-06-02T08:17:49.033Z",
      "device_tags": [see tags part],
      "alert_events": [see alerts part],
      "transactions": [see transactions part]
    }
  ]
}
```

Parameter |Description
--------- | -----------
 id | Package ID
 user_id | The user ID
 device_hash | The sensor hash
 device_uid | The sensor UID
 device_group_uid | The sensor Group UID
 status | The package status (1 - active, 0 - not active)
 destination | TBD
 created_at | Date and time when the package was create
 updated_at | Date and time when the package was updated
 device_tags | The list of sensor tags
 alert_events | The list of alerts for this packages
 transactions | The transaction data
 
 
## Packages historical transactions by shipment ID

GET /api/device/search

Return a specific package by shipment ID

> Example of a request:

```shell
curl -X GET "https://demo-dashboard.moeco.io/api/search?&__order=updated_at+desc&__count=100&__offset=0&term=12345" -H "accept: application/json" -H "authorization: bearer 1dbb71a55488a16f60608ffece8777d8"
```

### Request

GET `https://demo-dashboard.moeco.io/api/search?order=updated_at+desc&count=100&offset=0&term=12345`

### Request parameters

Parameter | Default | Description
--------- | ------- | -----------
order | - | Query order type
count | 20 | Necessary rows count
offset | - | Offset
term | - | Shipment ID

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 865,
      "user_id": 1,
      "device_hash": "33399974187546814930",
      "device_uid": "bb13d97189392984",
      "device_group_uid": "0b71c58eaf52a5e6",
      "status": 1,
      "destination": null,
      "created_at": "2020-06-02T08:17:49.033Z",
      "updated_at": "2020-06-02T08:17:49.033Z",
      "device_tags": [see tags part],
      "alert_events": [see alerts part],
      "transactions": [see transactions part]
    }
  ]
}
```
Parameter |Description
--------- | -----------
 id | Package ID
 user_id | The user ID
 device_hash | The sensor hash
 device_uid | The sensor UID
 device_group_uid | The sensor Group UID
 status | The package status (1 - Init, 2 - On the way, 3 - Delivered, 4 - Lost, 5 - Canceled, 6 - Archived)
 destination | TBD
 created_at | Date and time when the transaction was create
 updated_at | Date and time when the transaction was updated
 device_tags | The list of sensor tags
 alert_events | The list of alerts for this packages
 transactions | The transaction data

## Alerts list

GET /api/alert

Return information about alerts settings

> Example of a request:

```shell
curl -X GET "https://demo-dashboard.moeco.io/api/alert?count=20&offset=0" -H "accept: application/json" -H "authorization: bearer 1dbb71a55488a16f60608ffece8777d8"
```

### Request

GET `https://demo-dashboard.moeco.io/api/alert?count=20&offset=0`

### Request parameters

Parameter | Default | Description
--------- | ------- | -----------
count | 20 | Necessary rows count
offset | - | Offset

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1095,
      "user_id": 1,
      "name": "Test alert",
      "sensor_name": "LOC",
      "sensor_params": "{\"ARRIVES_TO\":[{\"country\":\"ca\"}]}",
      "alert_type": 1,
      "alert_email": "1",
      "alert_phone": "0",
      "alert_status": 1,
      "created_at": "2020-07-13T13:47:33.050Z",
      "updated_at": "2020-07-13T13:47:33.050Z"
    }
  ]
}
```
Parameter |Description
--------- | -----------
 id | Package ID
 user_id | The user ID
 name | The alert name
 sensor_name | The sensor name
 sensor_params | The sensor alert settings
 alert_type | The alert type
 alert_email | Send or not alerts to email
 alert_phone | Send or not alerts to phone
 alert_status | The alert status
 created_at | Date and time when the alert was create
 updated_at | Date and time when the alert was updated

## Packages transactions

GET /api/transactions

Return data from sensors

> Example of a request:

```shell
curl -X GET "https://demo-dashboard.moeco.io/api/transactions?count=20&offset=0" -H "accept: application/json" -H "authorization: bearer eb2427956185ea8b744fe1473eec8e16"
```

### Request

GET `https://demo-dashboard.moeco.io/api/transactions?count=20&offset=0`

### Request parameters

Parameter | Default | Description
--------- | ------- | -----------
count | 20 | Necessary rows count
offset | - | Offset

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "qEzyg3IB3hSaPf0YgL7f",
      "source": {
        "device_hash": "89457387300000723687",
        "timestamp": "2020-06-05T09:56:25.000Z",
        "blockchain_id": "65e250241793b883c0a473a4373c68774bc93c1a16f1640d6b3b4f9181b4439b",
        "location": {
          "countryCode": "RU",
          "place_ids": [],
          "lt": 59.919047285714285,
          "lg": 30.454982714285716,
          "addr": null,
          "brand": "MTS",
          "operator": "Mobile TeleSystems"
        },
        "sensors": {
          "TEMP": 26,
          "HUMI": 37,
          "ORIENT": 2,
          "LIGHT": 0,
          "LINEBRK": 0,
          "MOTION": 0
        },
        "baseStations": [],
        "battery": 0,
        "alerts": [see alerts part],
        "alertCount": 0,
      }
    },
  ]
}
```
Parameter |Description
--------- | -----------
 id | The transaction ID
 source | The data in transaction
 source.device_hash | The device hash
 source.timestamp | The last time when the package transmitted status
 source.blockchain_id | The blockchain id 
 source.location | The location where the sensor was detected
 source.location.countryCode | The country code where sensor was detected
 source.location.brand | The brand of operator that we used to send data
 source.location.operator | The operator name that we used to send data
 source.location.lt | The location latitude
 source.location.lg | The location longitude
 source.location.addr | The location address (if we can get it)
 source.sensors | The data value from sensor
 source.alerts | The list of alerts
 source.alertCount | The number of alerts
