# fixed point-EN

#### Region Modem Interfaces

##### 1.1 Add a Region

```
URL: `/v1/cms/region/add`
- Method: `post`
- Need token or not: "Need"
- Request data:
  - `name`: string, region name, required
  - `lat`: string, latitude, required
  - `lng`: string, longitude, required
  - `radius`: int, radius unit meter
  - `tag_id_list`: string, type’s array tag id array, can be empty, but once filled, each item in the array must be the legal_id character string.
  - `is_foreign`: bool, whether create in the google map, default is false
- Response data:
  ```json
  {
    "error_code": 1002,
    "msg": "create data success"
  }

```

#####  1.2 Update a Region

```
	URL: `/v1/cms/region/:id/update`
 Method: `put`
 Need token or not: "Need"
 Request data: The same way with above interface, so omit.
 Response:
  ```json
  {
    "error_code": 1003,
    "msg": "update success"
  }

```

##### 1.3Delete a Region

```
URL: `/v1/cms/region/:id/delete`
- Method: `delete`
- Need token or not: "Need"
- Return data:
  ```json
  {
    "error_code": 1004,
    "msg": "delete success"
  }

```

##### 1.4 Get List

```
URL: `/v1/cms/region/list`
- Method: `get`
- Need token or not: "Need"
- Supported query parameters:
  - `page`: int, current page number, default is 1 if not filled
  - `pageSize`: int, items in one page, default is 10 if not filled
  - `is_foreign`: bool, whether created in the google map
  - `tag_id_list`: string, use English comma to divide several tag id
- Return data:
  ```json
  {
    "data": [
      {
        "id": "5ff2bb7ca5140838181ceacd",
        "date_created": "2021-01-04T14:53:48.038+08:00",
        "name": "xxxx",
        "lat": "31.111111",
        "lng": "123.1111111",
        "currency": 0,
        "radius": 10000,
        "price": 0,
        "is_foreign": false,
        "allow_deleted": 0,
        "tag_list": []
      }
    ], 
    "error_code": 1000,
    "msg": "get list data success",
    "totalCount": 1
  }

```