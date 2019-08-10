# API Reference

## Items

### Endpoints

* [`POST /api/users`](#create-an-item)
* [`GET /api/users/:_id`](#retrieve-an-item)
* [`PATCH /api/users/_id`](#update-an-item)
* [`DELETE /api/users/_id`](#delete-an-item)
* [`GET /api/users`](#list-all-items)

### Create an item

Arguments

* available
  * type: boolean
  * *required*
* category
  * type: string (enum)
  * enums: `Laptop - Mac`, `Laptop - PC`, `iPad`, `keyboard`, `mouse`
  * *required*
* condition
  * type: string (enum)
  * enums: `new`, `good`, `okay`, `bad`
  * *required*
* description
  * type: string
  * *optional*
* name
  * type: string
  * *required*
* sn
  * type: string
  * *required*
* tags
  * type: list
  * *optional*

``` 
POST /api/items
```

```
{
	"available": true,
	"category": "Laptop - Mac",
	"condition": "new",
	"description": "2019 MacBook Pro 13, i5, 256GB SSD, 8GB RAM",
	"name": "MacBook Pro 13",
	"sn": "123456789",
	"tags": ["laptop", "macbook", "apple", "new"]
}
```

Response:

```
{
    "description": "2019 MacBook Pro 13, i5, 256GB SSD, 8GB RAM",
    "tags": [
            "laptop",
            "macbook",
            "apple",
            "new"
        ],
    "_id": "5d4cc8708149620a29e73050",
    "available": true,
    "category": "Laptop - Mac",
    "condition": "new",
    "name": "MacBook Pro 13",
    "sn": "1234567890",
    "createdAt": "2019-08-09T01:12:16.246Z",
    "updatedAt": "2019-08-09T01:12:16.246Z",
    "__v": 0
}
```

### Retrieve an item

Arguments

* item
  * type: string (id)
  * *required*
  
```
GET /api/items/:_id
```

Response:

```
{
    "description": "2019 MacBook Pro 13, i5, 256GB SSD, 8GB RAM",
    "tags": [
            "laptop",
            "macbook",
            "apple",
            "new"
        ],
    "_id": "5d4cc8708149620a29e73050",
    "available": true,
    "category": "Laptop - Mac",
    "condition": "new",
    "name": "MacBook Pro 13",
    "sn": "1234567890",
    "createdAt": "2019-08-09T01:12:16.246Z",
    "updatedAt": "2019-08-09T01:12:16.246Z",
    "__v": 0
}
```

### Update an item

Arguments

* item
  * type: string (id)
  * *required*
* available
  * type: boolean
  * *optional*
* category
  * type: string (enum)
  * enums: `Laptop - Mac`, `Laptop - PC`, `iPad`, `keyboard`, `mouse`
  * *optional*
* condition
  * type: string (enum)
  * enums: `new`, `good`, `okay`, `bad`
  * *optional*
* description
  * type: string
  * *optional*
* name
  * type: string
  * *optional*
* sn
  * type: string
  * *optional*
* tags
  * type: list
  * *optional*

```
PATCH /api/items/:_id
```

```
{
	"available": false
}
```

Response:

```
{
    "description": "2019 MacBook Pro 13, i5, 256GB SSD, 8GB RAM",
    "tags": [
            "laptop",
            "macbook",
            "apple",
            "new"
        ],
    "_id": "5d4cc8708149620a29e73050",
    "available": false,
    "category": "Laptop - Mac",
    "condition": "new",
    "name": "MacBook Pro 13",
    "sn": "1234567890",
    "createdAt": "2019-08-09T01:12:16.246Z",
    "updatedAt": "2019-08-10T13:17:13.104Z",
    "__v": 0
}
```

### Delete an item

Arguments

* item
  * type: string (id)
  * *required*

```
DELETE /api/items/:_id
```

Response:

```
{
    "n": 1,
    "ok": 1,
    "deletedCount": 1
}
```

### List all items

Arguments

* available
  * type: boolean
  * *optional*
* category
  * type: string (enum)
  * enums: `Laptop - Mac`, `Laptop - PC`, `iPad`, `keyboard`, `mouse`
  * *optional*
* condition
  * type: string (enum)
  * enums: `new`, `good`, `okay`, `bad`
  * *optional*
* description
  * type: string
  * *optional*
* name
  * type: string
  * *optional*
* sn
  * type: string
  * *optional*
* tags
  * type: list
  * *optional*

```
GET /api/items
```

Response:

```
[
    {
        "description": "2019 MacBook Pro 13, i5, 256GB SSD, 8GB RAM",
        "tags": [
                "laptop",
                "macbook",
                "apple",
                "new"
            ],
        "_id": "5d4cc8708149620a29e73050",
        "available": true,
        "category": "Laptop - Mac",
        "condition": "new",
        "name": "MacBook Pro 13",
        "sn": "1234567890",
        "createdAt": "2019-08-09T01:12:16.246Z",
        "updatedAt": "2019-08-09T01:12:16.246Z",
        "__v": 0
    },
    {...},
    {...}
]
```
