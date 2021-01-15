# Logistic API v.0.1

## Main request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
authorization | string | - | Yes | Authorization token

## Get alerts list

GET /api/alert

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/alert \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/alert?__order=&__count=20&__offset=&__term=&__all=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
__term | string | - | No | Any query term
__all | boolean | - | No | Show not all alerts

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "user_id": 0,
      "name": "string",
      "device_group_uid": "string",
      "sensor_name": "string",
      "sensor_params": "string",
      "alert_type": 0,
      "alert_email": "string",
      "alert_phone": "string",
      "alert_status": 0,
      "created_at": "2020-06-25",
      "updated_at": "2020-06-25"
    }
  ]
}
```

Parameter |Description
--------- | -----------
 id | Alert ID
 user_id | User ID
 name | Alert name
 device\_group\_uid | Device group UID
 sensor_name | Sensor name
 sensor_params | Sensor params
 alert_type | Alert type 
 alert_email | True if we should send alert to the email
 alert_phone | True if we should send alert to the phone
 alert_status | Alert status
 created_at | Date and time when alert was created
 updated_at | Date and time when alert was updated

## Create alert

POST /api/alert

> Example of a request:

```shell
curl --request POST \
  --url https://demo-dashboard.moeco.io/api/alert \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

POST `https://demo-dashboard.moeco.io/api/alert?body`

> Body example

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

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
body | object | - | Alert description


### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "user_id": 0,
      "name": "string",
      "device_group_uid": "string",
      "sensor_name": "string",
      "sensor_params": "string",
      "alert_type": 0,
      "alert_email": "string",
      "alert_phone": "string",
      "alert_status": 0,
      "created_at": "2020-06-25",
      "updated_at": "2020-06-25"
    }
  ]
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
 alert_phone | True if we should send alert to the phone
 alert_status | Alert status
 created_at | Date and time when alert was created
 updated_at | Date and time when alert was updated


## Get alert by id

GET /api/alert/{id}

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/alert/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io//api/alert/{id}?id`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Alert ID


### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "user_id": 0,
      "name": "string",
      "device_group_uid": "string",
      "sensor_name": "string",
      "sensor_params": "string",
      "alert_type": 0,
      "alert_email": "string",
      "alert_phone": "string",
      "alert_status": 0,
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
 id | Alert ID
 organization_id | Organization ID
 user_id | User ID
 name | Name
 device_group_uid | Device group UID 
 sensor_name | Sensor name 
 sensor_params | Sensor params
 alert_type | Alert type
 alert_email | True if we should send alert to the email
 alert_phone | True if we should send alert to the phone
 alert_status | Alert status
 created_at | Date and time when alert was created
 updated_at | Date and time when alert was updated 

## Delete alert

DELETE /api/alert/{id}

> Example of a request:

```shell
curl --request DELETE \
  --url https://demo-dashboard.moeco.io/api/alert/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

DELETE `https://demo-dashboard.moeco.io//api/alert/{id}?id`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Alert ID

## Change the alert

PUT /api/alert/{id}

> Example of a request:

```shell
curl --request PUT \
  --url https://demo-dashboard.moeco.io/api/alert/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

PUT `https://demo-dashboard.moeco.io//api/alert/{id}?id=&body=`
 
> Body example

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

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Alert ID |
body | object | - | No | Alert description

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "user_id": 0,
      "name": "string",
      "device_group_uid": "string",
      "sensor_name": "string",
      "sensor_params": "string",
      "alert_type": 0,
      "alert_email": "string",
      "alert_phone": "string",
      "alert_status": 0,
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
 id | Alert ID
 organization_id | Organization ID 
 user_id | User ID
 name | string
 device_group_uid | Device group UID
 sensor_name | Sensor name
 sensor_params | Sensor params
 alert_type | Alert type
 alert_email | True if we should send alert to the email
 alert_phone | True if we should send alert to the phone
 alert_status | Alert status
 created_at | Date and time when alert was created
 updated_at | Date and time when alert was updated 


## Get countries suggestions

GET /api/alert/countries

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/alert/countries \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/alert/countries?__order=&__count=20&__offset=&term=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
term | string | - | No | Any query term

### Response

> The above command returns JSON structured like this:

```json
string
```

Parameter |Description
--------- | -----------

## Get events in alert

GET /api/alert/event

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/alert/event \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/alert/event?__order=&__count=20&__offset=&term=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
term | string | - | No | Any query term

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "state": 0,
      "alert_id": 0,
      "package_id": 0,
      "device_hash": "string",
      "last_trx": "2020-12-20",
      "process_counter": 0,
      "sensor_name": "string",
      "trigger_params": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20",
      "alert": {
        "id": 0,
        "organization_id": 0,
        "user_id": 0,
        "name": "string",
        "device_group_uid": "string",
        "sensor_name": "string",
        "sensor_params": "string",
        "alert_type": 0,
        "alert_email": "string",
        "alert_phone": "string",
        "alert_status": 0,
        "created_at": "2020-12-20",
        "updated_at": "2020-12-20"
      }
    }
  ]
}
```

#### Data

Parameter |Description
--------- | -----------
id | Alert ID
state | State 
alert_id | Alert ID 
package_id | Package ID
organization_id | Organization ID
device_hash | Device hash 
last_trx | Last TRX 
process_counter | Process counter
sensor_name | Sensor name 
trigger_params | Trigger params
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

#### Alert

Parameter |Description
--------- | -----------
id | Alert ID
organization_id | Organization ID
user_id | User ID 
name | Name 
device_group_uid | Device group UID
sensor_name | Sensor name 
sensor_params | Sensor params 
alert_type | Alert type (TBD)
alert_email | True if we should send alert to the email 
alert_phone | True if we should send alert to the phone 
alert_status | Alert status 
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

## Get event by ID

GET /api/alert/event/{id}

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/​api​/alert​/event​/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/alert/event/{id}?id`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Alert ID

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "state": 0,
      "alert_id": 0,
      "package_id": 0,
      "device_hash": "string",
      "last_trx": "2020-12-20",
      "process_counter": 0,
      "sensor_name": "string",
      "trigger_params": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20",
      "alert": {
        "id": 0,
        "organization_id": 0,
        "user_id": 0,
        "name": "string",
        "device_group_uid": "string",
        "sensor_name": "string",
        "sensor_params": "string",
        "alert_type": 0,
        "alert_email": "string",
        "alert_phone": "string",
        "alert_status": 0,
        "created_at": "2020-12-20",
        "updated_at": "2020-12-20"
      }
    }
  ]
}
```

#### Data

Parameter |Description
--------- | -----------
id | Alert ID
state | State 
alert_id | Alert ID 
package_id | Package ID
device_hash | Device hash
last_trx | Last TRX
process_counter | Process counter (TBD)
sensor_name | Sensor name
trigger_params | Trigger params
created_at | Date and time when event was created
updated_at | Date and time when event was updated

#### Alert

Parameter |Description
--------- | -----------
id | Alert ID
organization_id | Organization ID
user_id | User ID 
name | Name 
device_group_uid | Device group UID
sensor_name | Sensor name 
sensor_params | Sensor params 
alert_type | Alert type (TBD)
alert_email | True if we should send alert to the email 
alert_phone | True if we should send alert to the phone 
alert_status | Alert status 
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

## Get last event

GET /api/alert/event/last

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/alert/event/last \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io//api/alert/event/last?__alert_id=&__device_hash=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
alert_id | integer | - | Yes | SRC alert ID
device_hash | string | - | Yes | SRC alert device hash

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "state": 0,
      "alert_id": 0,
      "package_id": 0,
      "device_hash": "string",
      "last_trx": "2020-12-20",
      "process_counter": 0,
      "sensor_name": "string",
      "trigger_params": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20",
      "alert": {
        "id": 0,
        "organization_id": 0,
        "user_id": 0,
        "name": "string",
        "device_group_uid": "string",
        "sensor_name": "string",
        "sensor_params": "string",
        "alert_type": 0,
        "alert_email": "string",
        "alert_phone": "string",
        "alert_status": 0,
        "created_at": "2020-12-20",
        "updated_at": "2020-12-20"
      }
    }
  ]
}
```

#### Data

Parameter |Description
--------- | -----------
id | Alert ID
state | State 
alert_id | Alert ID 
package_id | Package ID
device_hash | Device hash
last_trx | Last TRX
process_counter | Process counter (TBD)
sensor_name | Sensor name
trigger_params | Trigger params
created_at | Date and time when event was created
updated_at | Date and time when event was updated

#### Alert

Parameter |Description
--------- | -----------
id | Alert ID
organization_id | Organization ID
user_id | User ID 
name | Name 
device_group_uid | Device group UID
sensor_name | Sensor name 
sensor_params | Sensor params 
alert_type | Alert type (TBD)
alert_email | True if we should send alert to the email 
alert_phone | True if we should send alert to the phone 
alert_status | Alert status 
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

## Get notification about alert

GET /api/alert/notification

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/alert/notification \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/alert/notification?__order=&__count=20&__offset=&term=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
term | string | - | No | Any query term

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "alert_id": 0,
      "package_id": 0,
      "message": "string",
      "email_sent": "2020-12-20",
      "sms_sent": "2020-12-20",
      "viewed_by_app": "2020-12-20",
      "status": 0,
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20",
      "alert": {
        "id": 0,
        "organization_id": 0,
        "user_id": 0,
        "name": "string",
        "device_group_uid": "string",
        "sensor_name": "string",
        "sensor_params": "string",
        "alert_type": 0,
        "alert_email": "string",
        "alert_phone": "string",
        "alert_status": 0,
        "created_at": "2020-12-20",
        "updated_at": "2020-12-20"
      }
    }
  ]
}
```

#### Data

Parameter |Description
--------- | -----------
id | Alert ID
alert_id | Alert ID 
package_id | Package ID 
message | Message
email_sent | Date when email sent 
sms_sent | Date when sms sent 
viewed_by_app | Date when notification viewed by app 
status | Status
created_at | Date and time when event was created
updated_at | Date and time when event was updated

#### Alert

Parameter |Description
--------- | -----------
id | Alert ID
organization_id | Organization ID
user_id | User ID 
name | Name 
device_group_uid | Device group UID
sensor_name | Sensor name 
sensor_params | Sensor params 
alert_type | Alert type (TBD)
alert_email | True if we should send alert to the email 
alert_phone | True if we should send alert to the phone 
alert_status | Alert status 
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

## Creates alert notification

POST /api/alert/notification

> Example of a request:

```shell
curl --request POST \
  --url https://demo-dashboard.moeco.io/api/alert/notification
\
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

POST `https://demo-dashboard.moeco.io/api/alert/notification?body`

> Body example

```json
{
  "event_id": 1,
  "alert_id": 1,
  "package_id": 2,
  "message": "Notification description",
  "src_trx": "{}"
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
body | object | - | Alert description

### Response

> The above command returns JSON structured like this:

```json
{
{
  "data": [
    {
      "id": 0,
      "alert_id": 0,
      "package_id": 0,
      "message": "string",
      "email_sent": "2020-12-20",
      "sms_sent": "2020-12-20",
      "viewed_by_app": "2020-12-20",
      "status": 0,
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20",
      "alert": {
        "id": 0,
        "organization_id": 0,
        "user_id": 0,
        "name": "string",
        "device_group_uid": "string",
        "sensor_name": "string",
        "sensor_params": "string",
        "alert_type": 0,
        "alert_email": "string",
        "alert_phone": "string",
        "alert_status": 0,
        "created_at": "2020-12-20",
        "updated_at": "2020-12-20"
      }
    }
  ]
}
```

**Data**

Parameter |Description
--------- | -----------
id | Alert event id
alert_id |  Alert ID
package_id | Package ID
message | Message 
email_sent | TBD
sms_sent | TBD
viewed_by_app | TBD
status | Status
created_at | Date and time when event was created
updated_at | Date and time when event was updated

**Alert**

Parameter |Description
--------- | -----------
id | Alert event id
organization_id | Organization ID 
user_id | User ID 
name | Alert name
device_group_uid | Device group UID 
sensor_name | Sensor name
sensor_params | Sensor parameters
alert_type | Alert type (TBD)
alert_email | True if we should send alert to the email
alert_phone | True if we should send alert to the phone
alert_status | Atert status (TBD)
created_at | Date and time when alert was created
updated_at | Date and time when alert was updated

## Get notification by id 

GET /api/alert/notification/{id}

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/alert/notification/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/alert/notification/{id}?id`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Notification ID

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "alert_id": 0,
      "package_id": 0,
      "message": "string",
      "email_sent": "2020-12-20",
      "sms_sent": "2020-12-20",
      "viewed_by_app": "2020-12-20",
      "status": 0,
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20",
      "alert": {
        "id": 0,
        "organization_id": 0,
        "user_id": 0,
        "name": "string",
        "device_group_uid": "string",
        "sensor_name": "string",
        "sensor_params": "string",
        "alert_type": 0,
        "alert_email": "string",
        "alert_phone": "string",
        "alert_status": 0,
        "created_at": "2020-12-20",
        "updated_at": "2020-12-20"
      }
    }
  ]
}
```

**Data**

Parameter |Description
--------- | -----------
id   | ID
alert_id | Alert ID 
package_id | Package ID
message | Message
email_sent | TBD
sms_sent | TBD
viewed_by_app | TBD
status | Status
created_at | Date and time when event was created
updated_at | Date and time when event was updated

**Alert**

Parameter |Description
--------- | -----------
id   | Alert ID
organization_id | Organization ID
user_id | User ID 
name | Name 
device_group_uid | Device group UID
sensor_name | Sensor name 
sensor_params | Sensor params 
alert_type | Alert type (TBD)
alert_email | True if we should send alert to the email 
alert_phone | True if we should send alert to the phone 
alert_status | Alert status 
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

## Change notification

PUT /api/alert/notification/{id}

> Example of a request:

```shell
curl --request PUT \
  --url https://demo-dashboard.moeco.io/api/alert/notification/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

PUT `https://demo-dashboard.moeco.io//api/alert/notification/{id}?id=&body=`

> Body example

```json
{
  "status": 1,
  "viewed_by_app": "2020-12-09T07:10:00.757Z",
  "sms_sent": "2020-12-09T07:10:00.757Z",
  "email_sent": "2020-12-09T07:10:00.757Z"
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Notification ID |
body | object | - | No | Notification description


### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "alert_id": 0,
      "package_id": 0,
      "message": "string",
      "email_sent": "2020-12-20",
      "sms_sent": "2020-12-20",
      "viewed_by_app": "2020-12-20",
      "status": 0,
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20",
      "alert": {
        "id": 0,
        "organization_id": 0,
        "user_id": 0,
        "name": "string",
        "device_group_uid": "string",
        "sensor_name": "string",
        "sensor_params": "string",
        "alert_type": 0,
        "alert_email": "string",
        "alert_phone": "string",
        "alert_status": 0,
        "created_at": "2020-12-20",
        "updated_at": "2020-12-20"
      }
    }
  ]
}
```

**Data**

Parameter |Description
--------- | -----------
id | Alert event id
alert_id | Alert ID
package_id | Package ID
message | Message
email_sent | Date when email sent 
sms_sent | Date when sms sent 
viewed_by_app | Date when notification viewed by app 
status | Status 
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

**Alert**

Parameter | Description
--------- | -----------
id | Alert ID
organization_id | Organization ID
user_id | User ID 
name | Name 
device_group_uid | Device group UID
sensor_name | Sensor name 
sensor_params | Sensor params 
alert_type | Alert type (TBD)
alert_email | True if we should send alert to the email 
alert_phone | True if we should send alert to the phone 
alert_status | Alert status 
created_at | Date and time when event was created
updated_at | Date and time when event was updated 
 
## Activate the package

GET /api/decoder/active_package

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/decoder/active_package \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/decoder/active_package?device_hash=&trx_time=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
device_hash | string | - | Yes | Device hash
trx_time | string($date) | - | Yes | trx date

## Get alerts status by organization_id

GET /api/decoder/alert/{organization_id}

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api​/decoder​/alert​/{organization_id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/decoder/alert/{organization_id}?organization_id`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
organization_id | integer | - | Yes | organization_id

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "user_id": 0,
      "name": "string",
      "device_group_uid": "string",
      "sensor_name": "string",
      "sensor_params": "string",
      "alert_type": 0,
      "alert_email": "string",
      "alert_phone": "string",
      "alert_status": 0,
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
id | Alert ID
organization_id | Organization ID
user_id | User ID
name | Alert name 
device_group_uid | Device group UID 
sensor_name |Sensor name
sensor_params | Sensor parameters
alert_type | Alert type (TBD)
alert_email | True if we should send alert to the email
alert_phone | True if we should send alert to the phone
alert_status | Atert status (TBD)
created_at | Date and time when alert was created
updated_at | Date and time when alert was updated

## Create alert events

POST /api/decoder/events

> Example of a request:

```shell
curl --request POST \
  --url https://demo-dashboard.moeco.io/api/decoder/events \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

POST `https://demo-dashboard.moeco.io/api/decoder/events?body`

> Body example

```json
{
  "state": 1,
  "alert_id": 1,
  "package_id": 1,
  "device_hash": "1123dfhhj",
  "sensor_name": "position",
  "last_trx": "2020-12-09T07:10:00.766Z",
  "trigger_params": "{}",
  "process_counter": 0
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
body | object | - | Alert description

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "state": 0,
      "alert_id": 0,
      "package_id": 0,
      "device_hash": "string",
      "last_trx": "2020-12-20",
      "process_counter": 0,
      "sensor_name": "string",
      "trigger_params": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
id | Alert ID
state | State 
alert_id | Alert ID 
package_id | Package ID
device_hash | Device hash
last_trx | Last TRX
process_counter | Process counter (TBD)
sensor_name | Sensor name
trigger_params | Trigger params
created_at | Date and time when event was created
updated_at | Date and time when event was updated

## Change alert event's

PUT /api/decoder/events/{id}

> Example of a request:

```shell
curl --request PUT \
  --url https://demo-dashboard.moeco.io/api/decoder/events/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

PUT `https://demo-dashboard.moeco.io/api/decoder/events/{id}?id=&body=`

> Body example

```json
{
  "id": 1,
  "state": 1,
  "alert_id": 1,
  "package_id": 1,
  "device_hash": "1123dfhhj",
  "sensor_name": "position",
  "last_trx": "2020-12-09T07:10:00.770Z",
  "trigger_params": "{}",
  "process_counter": 0,
  "created_at": "2020-12-09T07:10:00.770Z",
  "updated_at": "2020-12-09T07:10:00.770Z"
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Event ID |
body | object | - | No | Event description


### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "state": 0,
      "alert_id": 0,
      "package_id": 0,
      "device_hash": "string",
      "last_trx": "2020-12-20",
      "process_counter": 0,
      "sensor_name": "string",
      "trigger_params": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
id | Alert ID
state | State 
alert_id | Alert ID 
package_id | Package ID
device_hash | Device hash
last_trx | Last TRX
process_counter | Process counter (TBD)
sensor_name | Sensor name
trigger_params | Trigger params
created_at | Date and time when event was created
updated_at | Date and time when event was updated

## Get device info by hash

GET /api/device/{hash}

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/device/{hash} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/device/{hash}?hash=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
hash | string | - | Yes | Device hash, or unique ID

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "hash": "string",
      "manufacturer": "string",
      "blockchain_uid": "string",
      "battery_status": 0,
      "device_group_uid": "string",
      "status": 0,
      "tags": [
        {
          "id": 0,
          "organization_id": 0,
          "device_group_uid": "string",
          "tag_name": "string",
          "tag_type": "string",
          "tag_order": 0,
          "tag_required": 0,
          "tag_data": "string",
          "created_at": "2020-12-20",
          "updated_at": "2020-12-20"
        }
      ]
    }
  ]
}
```

**Data** 

Parameter |Description
--------- | -----------
hash | Device hash
manufacturer | Manufacturer 
blockchain_uid | Blockchain UID
battery_status | Battery status 
device_group_uid | Device group UID
status | Status 

**Tags** 

Parameter |Description
--------- | -----------
ID | Alert ID
organization_id | Organization ID
device_group_uid | Device group UID
tag_name|Tag name
tag_type|Tag type
tag_order|Tag order
tag_required|Tag required
tag_data| Tag data
created_at | Date and time when event was created
updated_at | Date and time when event was updated

## Search a device 

GET /api/device/search

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/device/search \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/device/search?hash=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
hash | string | - | Yes | Device hash, or unique ID

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "hash": "string",
      "manufacturer": "string",
      "blockchain_uid": "string",
      "battery_status": 0,
      "device_group_uid": "string",
      "status": 0,
      "tags": [
        {
          "id": 0,
          "organization_id": 0,
          "device_group_uid": "string",
          "tag_name": "string",
          "tag_type": "string",
          "tag_order": 0,
          "tag_required": 0,
          "tag_data": "string",
          "created_at": "2020-12-20",
          "updated_at": "2020-12-20"
        }
      ]
    }
  ]
}
```

**Data**

Parameter |Description
--------- | -----------
hash | Device hash
manufacturer | Manufacturer 
blockchain_uid | Blockchain UID
battery_status | Battery status 
device_group_uid | Device group UID
status | Status 

**Tags**

Parameter |Description
--------- | -----------
ID | Alert ID
organization_id | Organization ID
device_group_uid | Device group UID
tag_name | Tag name
tag_type | Tag type
tag_order | Tag order
tag_required | Tag required
tag_data | Tag data
created_at | Date and time when event was created
updated_at | Date and time when event was updated

## Get info about devices geolocation

GET /api/geoDevices

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/geoDevices \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' 
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/geoDevices?`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------

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

## Get info about system

GET /api/info

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/info \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/info?__order=&__count=20&__offset=&term=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
term | string | - | No | Any query term

## Get list of packages

GET /api/package

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/package \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/package __order=&__count=20&__offset=&term=&__only_active=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
term | string | - | No | Any query term
only_active | boolean | - | No | Show only active packages


### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "user_id": 0,
      "device_hash": "string",
      "device_uid": "string",
      "device_group_uid": "string",
      "status": 0,
      "destination": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20",
      "device_tags": [
        {
          "id": 0,
          "tag_id": 0,
          "tag_value": "string",
          "device_hash": "string",
          "package_id": 0,
          "created_at": "2020-12-20",
          "updated_at": "2020-12-20"
        }
      ],
      "alert_events": [
        {
          "id": 0,
          "state": 0,
          "alert_id": 0,
          "package_id": 0,
          "device_hash": "string",
          "last_trx": "2020-12-20",
          "process_counter": 0,
          "sensor_name": "string",
          "trigger_params": "string",
          "created_at": "2020-12-20",
          "updated_at": "2020-12-20",
          "alert": {
            "id": 0,
            "organization_id": 0,
            "user_id": 0,
            "name": "string",
            "device_group_uid": "string",
            "sensor_name": "string",
            "sensor_params": "string",
            "alert_type": 0,
            "alert_email": "string",
            "alert_phone": "string",
            "alert_status": 0,
            "created_at": "2020-12-20",
            "updated_at": "2020-12-20"
          }
        }
      ],
      "transactions": [
        "string"
      ]
    }
  ]
}
```

**Data**

Parameter |Description
--------- | -----------
ID | Alert ID
organization_id | Organization ID
user_id | User ID
device_hash | Device hash
device_uid | device UID 
device_group_uid | Device group UID
status | Status
destination | Destination (TBD)
created_at | Date and time when event was created
updated_at | Date and time when event was updated

**Device tags**

Parameter |Description
--------- | -----------
ID | Device ID
tag id| Tag ID
tag_value | Tag value
device_hash | Device hash
package_id | Package ID 
created_at | Date and time when event was created
updated_at | Date and time when event was updated

**Alert events**

Parameter |Description
--------- | -----------
id | Alert event id
state| State
alert_id | Alert ID
package_id | Package ID
device_hash | Device hash
last_trx | Last TRX
process_counter | Process counter 
sensor_name | Sensor name
sensor_params | Sensor parameter
created_at | Date and time when event was created
updated_at | Date and time when event was updated 
ID | Alert ID
organization_id | Organization ID
user id| User ID
name | Name
device_group_uid | Device group UID
sensor_name | Sensor name 
sensor_params | Sensor params 
alert_type | Alert type (TBD)
alert_email | True if we should send alert to the email
alert_phone | True if we should send alert to the phone
alert_status | Atert status (TBD)
created_at | Date and time when event was created
updated_at | Date and time when event was updated

## Create package

POST /api/package

> Example of a request:

```shell
curl --request POST \
  --url https://demo-dashboard.moeco.io/api/package\
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

POST `https://demo-dashboard.moeco.io/api/package?body`

> Body example

```json
{
  "device_hash": "89457387300000021934",
  "tags": [
    {
      "tag_id": 1,
      "tag_value": "aa:1234567"
    }
  ],
  "destination": {}
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
body | object | - | Alert description


### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "user_id": 0,
      "device_hash": "string",
      "device_uid": "string",
      "device_group_uid": "string",
      "status": 0,
      "destination": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20",
      "necessaryTags": [
        {
          "id": 0,
          "organization_id": 0,
          "device_group_uid": "string",
          "tag_name": "string",
          "tag_type": "string",
          "tag_order": 0,
          "tag_required": 0,
          "tag_data": "string",
          "created_at": "2020-12-20",
          "updated_at": "2020-12-20"
        }
      ],
      "addedTags": [
        {
          "id": 0,
          "tag_id": 0,
          "tag_value": "string",
          "device_hash": "string",
          "package_id": 0,
          "created_at": "2020-12-20",
          "updated_at": "2020-12-20"
        }
      ]
    }
  ]
}
```

Parameter |Description
--------- | -----------
ID | Alert ID
organization_id | Organization ID
user_id | User ID
device_hash | Device hash
device_uid | device UID 
device_group_uid | Device group UID
status | Status
destination | Package destination
created_at | Date and time when event was created
updated_at | Date and time when event was updated
tag_name | Tag name
tag_type | Tag type
tag_order | Tag order
tag_required | Tag required
tag_data | Tag data
tag id | Tag ID
tag_value | Tag value
package_id | Package ID 

## Get package by id

GET /api/package/{id}

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/package/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/package/{id}?id`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Package ID

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "user_id": 0,
      "device_hash": "string",
      "device_uid": "string",
      "device_group_uid": "string",
      "status": 0,
      "destination": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20",
      "device_tags": [
        {
          "id": 0,
          "tag_id": 0,
          "tag_value": "string",
          "device_hash": "string",
          "package_id": 0,
          "created_at": "2020-12-20",
          "updated_at": "2020-12-20"
        }
      ],
      "alert_events": [
        {
          "id": 0,
          "state": 0,
          "alert_id": 0,
          "package_id": 0,
          "device_hash": "string",
          "last_trx": "2020-12-20",
          "process_counter": 0,
          "sensor_name": "string",
          "trigger_params": "string",
          "created_at": "2020-12-20",
          "updated_at": "2020-12-20",
          "alert": {
            "id": 0,
            "organization_id": 0,
            "user_id": 0,
            "name": "string",
            "device_group_uid": "string",
            "sensor_name": "string",
            "sensor_params": "string",
            "alert_type": 0,
            "alert_email": "string",
            "alert_phone": "string",
            "alert_status": 0,
            "created_at": "2020-12-20",
            "updated_at": "2020-12-20"
          }
        }
      ],
      "transactions": [
        "string"
      ]
    }
  ]
}
```

**Data**

Parameter |Description
--------- | -----------
id | Alert ID
organization_id | Organization ID
user_id | User ID 
device_hash | Device hash
device_uid | Device UID 
device_group_uid | Device group UID
status | Status 
destination | Destination
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

**Device tags**

Parameter |Description
--------- | -----------
ID | ID
tag id| Tag ID
tag_value | Tag value
device_hash | Device hash
package_id | Package ID 
created_at | Date and time when event was created
updated_at | Date and time when event was updated

**Alert events**

Parameter |Description
--------- | -----------
id | Alert event id
state| State
alert_id | Alert ID
package_id | Package ID
device_hash | Device hash
last_trx | Last TRX
process_counter | Process counter 
sensor_name | Sensor name
trigger_params | Trigger parameter
created_at | Date and time when event was created
updated_at | Date and time when event was updated 
ID | Alert ID
organization_id | Organization ID
user id | User ID
name | Name
device_group_uid | Device group UID
sensor_name | Sensor name 
sensor_params | Sensor params 
alert_type | Alert type (TBD)
alert_email | True if we should send alert to the email
alert_phone | True if we should send alert to the phone
alert_status | Atert status (TBD)
created_at | Date and time when event was created
updated_at | Date and time when event was updated

## Change data in some package

PUT /api/package/{id}

> Example of a request:

```shell
curl --request PUT \
  --url https://demo-dashboard.moeco.io/api/package/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

PUT `https://demo-dashboard.moeco.io/api/package/{id}?id=&body=`

> Body example

```json
{
  "status": 2,
  "destination": {}
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
status | integer | - | No | Package statuus ID |
destination | string | - | No | Package description


### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "user_id": 0,
      "device_hash": "string",
      "device_uid": "string",
      "device_group_uid": "string",
      "status": 0,
      "destination": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
id | Package ID
organization_id | Organization ID
user_id | User ID 
device_hash | Device hash
device_uid | Device UID 
device_group_uid | Device group UID
status | Status 
destination | Destination
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

## Get charts from some package by id

GET /api/package/{id}/charts

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/package/{id}/charts \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/package/{id}/charts?__id=&__samples=1&__start_date=&__stop_date=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Package ID
__samples | integer | 1 | No | Samples count
__start_date | string($date) | - | No | Start date
__stop_date | string($date) | 0 | No | Start date

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    "string"
  ],
```

Parameter |Description
--------- | -----------


## Get track info from some package by id

GET /api/package/{id}/track

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/package/{id}/track \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/package/{id}/track?__id=&__distance=100&__start_date=&__stop_date=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Package ID
__distance | integer | 100 | No | Min distance in meters
__start_date | string($date) | - | No | Start date
__stop_date | string($date) | 0 | No | Start date

## Get transactions from some package by id

GET /api/package/{id}/transactions

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/package/{id}/transactions\
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/package/{id}/transactions?__order=&__count=20&__offset=&term=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Package ID
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
__term | string | - | No | Any query term

## Get package statuses

GET /api/package/statuses

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/package/statuses \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/package/statuses`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
        "ONTHEWAY": {
        ...
        "DELIVERED": {
        ...
        "CANCELED": {
        ...
        "ARCHIVED": {
        ...
      "statusesById": {
        "1": {
        ...
        "2": {
        ...
        "3": {
        ...
        "4": {
        ...
        "5": {
        ...
        "6": {
        ...
  ]
}
```

Parameter |Description
--------- | -----------

## Change tags for package

PUT /api/package/tags

> Example of a request:

```shell
curl --request PUT \
  --url https://demo-dashboard.moeco.io/api/package/tags \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

PUT `https://demo-dashboard.moeco.io/api/package/tags?body=`

> Body example

```json
{
  "deviceHash": "89457387300000021934",
  "id": 0
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
deviceHash | string | - | Yes | Device hash
id | integer | - | Yes | Tag ID

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "tag_id": 0,
      "tag_value": "string",
      "device_hash": "string",
      "package_id": 0,
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
ID | ID
tag id | Tag ID
tag_value | Tag value
device_hash | Device hash
package_id | Package ID 
created_at | Date and time when event was created
updated_at | Date and time when event was updated

## Delete tags from package

DELETE /api/package/tags/{id}

> Example of a request:

```shell
curl --request DELETE \
  --url https://demo-dashboard.moeco.io/api/package/tags/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

DELETE `https://demo-dashboard.moeco.io/api/package/tags/{id}?id`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Tag ID

## Get region list 

GET /api/region

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/region \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/region?__order=&__count=20&__offset=&term=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
term | string | - | No | Any query term

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "user_id": 0,
      "name": "string",
      "data": [
        {
          "type": "country",
          "value": "Russia"
        }
      ],
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
id | Alert ID
organization_id | Organization ID
user_id | User ID 
name | Data type
type | Region type
value | Region name
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

## Creates new region

POST /api/region

> Example of a request:

```shell
curl --request POST \
  --url https://demo-dashboard.moeco.io/api/region\
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

POST `https://demo-dashboard.moeco.io/api/region?body`

> Body example

```json
{
{
  "name": "Country linst #1",
  "data": [
    {
      "type": "country",
      "value": "Russia"
    }
  ]
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
body | object | - | region description


### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "user_id": 0,
      "name": "string",
      "data": [
        {
          "type": "country",
          "value": "Russia"
        }
      ],
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
ID | ID region
organization_id | Organization ID
user_id | User ID
name | Data type
type | Region type
value | Region name
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

## Get info about region by ID

GET /api/region/{id}

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/region/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/region/{id}?id`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Region ID

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "user_id": 0,
      "name": "string",
      "data": [
        {
          "type": "country",
          "value": "Russia"
        }
      ],
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
id | ID region
organization_id | Organization ID
user_id | User ID 
name | Data type
type | Region type
value | Region name
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

## Delete region

DELETE /api/region/{id}

> Example of a request:

```shell
curl --request DELETE \
  --url https://demo-dashboard.moeco.io/api/region/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

DELETE `https://demo-dashboard.moeco.io/api/region/{id}?id`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | region ID 

## Change info about region 

PUT /api/region/{id}

> Example of a request:

```shell
curl --request PUT \
  --url https://demo-dashboard.moeco.io/api/region/{id}\
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

PUT `https://demo-dashboard.moeco.io/api/region/{id}?id=&body=`

> Body example

```json
{
  "name": "Country linst #1",
  "data": [
    {
      "type": "country",
      "value": "Russia"
    }
  ]
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Region ID |
body | object | - | No | Region description

### Response

> The above command returns JSON structured like this:

```json
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "user_id": 0,
      "name": "string",
      "data": [
        {
          "type": "country",
          "value": "Russia"
        }
      ],
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
id | region ID
organization_id | Organization ID
user_id | User ID 
name | Data type
type | Region type
value | Region name
created_at | Date and time when event was created
updated_at | Date and time when event was updated 

## Search data in the base

GET /api/search

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/search \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/search?__order=&__count=20&__offset=&term=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
__term | string | - | No | Any query term

## Get tags list

GET /api/tag

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/tag \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/tag?__order=&__count=20&__offset=&term=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
__term | string | - | No | Any query term

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "device_group_uid": "string",
      "tag_name": "string",
      "tag_type": "string",
      "tag_order": 0,
      "tag_required": 0,
      "tag_data": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
ID | Tag ID
organization_id | Organization ID
device_group_uid | Device group UID
tag_name | Tag name
tag_type | Tag type
tag_order | Tag order
tag_required | Tag required
tag_data | Tag data
created_at | Date and time when event was created
updated_at | Date and time when event was updated

## Create tag

POST /api/tag

> Example of a request:

```shell
curl --request POST \
  --url https://demo-dashboard.moeco.io/api/tag\
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

POST `https://demo-dashboard.moeco.io/api/tag?body`

> Body example

```json
{
  "device_group_uid": "string",
  "tag_name": "Any_name",
  "tag_type": "textBox",
  "tag_order": 3,
  "tag_required": 1,
  "tag_data": "string"
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
body | object | - | Alert description


### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "device_group_uid": "string",
      "tag_name": "string",
      "tag_type": "string",
      "tag_order": 0,
      "tag_required": 0,
      "tag_data": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
ID | Tag ID
organization_id | Organization ID
device_group_uid | Device group UID
tag_name | Tag name
tag_type | Tag type
tag_order | Tag order
tag_required | Tag required
tag_data | Tag data
created_at | Date and time when event was created
updated_at | Date and time when event was updated

## Get tag by ID

GET /api/tag/{id}

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/tag/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/tag/{id}?id`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Tag ID

### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "device_group_uid": "string",
      "tag_name": "string",
      "tag_type": "string",
      "tag_order": 0,
      "tag_required": 0,
      "tag_data": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
ID | Tag ID
organization_id | Organization ID
device_group_uid | Device group UID
tag_name | Tag name
tag_type | Tag type
tag_order | Tag order
tag_required | Tag required
tag_data | Tag data
created_at | Date and time when event was created
updated_at | Date and time when event was updated

## Delete tag by ID

DELETE /api/tag/{id}

> Example of a request:

```shell
curl --request DELETE \
  --url https://demo-dashboard.moeco.io/api/tag/{id} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

DELETE `https://demo-dashboard.moeco.io/api/tag/{id}?id`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Tag ID

## Change a tag

PUT /api/tag/{id}

> Example of a request:

```shell
curl --request PUT \
  --url https://demo-dashboard.moeco.io/api/tag/{id}\
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

PUT `https://demo-dashboard.moeco.io/api/tag/{id}?id=&body=`

> Body example

```json
{
  "device_group_uid": "string",
  "tag_name": "Any_name",
  "tag_type": "textBox",
  "tag_order": 3,
  "tag_required": 1,
  "tag_data": "string"
}
```

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
id | integer | - | Yes | Tag ID |
body | object | - | No | Alert description


### Response

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 0,
      "organization_id": 0,
      "device_group_uid": "string",
      "tag_name": "string",
      "tag_type": "string",
      "tag_order": 0,
      "tag_required": 0,
      "tag_data": "string",
      "created_at": "2020-12-20",
      "updated_at": "2020-12-20"
    }
  ]
}
```

Parameter |Description
--------- | -----------
ID | Tag ID
organization_id | Organization ID
device_group_uid | Device group UID
tag_name | Tag name
tag_type | Tag type
tag_order | Tag order
tag_required | Tag required
tag_data | Tag data
created_at | Date and time when event was created
updated_at | Date and time when event was updated

## Get transactions list

GET /api/transactions

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/transactions \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/transactions?__order=&__count=20&__offset=&term=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
__term | string | - | No | Any query term

## Get transactions by device hash 

GET /api/transactions/{device_hash}

> Example of a request:

```shell
curl --request GET \
  --url https://demo-dashboard.moeco.io/api/transactions/{device_hash} \
  --header 'authorization: e0265e2d-b702-490a-96a3-8ea596c4f0aa' \
  --header 'Content-Type: application/json' \
```

### Request

GET `https://demo-dashboard.moeco.io/api/transactions/{device_hash}?__device_hash=&__order=&__count=20&__offset=&term=`

### Request parameters

Parameter | Type | Default | Required | Description
--------- | ------- | ----------- | ---------- | ---------
__device_hash | string | - | Yes | Device hash
__order | string | - | No | Query order
__count | integer | 20 | No | Necessary rows count
__offset | integer | 0 | No | Offset
__term | string | - | No | Any query term
