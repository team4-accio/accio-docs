# API Reference

## Checkouts

### Endpoints

* [`POST /api/checkouts`](#create-a-checkout)
* [`GET /api/checkouts/:_id`](#retrieve-a-checkout)
* [`PATCH /api/checkouts/_id`](#update-a-checkout)
* [`DELETE /api/checkouts/_id`](#delete-a-checkout)
* [`GET /api/checkouts`](#list-all-checkouts)

### Create a checkout

Arguments

* items
  * type: list
  * *optional*
* out
  * type: date
  * *required*
* return
  * type: date
  * *required*
* status
  * type: string (enum)
  * enums: `approved`, `closed`, `pending`, `rejected`
  * *required*
* user
  * type: string (id)
  * *required*

``` 
POST /api/checkouts
```

```
{
    "items": ["5d422db239f8910d495aee65"],
    "out": "2019-08-01T00:00:00.000Z",
    "return": "2019-08-31T00:00:00.000Z",
    "status": "pending",
    "user": "5d422915501c450bd4230aac"
}
```

Response:

```
{
    "items": [
        {
            "description": "2019 MacBook Pro 13, i5, 256GB SSD, 8GB RAM",
            "tags": [
                "laptop",
                "macbook",
                "apple",
                "new"
            ],
            "_id": "5d422db239f8910d495aee65",
            "available": false,
            "category": "Laptop - Mac",
            "condition": "new",
            "name": "MacBook Pro 13",
            "sn": "123456789",
            "createdAt": "2019-08-01T00:09:22.552Z",
            "updatedAt": "2019-08-01T00:09:22.552Z",
            "__v": 0
        },
        {...},
        {...}
    ],
    "_id": "5d4236831c6f3b11c9783d63",
    "out": "2019-08-01T00:00:00.000Z",
    "return": "2019-08-31T00:00:00.000Z",
    "status": "pending",
    "user": "5d422915501c450bd4230aac",
    "createdAt": "2019-08-01T00:46:59.754Z",
    "updatedAt": "2019-08-01T00:46:59.754Z",
    "__v": 0
}
```

### Retrieve a checkout

Arguments

* checkout
  * type: string (id)
  * *required*
  
```
GET /api/checkouts/:_id
```

Response:

```
{
    "items": [
        {
            "description": "2019 MacBook Pro 13, i5, 256GB SSD, 8GB RAM",
            "tags": [
                "laptop",
                "macbook",
                "apple",
                "new"
            ],
            "_id": "5d422db239f8910d495aee65",
            "available": false,
            "category": "Laptop - Mac",
            "condition": "new",
            "name": "MacBook Pro 13",
            "sn": "123456789",
            "createdAt": "2019-08-01T00:09:22.552Z",
            "updatedAt": "2019-08-01T00:09:22.552Z",
            "__v": 0
        },
        {...},
        {...}
    ],
    "_id": "5d4236831c6f3b11c9783d63",
    "out": "2019-08-01T00:00:00.000Z",
    "return": "2019-08-31T00:00:00.000Z",
    "status": "pending",
    "user": "5d422915501c450bd4230aac",
    "createdAt": "2019-08-01T00:46:59.754Z",
    "updatedAt": "2019-08-01T00:46:59.754Z",
    "__v": 0
}
```

### Update a checkout

Arguments

* checkout
  * type: string (id)
  * *required*
* items
  * type: list
  * *optional*
* out
  * type: date
  * *optional*
* return
  * type: date
  * *optional*
* status
  * type: string (enum)
  * enums: `approved`, `closed`, `pending`, `rejected`
  * *optional*
* user
  * type: string (id)
  * *optional*

```
PATCH /api/checkouts/:_id
```

```
{
    "status": "approved"
}
```

Response:

```
{
    "items": [
        {
            "description": "2019 MacBook Pro 13, i5, 256GB SSD, 8GB RAM",
            "tags": [
                "laptop",
                "macbook",
                "apple",
                "new"
            ],
            "_id": "5d422db239f8910d495aee65",
            "available": false,
            "category": "Laptop - Mac",
            "condition": "new",
            "name": "MacBook Pro 13",
            "sn": "123456789",
            "createdAt": "2019-08-01T00:09:22.552Z",
            "updatedAt": "2019-08-01T00:09:22.552Z",
            "__v": 0
        },
        {...},
        {...}
    ],
    "_id": "5d4236831c6f3b11c9783d63",
    "out": "2019-08-01T00:00:00.000Z",
    "return": "2019-08-31T00:00:00.000Z",
    "status": "approved",
    "user": "5d422915501c450bd4230aac",
    "createdAt": "2019-08-01T00:46:59.754Z",
    "updatedAt": "2019-08-01T00:51:14.817Z",
    "__v": 0
}
```

### Delete a checkout

Arguments

* user
  * type: string (id)
  * *required*

```
DELETE /api/checkouts/:_id
```

Response:

```
{
    "n": 1,
    "ok": 1,
    "deletedCount": 1
}
```

### List all checkouts

Arguments

* items
  * type: list
  * *optional*
* out
  * type: date
  * *optional*
* return
  * type: date
  * *optional*
* status
  * type: string (enum)
  * enums: `approved`, `closed`, `pending`, `rejected`
  * *optional*
* user
  * type: string (id)
  * *optional*

```
GET /api/checkouts
```

Response:

```
[
    {
        "items": [
            {
                "description": "2019 MacBook Pro 13, i5, 256GB SSD, 8GB RAM",
                "tags": [
                    "laptop",
                    "macbook",
                    "apple",
                    "new"
                ],
                "_id": "5d422db239f8910d495aee65",
                "available": false,
                "category": "Laptop - Mac",
                "condition": "new",
                "name": "MacBook Pro 13",
                "sn": "123456789",
                "createdAt": "2019-08-01T00:09:22.552Z",
                "updatedAt": "2019-08-01T00:09:22.552Z",
                "__v": 0
            },
            {...},
            {...}
        ],
        "_id": "5d4236831c6f3b11c9783d63",
        "out": "2019-08-01T00:00:00.000Z",
        "return": "2019-08-31T00:00:00.000Z",
        "status": "pending",
        "user": "5d422915501c450bd4230aac",
        "createdAt": "2019-08-01T00:46:59.754Z",
        "updatedAt": "2019-08-01T00:46:59.754Z",
        "__v": 0
    },
    {...},
    {...}
]
```
