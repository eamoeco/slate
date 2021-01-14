# Masternode API 

## Main request parameters

You should use authorization token in all requests that you send.

Header | Type | Default | Description | Example
--------- | ------- | ----------- | ----------- | -----------
authorization | string | - | Authorization token | bearer 1dbb71a55488a16f60608ffece8777d8

## Authorization

POST /api/auth

Return an access token for other API endpoints.

> Example of a request:

```shell
curl -X POST "https://demo-dashboard.moeco.io/api/auth" -H "accept: application/json" -H "Content-Type: application/json" -d "{ "email": "test@me.com", "password": "123"}"
```

### Request

POST `https://demo-dashboard.moeco.io/api/auth`

### Request parameters

Payload | Default | Description
--------- | ------- | -----------
email| - | The user login
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

Field |Description
--------- | -----------
 id | The token ID
 user_id | The user ID
 token_type | The token type (bearer)
 access_token | The access token value
 expires_at | Date and time when the token will expire
 created_at | Date and time when the token was created
 updated_at | Not used
 ip_address | The user IP address

## Verify authorization

GET /api/auth

Verify the access token.

> Example of a request:

```shell
curl -X GET "https://demo-dashboard.moeco.io/api/auth" -H  "accept: application/json" -H  "authorization: Bearer 1dbb71a55488a16f60608ffece8777d8"
```

### Request

GET `https://demo-dashboard.moeco.io/api/auth`

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

Field |Description
--------- | -----------
 id | The token ID
 user_id | The user ID
 token_type | The token type (bearer)
 access_token | The access token value
 expires_at | Date and time when the token will expire
 created_at | Date and time when the token was created
 updated_at | Not used
 ip_address | The user IP address

## Shipment list

GET /api/package 

Returns list of shipments with basic information about sensors, transactions and alerts.

> Example of a request:

```shell
curl -X GET "https://demo-dashboard.moeco.io/api/package?__count=20&__offset=0&only_active=true" -H "accept: application/json" -H "authorization: bearer 1dbb71a55488a16f60608ffece8777d8"
```

### Request

GET `https://demo-dashboard.moeco.io/api/package?__count=20&__offset=0&only_active=true`

### Request parameters

Query | Default | Description
--------- | ------- | -----------
__count | 20 | Necessary rows count
__offset | - | Offset
only_active | - | Get packages from actived sensors 

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

Field |Description
--------- | -----------
 id | Package ID
 user_id | The user ID
 device_hash | The sensor hash
 device_uid | The sensor UID
 device_group_uid | The sensor Group UID
 status | The shipment status (1 - active, 0 - not active)
 destination | TBD
 created_at | Date and time when the shipment was create
 updated_at | Date and time when the shipment was updated
 device_tags | The list of sensor tags
 alert_events | The list of alerts for this shipments
 transactions | The transaction data
 
 
## Shipments historical transactions by shipment ID

GET /api/device/search

Returns the single shipments with basic information about sensors, transactions and alerts by its ID.

> Example of a request:

```shell
curl -X GET "https://demo-dashboard.moeco.io/api/search?__order=updated_at+desc&__count=100&__offset=0&term=12345" -H "accept: application/json" -H "authorization: bearer 1dbb71a55488a16f60608ffece8777d8"
```

### Request

GET `https://demo-dashboard.moeco.io/api/search?__order=updated_at+desc&__count=100&__offset=0&term=12345`

### Request parameters

Query | Default | Description
--------- | ------- | -----------
__order | - | Query order type
__count | 20 | Necessary rows count
__offset | - | Offset
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

Field |Description
--------- | -----------
 id | The shipment ID
 user_id | The user ID
 device_hash | The sensor hash
 device_uid | The sensor UID
 device_group_uid | The sensor Group UID
 status | The shipment status (1 - Init, 2 - On the way, 3 - Delivered, 4 - Lost, 5 - Canceled, 6 - Archived)
 destination | TBD
 created_at | Date and time when the transaction was create
 updated_at | Date and time when the transaction was updated
 device_tags | The list of sensor tags
 alert_events | The list of alerts for this shipments
 transactions | The transaction data

## Alerts list

GET /api/alert

Return information about alerts settings

> Example of a request:

```shell
curl -X GET "https://demo-dashboard.moeco.io/api/alert?__count=20&__offset=0" -H "accept: application/json" -H "authorization: bearer 1dbb71a55488a16f60608ffece8777d8"
```

### Request

GET `https://demo-dashboard.moeco.io/api/alert?count=20&offset=0`

### Request parameters

Query | Default | Description
--------- | ------- | -----------
__count | 20 | Necessary rows count
__offset | - | Offset

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

Field |Description
--------- | -----------
 id | The shipment ID
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

## Shipments transactions

GET /api/transactions

Return data from sensors

> Example of a request:

```shell
curl -X GET "https://demo-dashboard.moeco.io/api/transactions?__count=20&__offset=0" -H "accept: application/json" -H "authorization: bearer eb2427956185ea8b744fe1473eec8e16"
```

### Request

GET `https://demo-dashboard.moeco.io/api/transactions?__count=20&__offset=0`

### Request parameters

Query | Default | Description
--------- | ------- | -----------
__count | 20 | Necessary rows count
__offset | - | Offset

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

Field |Description
--------- | -----------
 id | The transaction ID
 source | The data in transaction
 source.device_hash | The sensor hash
 source.timestamp | The last time when the shipment transmitted status
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

## Alerts list

POST /api/gate/auth

> Example of a request:

```shell
curl --request POST \
  --url https://demo-dashboard.moeco.io/api/gate/auth \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

POST `https://demo-dashboard.moeco.io/api/gate/auth 
?__body=`

> Body example

```json
{
  "api_key": "43e83415d71163ab",
  "name": "Test name",
  "pub_key": "Tksdh487t49387tuuiufi"
}
```
### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__body | object | - | No | Example Value

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 42,
      "name": "My gateway",
      "organization_id": 1,
      "user_id": 1,
      "group_uid": "5b15b43c1e01dc3ec51d422ce82a4e75",
      "blockchain_uid": "5b15b43c1e01dc3ec51d422ce82a4e75",
      "pub_key": "--pub-key--",
      "latitude": 1,
      "longitude": 1,
      "status": 1,
      "updated_at": "2019-02-12T16:13:30.239Z",
      "created_at": "2018-12-17T09:13:34.299Z",
      "blockchain_id": "43e83415d71163ab",
      "group_id": "43e83415d71163ab"
}
```

Parameter |Description
--------- | -----------
 id | Alert ID
 name | Alert name
 organization_id | Organization ID 
 user_id | User ID
 group_uid | Group UID 
 blockchain_uid | Blockchain UID
 pub_key | Pub Key 
 latitude| Latitude
 longitude | Longitude 
 status | status (TBD)
 updated_at | Date and time when alert was updated
 created_at | Date and time when alert was created
 blockchain_id | Blockchain ID
 group_id | Group ID 


## Alert device

GET /api/gate/device

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/gate/device \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/gate/device`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
no | - | - | - | -


### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "devices": [
        {
          "id": 42,
          "hash": "asdqwe",
          "organization_id": "Организация",
          "user_id": 1,
          "manufacturer": "asdqwe",
          "blockchain_uid": "asdqwe",
          "battery_status": 50,
          "device_group_uid": "asdqwe",
          "status": 1,
          "cert": "--pub-key--",
          "updated_at": "2019-02-12T16:13:30.239Z",
          "created_at": "2018-12-17T09:13:34.299Z"
        }
      ],
      "device_groups": [
        {
          "id": 42,
          "blockchain_uid": "5b15b43c1e01dc3ec51d422ce82a4e75",
          "name": "My group",
          "group_type": 123123123,
          "uplink_lifetime": 3000,
          "downlink_lifetime": 3000,
          "trx_timeout": 3000,
          "services": [
            "string"
          ],
          "status": 1,
          "organization_id": 1,
          "user_id": 1,
          "tarif_str": "ANY_TARIF_NAME",
          "cert": "string",
          "updated_at": "2019-02-12T16:13:30.239Z",
          "created_at": "2018-12-17T09:13:34.299Z"
        }
	 ]
 }
```

 #### Device

Parameter |Description
--------- | -----------
 id | Alert ID
 hash | Hash
 organization_id | Organization ID
 user_id | User ID
 manufacturer | Manufacturer name
 blockchain_uid | Blockchain UID
 battery_status | Battery status
 device_group_uid | Device group UID
 device_group_uid sensor_name | Sensor name
 status | Status
 cert | Cert 
 updated_at | Date and time when alert was updated
 created_at | Date and time when alert was created


#### Device_groups

Parameter |Description
--------- | -----------
 id | Alert ID
 blockchain_uid | Blockchain UID
 name | Name of group
 group_type | Group type ID
 uplink_lifetime | Uplink lifetimehash 
 downlink_lifetime | Downlink lifetime
 trx_timeout | TRX timeout
 services | Services 
 string | String 
 status | Status
 organization_id | Organization ID 
 user_id | User ID cert | Cert 
 tarif_str | Any Tarif Name 
 cert | Cert
 updated_at | Date and time when alert was updated
 created_at | Date and time when alert was created
 
## Alert downlink

POST /api/gate/downlink

> Example of a request:

```shell
curl --request POST \
  --url https://demo-dashboard.moeco.io/api/gate/downlink \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/gate/downlink? __authorization=&__body=`

> Body example

```json
{
  "transactions": [
    {
      "device_hash": "aa:bb:cc:dd:ee",
      "payload": "{\"data\":\"mydata\"}",
      "blockchain_id": "string",
      "timestamp": "2020-12-02T06:35:56.237Z"
    }
  ]
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
authorization | string | - | Yes | Authorization token
body|object | - | No | Example Value

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    "string"
  ]
}
```

Parameter |Description
--------- | -----------
 Data | String (sensor data)

## Alert downlink statuses

POST /api/gate/downlink/statuses

> Example of a request:

```shell
curl --request POST \
  --url https://demo-dashboard.moeco.io/api/gate/downlink/statuses \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

DELETE `https://demodashboard.moeco.io//api/gate/downlink/statuses?__body=`

> Body example

```json
{
  "transactions": [
    "9d8e66b25cbb6fc50623a846ac4c4c80"
  ]
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
body | object | - | No |  Example Value

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    "string"
  ]
}
```

Parameter |Description
--------- | -----------
data | string (sensor data)

## Settings

GET /api/gate/settings

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/gate/settings \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

PUT `https://demo-dashboard.moeco.io//api/gate/settings?__api_key=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
api_key | string | - | No | Gate group api_key |
