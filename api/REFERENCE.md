# API Reference

## Table of Contents

* [auth](#auth)
* [checkouts](#checkouts)
* [items](#items)
* [users](#users)

---

## Auth

### Endpoints

* [`POST /login`](#log-in-a-user)
* [`POST /logout`](#log-out-a-user)

### Log in a user

Arguments

* email
  * type: string (email)
  * *required*
* password
  * type: string (hash)
  * *required*

``` 
POST /login
```

```
{
	"email": "ironman@avengers.com",
	"password": "password"
}
```

Response:

```
-H x-session-token:99f37640-b4e9-11e9-a660-25ca1b2ae688
```

```
{
    "_id": "5d435546947f0b7bdc41f451",
    "checkouts": [
        {
            "items": [
                "5d422db239f8910d495aee65"
            ],
            "_id": "5d43cbb7c7a2a30ce193dfab",
            "out": "2019-08-01T00:00:00.000Z",
            "return": "2019-08-31T00:00:00.000Z",
            "status": "pending",
            "user": "5d435546947f0b7bdc41f451",
            "createdAt": "2019-08-02T05:35:51.898Z",
            "updatedAt": "2019-08-02T05:35:51.898Z",
            "__v": 0
        }
    ],
    "createdAt": "2019-08-01T21:10:30.071Z",
    "email": "ironman@avengers.com",
    "name": "Tony Stark",
    "role": "user",
    "status": "inactive",
    "updatedAt": "2019-08-02T05:51:41.478Z"
}
```

### Log out a user
  
```
POST /logout
-H x-session-token:99f37640-b4e9-11e9-a660-25ca1b2ae688
```

Response:

```
{
    "message": "User: ironman@avengers.com logged out successfully"
}
```

## Checkouts

### Endpoints

* [`POST /api/items`](#create-a-checkout)
* [`GET /api/items/:_id`](#retrieve-a-checkout)
* [`PATCH /api/items/_id`](#update-a-checkout)
* [`DELETE /api/items/_id`](#delete-a-checkout)
* [`GET /api/items`](#list-all-checkouts)

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
    "_id": "5d422db239f8910d495aee65",
    "available": true,
    "category": "Laptop - Mac",
    "condition": "new",
    "name": "MacBook Pro 13",
    "sn": "123456789",
    "createdAt": "2019-08-01T00:09:22.552Z",
    "updatedAt": "2019-08-01T00:09:22.552Z",
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
    "_id": "5d422db239f8910d495aee65",
    "available": true,
    "category": "Laptop - Mac",
    "condition": "new",
    "name": "MacBook Pro 13",
    "sn": "123456789",
    "createdAt": "2019-08-01T00:09:22.552Z",
    "updatedAt": "2019-08-01T00:09:22.552Z",
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
	"status": "inactive"
}
```

Response:

```
{
    "checkout": [],
    "session": null,
    "_id": "5d41b7e4ac06494b7b7a9d82",
    "email": "jlouie@gmail.com",
    "name": "Justin Louie",
    "password": "password",
    "role": "admin",
    "salt": "123",
    "status": "inactive",
    "createdAt": "2019-07-31T15:46:44.009Z",
    "updatedAt": "2019-07-31T15:47:41.679Z",
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
        "_id": "5d422db239f8910d495aee65",
        "available": true,
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
]
```

## Users

### Endpoints

* [`POST /api/users`](#create-a-user)
* [`GET /api/users/:_id`](#retrieve-a-user)
* [`PATCH /api/users/_id`](#update-a-user)
* [`DELETE /api/users/_id`](#delete-a-user)
* [`GET /api/users`](#list-all-users)

### Create a user

Arguments

* checkouts
  * type: list
  * *optional*
* email
  * type: string (email)
  * *required*
* name
  * type: string
  * *required*
* password
  * type: string (hash)
  * *required*
* passwordConfirm
  * type: string (hash)
  * *required*
* role
  * type: string (enum)
  * enums: `admin`, `user`
  * *required*
* salt
  * type: string
  * *required*
* session
  * type: string
  * *optional*
* status
  * type: string (enum)
  * enums: `active`, `inactive`
  * *required*

``` 
POST /api/users
```

```
{
	"email": "ironman@avengers.com",
	"name": "Tony Stark",
	"password": "password",
	"passwordConfirm": "password",
	"role": "user",
	"status": "active"
}
```

Response:

```
{
    "_id": "5d435546947f0b7bdc41f451",
    "checkouts": [],
    "createdAt": "2019-08-01T21:10:30.071Z",
    "email": "ironman@avengers.com",
    "name": "Tony Stark",
    "role": "user",
    "status": "active",
    "updatedAt": "2019-08-01T21:10:30.071Z"
}
```

### Retrieve a user

Arguments

* user
  * type: string (id)
  * *required*
  
```
GET /api/users/:_id
```

Response:

```
{
    "checkouts": [
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
                    "_id": "5d43d761952a2b11123e74a6",
                    "available": false,
                    "category": "Laptop - Mac",
                    "condition": "new",
                    "name": "MacBook Pro 13",
                    "sn": "123456789",
                    "createdAt": "2019-08-02T06:25:37.757Z",
                    "updatedAt": "2019-08-02T06:25:37.757Z",
                    "__v": 0
                }
            ],
            "_id": "5d43cbb7c7a2a30ce193dfab",
            "out": "2019-08-01T00:00:00.000Z",
            "return": "2019-08-31T00:00:00.000Z",
            "status": "approved",
            "user": "5d435546947f0b7bdc41f451",
            "createdAt": "2019-08-02T05:35:51.898Z",
            "updatedAt": "2019-08-02T06:25:59.813Z",
            "__v": 0
        },
        {...},
        {...}
    ],
    "createdAt": "2019-08-01T21:10:30.071Z",
    "email": "ironman@avengers.com",
    "name": "Tony Stark",
    "role": "user",
    "status": "active",
    "updatedAt": "2019-08-02T05:35:51.953Z"
}
```

### Update a user

Arguments

* user
  * type: string (id)
  * *required*
* checkouts
  * type: list
  * *optional*
* email
  * type: string (email)
  * *optional*
* name
  * type: string
  * *optional*
* role
  * type: string (enum)
  * enums: `admin`, `user`
  * *optional*
* status
  * type: string (enum)
  * enums: `active`, `inactive`
  * *optional*

```
PATCH /api/users/:_id
```

```
{
	"status": "inactive"
}
```

Response:

```
{
    "_id": "5d435546947f0b7bdc41f451",
    "checkouts": [
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
                    "_id": "5d43d761952a2b11123e74a6",
                    "available": false,
                    "category": "Laptop - Mac",
                    "condition": "new",
                    "name": "MacBook Pro 13",
                    "sn": "123456789",
                    "createdAt": "2019-08-02T06:25:37.757Z",
                    "updatedAt": "2019-08-02T06:25:37.757Z",
                    "__v": 0
                }
            ],
            "_id": "5d43cbb7c7a2a30ce193dfab",
            "out": "2019-08-01T00:00:00.000Z",
            "return": "2019-08-31T00:00:00.000Z",
            "status": "approved",
            "user": "5d435546947f0b7bdc41f451",
            "createdAt": "2019-08-02T05:35:51.898Z",
            "updatedAt": "2019-08-02T06:25:59.813Z",
            "__v": 0
        },
        {...},
        {...}
    ],
    "createdAt": "2019-08-01T21:10:30.071Z",
    "email": "ironman@avengers.com",
    "name": "Tony Stark",
    "role": "user",
    "status": "inactive",
    "updatedAt": "2019-08-02T05:42:32.006Z"
}
```

### Delete a user

Arguments

* user
  * type: string (id)
  * *required*

```
DELETE /api/users/:_id
```

Response:

```
{
    "n": 1,
    "ok": 1,
    "deletedCount": 1
}
```

### List all users

Arguments

* checkouts
  * type: list
  * *optional*
* email
  * type: string (email)
  * *optional*
* name
  * type: string
  * *optional*
* role
  * type: string (enum)
  * enums: `admin`, `user`
  * *optional*
* status
  * type: string (enum)
  * enums: `active`, `inactive`
  * *optional*

```
GET /api/users
```

Response:

```
[
    {
        "checkouts": [
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
                    "_id": "5d43d761952a2b11123e74a6",
                    "available": false,
                    "category": "Laptop - Mac",
                    "condition": "new",
                    "name": "MacBook Pro 13",
                    "sn": "123456789",
                    "createdAt": "2019-08-02T06:25:37.757Z",
                    "updatedAt": "2019-08-02T06:25:37.757Z",
                    "__v": 0
                }
            ],
            "_id": "5d43cbb7c7a2a30ce193dfab",
            "out": "2019-08-01T00:00:00.000Z",
            "return": "2019-08-31T00:00:00.000Z",
            "status": "approved",
            "user": "5d435546947f0b7bdc41f451",
            "createdAt": "2019-08-02T05:35:51.898Z",
            "updatedAt": "2019-08-02T06:25:59.813Z",
            "__v": 0
            },
            {...},
            {...}
        ],
        "createdAt": "2019-08-01T21:10:30.071Z",
        "email": "ironman@avengers.com",
        "name": "Tony Stark",
        "role": "user",
        "status": "active",
        "updatedAt": "2019-08-02T05:35:51.953Z"
    },
    {...},
    {...}
]
```
