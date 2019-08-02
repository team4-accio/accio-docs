# API Reference

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
