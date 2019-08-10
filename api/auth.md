# API Reference

## Auth

### Endpoints

* [`POST /login`](#log-in-a-user)
* [`DELETE /login`](#log-out-a-user)
* [`GET /session`](#retrieve-a-session-user)

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
DELETE /login
-H x-session-token:99f37640-b4e9-11e9-a660-25ca1b2ae688
```

Response:

```
{
    "message": "User: ironman@avengers.com logged out successfully"
}
```

### Retrieve a session user
  
```
GET /session
-H x-session-token:99f37640-b4e9-11e9-a660-25ca1b2ae688
```

Response:

```
{
    "_id": "5d4e3665eb07587db335c395",
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
                    "_id": "5d4cc8708149620a29e73050",
                    "available": false,
                    "category": "Laptop - Mac",
                    "condition": "new",
                    "name": "MacBook Pro 13",
                    "sn": "1234567890",
                    "createdAt": "2019-08-09T01:12:16.246Z",
                    "updatedAt": "2019-08-10T13:17:13.104Z",
                    "__v": 0
}                ,
                {...},
                {...}
            ],
            "_id": "5d4ec0c4d48c4bac94edefe3",
            "out": "2019-08-01T00:00:00.000Z",
            "return": "2019-08-31T00:00:00.000Z",
            "status": "pending",
            "user": "5d4e3665eb07587db335c395",
            "createdAt": "2019-08-10T13:04:04.202Z",
            "updatedAt": "2019-08-10T13:04:04.202Z",
            "__v": 0
        },
        {...},
        {...}
    ],
    "createdAt": "2019-08-10T03:13:41.866Z",
    "email": "blackwidow@avengers.com",
    "name": "Natasha Romanovaa",
    "role": "user",
    "status": "active",
    "updatedAt": "2019-08-10T13:04:04.211Z"
}
```
