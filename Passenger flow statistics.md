## Passenger flow statistics

### Query device list

interface URL**

> /statistic/taxi/wifiSniffer/list?page=1&pageSize=40&key=

| environment | URL |
| --- | --- |
| vip | https://www.vehhub.vip |

**Request method**

> GET

Request Header Parameter

| Parameter name | Example Value | Parameter Type | Required or not | Parameter Description |
| --- | --- | ---- | ---- | ---- |
| authorization | Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhY | string | yes | - |

**Request Query Parameter

| Parameter name | Example Value | Parameter Type | Required or not | Parameter Description |
| --- | --- | ---- | ---- | ---- |
| page | 1 | string | yes | - |
| pageSize | 40 | string | yes | - |
| key | - | string | yes | - |

Authentication method

> Inherit from parent

Example response

* success(200)

```javascript
{
    "msg": "success",
    "code": 0,
    "data": {
        "pageIndex": 1,
        "pageSize": 40,
        "total": 13,
        "pages": 1,
        "list": [
            {
                "id": "y1c-325-60418"
            },
            {
                "id": "y1c-325-60421"
            },
            {
                "id": "y1c-325-60580"
            }
        ]
    }
}
```

| Parameter name | Example Value | Parameter Type | Parameter Description |
| --- | --- | ---- | ---- |
| msg | success | string | - |
| code | 0 | string | - |
| data | - | object | - |
| data.pageIndex | 1 | integer | current page |
| data.pageSize | 40 | integer | one page |
| data.total | 13 | integer | total number |
| data.pages | 1 | integer | total page |
| data.list | - | array | - |
| data.list.id | y1c-325-60418 | string | - |

### Details of a device

interface URL**

> /statistic/taxi/wifiSniffer/rangeTimeDataList?deviceId=y1c-325-60418&startDate=2025-08-15&endDate=2025-08-21

| environment | URL |
| --- | --- |
| vip | https://www.vehhub.vip |

**Mock URL**

> /statistic/taxi/wifiSniffer/rangeTimeDataList?apipost_id=26a9834fb1200f

**Request method**

**Request Header Parameter**

| Parameter name | Example Value | Parameter Type | Required or not | Parameter Description |
| --- | --- | ---- | ---- | ---- |
| authorization | Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXThkNzc5YzIwYSIsInVzZXJfaWQiOiI2FBfw | string | yes | - |

**Request Query Parameter**

| Parameter name | Example Value | Parameter Type | Required or not | Parameter Description |
| --- | --- | ---- | ---- | ---- |
| deviceId | y1c-325-60418 | string | yes | - |
| startDate | 2025-08-15 | string | yes | - |
| endDate | 2025-08-21 | string | yes | - |

**Sample Response***

* success(200)

```javascript
{
    "msg": {
        "timeList": [
            "2025-08-15",
            "2025-08-16",
            "2025-08-17",
            "2025-08-18",
            "2025-08-19",
            "2025-08-20",
            "2025-08-21"
        ],
        "yesterdayDataNum": 0,
        "nowDataNum": 0,
        "maxDate": {
            "date": "2025-08-15",
            "num": 0
        },
        "numList": [
            0,
            0,
            0,
            0,
            0,
            0,
            0
        ]
    },
    "code": 0
}
```

| Parameter name | Example Value | Parameter Type | Parameter Description |
| --- | --- | ---- | ---- |
| msg | - | object | - |
| msg.timeList | ["2025-08-15","2025-08-16","2025-08-17","2025-08-18","2025-08-19","2025-08-20","2025-08-21"] | array | Chart Time |
| msg.yesterdayDataNum | 0 | number | Yesterday's passenger flow |
| msg.nowDataNum | 0 | string | Today's passenger flow |
| msg.maxDate | - | object | - |
| msg.maxDate.date | 2025-08-15 | string | Maximum passenger flow time |
| msg.maxDate.num | 0 | string | Minimum passenger flow time |
| msg.numList | [0, 0,  0,  0, 0, 0,  0] | array | Passenger flow chart |
| code | 0 | string | - |

**Export data from a specific device**

**Interface URL**

> /statistic/taxi/wifiSniffer/export?Authorization=&deviceId=y1c-325-60418&startDate=2025-08-27&endDate=2025-09-02&lang=zh

**Request Method**

> GET

**Content-Type**

> none

**Request Header Parameter**

| Parameter name | Example value                                                | 参数类型 | 是否必填 | 参数描述 |
| -------------- | ------------------------------------------------------------ | -------- | -------- | -------- |
| authorization  | Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhY2NvdW50X2lkIjoiNjc1ZmY5ZGI3ZTUwNWM5OGQ3NzljMjA2IiwiZXhwIjoxNzU1OTA4NTgyLCJncm91cF9pZCI6IjY3NWZmOWRiN2U1MDVjOThkNzc5YzIwYSIsInVzZXJfaWQiOiI2NzVmZjlkYjdlNTA1Yzk4ZDc3OWMyMDcifQ.e1L3vHuhh_1OQ1akfDQg4QRMtKKHmYLVQQkSPbkFBfw | string   | 是       | -        |

**Request Query Parameter*

| Parameter name | Example value | Parameter Type | required or not | Parameter Description                         |
| -------------- | ------------- | -------------- | --------------- | --------------------------------------------- |
| Authorization  | -             | string         | yes             | certificate                                   |
| deviceId       | y1c-325-60418 | string         | yes             | card number                                   |
| startDate      | 2025-08-27    | string         | yes             | Start time                                    |
| endDate        | 2025-09-02    | string         | yes             | End Time                                      |
| lang           | zh            | string         | yes             | Language of data in the data table zh Chinese |

**Authentication method**

> Inherit from parent

**Example response**

* success(200)

```javascript
{
    "msg": {
        "timeList": [
            "2025-08-15",
            "2025-08-16",
            "2025-08-17",
            "2025-08-18",
            "2025-08-19",
            "2025-08-20",
            "2025-08-21"
        ],
        "yesterdayDataNum": 0,
        "nowDataNum": 0,
        "maxDate": {
            "date": "2025-08-15",
            "num": 0
        },
        "numList": [
            0,
            0,
            0,
            0,
            0,
            0,
            0
        ]
    },
    "code": 0
}
```

| Parameter name       | Example value                                                | Parameter Type | Parameter Description       |
| -------------------- | ------------------------------------------------------------ | -------------- | --------------------------- |
| msg                  | -                                                            | object         | -                           |
| msg.timeList         | ["2025-08-15","2025-08-16","2025-08-17","2025-08-18","2025-08-19","2025-08-20","2025-08-21"] | array          | Chart Time                  |
| msg.yesterdayDataNum | 0                                                            | number         | Yesterday's passenger flow  |
| msg.nowDataNum       | 0                                                            | string         | Today's passenger flow      |
| msg.maxDate          | -                                                            | object         | -                           |
| msg.maxDate.date     | 2025-08-15                                                   | string         | Maximum passenger flow time |
| msg.maxDate.num      | 0                                                            | string         | Minimum passenger flow time |
| msg.numList          | [0, 0,  0,  0, 0, 0,  0]                                     | array          | Passenger flow chart        |
| code                 | 0                                                            | string         | -                           |

* fail(404)

```javascript
No data yet
```

**Request Header Parameter**

| Parameter name | Example value                                                | 参数类型 | 是否必填 | 参数描述 |
| -------------- | ------------------------------------------------------------ | -------- | -------- | -------- |
| authorization  | Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhY2NvdW50X2lkIjoiNjc1ZmY5ZGI3ZTUwNWM5OGQ3NzljMjA2IiwiZXhwIjoxNzU1OTA4NTgyLCJncm91cF9pZCI6IjY3NWZmOWRiN2U1MDVjOThkNzc5YzIwYSIsInVzZXJfaWQiOiI2NzVmZjlkYjdlNTA1Yzk4ZDc3OWMyMDcifQ.e1L3vHuhh_1OQ1akfDQg4QRMtKKHmYLVQQkSPbkFBfw | string   | 是       | -        |

**Query