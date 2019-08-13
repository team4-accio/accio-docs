# API Reference

## Items

### Endpoints

* [`POST /api/items`](#create-an-item)
* [`GET /api/items/:_id`](#retrieve-an-item)
* [`PATCH /api/items/_id`](#update-an-item)
* [`DELETE /api/items/_id`](#delete-an-item)
* [`GET /api/items`](#list-all-items)

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

```js
axios.post("/api/items",
    {
        available: true,
	    category: "Laptop - Mac",
	    condition: "new",
	    description: "2019 MacBook Pro 13, i5, 256GB SSD, 8GB RAM",
	    name: "MacBook Pro 13",
	    sn: "123456789",
	    tags: ["laptop", "macbook", "apple", "new"]
    },
    {
        headers: {
            authorization: "86b89440-bb1d-11e9-8a28-0f10265f69af"
        }
    }
).then(function () {...});
```

Response:

```
{
    "description": "2019 MacBook Pro 13, i5, 256GB SSD, 8GB RAM",
    "tags": [],
    "_id": "5d4f10f04007c711c0ef8e4a",
    "available": false,
    "category": "Laptop - Mac",
    "condition": "new",
    "name": "MacBook Pro 13",
    "sn": "111111111",
    "createdAt": "2019-08-10T18:46:08.357Z",
    "updatedAt": "2019-08-11T20:57:34.382Z",
    "__v": 0
}
```

### Retrieve an item

Arguments

* item
  * type: string (id)
  * *required*
  
```js
axios.get("/api/items/5d4f10f04007c711c0ef8e4a", {
    headers: {
        authorization: "86b89440-bb1d-11e9-8a28-0f10265f69af"
    }
}).then(function () {...});
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
    "_id": "5d4f10f04007c711c0ef8e4a",
    "available": true,
    "category": "Laptop - Mac",
    "condition": "new",
    "name": "MacBook Pro 13",
    "sn": "111111111",
    "createdAt": "2019-08-10T18:46:08.357Z",
    "updatedAt": "2019-08-10T18:46:08.357Z",
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

```js
axios.patch("/api/items/5d4f10f04007c711c0ef8e4a", { available: false }, {
    headers: {
        authorization: "86b89440-bb1d-11e9-8a28-0f10265f69af"
    }
}).then(function () {...});
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
    "_id": "5d4f10f04007c711c0ef8e4a",
    "available": false,
    "category": "Laptop - Mac",
    "condition": "new",
    "name": "MacBook Pro 13",
    "sn": "111111111",
    "createdAt": "2019-08-10T18:46:08.357Z",
    "updatedAt": "2019-08-11T21:10:35.052Z",
    "__v": 0
}
```

### Delete an item

Arguments

* item
  * type: string (id)
  * *required*

```js
axios.delete("/api/items/5d4f10f04007c711c0ef8e4a", {
    headers: {
        authorization: "86b89440-bb1d-11e9-8a28-0f10265f69af"
    }
}).then(function () {...});
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

```js
axios.get("/api/items", {
    headers: {
        authorization: "86b89440-bb1d-11e9-8a28-0f10265f69af"
    },
    params: {
        available: true
    }
}).then(function () {...});
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
        "_id": "5d4f10f04007c711c0ef8e4a",
        "available": true,
        "category": "Laptop - Mac",
        "condition": "new",
        "name": "MacBook Pro 13",
        "sn": "111111111",
        "createdAt": "2019-08-10T18:46:08.357Z",
        "updatedAt": "2019-08-10T18:46:08.357Z",
        "__v": 0
    },
    {...},
    {...}
]
```
