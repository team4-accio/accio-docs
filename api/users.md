# API Reference

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
