# Recipes

## Table of Contents

* [List all available items](#list-all-available-items)
* [Create a checkout with 3 items](#create-a-checkout-with-3-items)
* [List all users with pending checkouts](#list-all-users-with-pending-checkouts)
* [List all overdue checkouts](#list-all-overdue-checkouts)

## List all available items

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

## Create a checkout with 3 items

```js
axios.post("/api/checkouts",
    {
        "items": [
        	"5d5328ea9a5c2fefbf30b6ef",
        	"5d5329469a5c2fefbf30b6f1",
        	"5d5329619a5c2fefbf30b6f2"
        ],
        "out": "2019-08-01T00:00:00.000Z",
        "return": "2019-08-31T00:00:00.000Z",
        "status": "pending",
        "user": "5d4f0ee64007c711c0ef8e49"
    },
    {
        headers: {
            authorization: "86b89440-bb1d-11e9-8a28-0f10265f69af"
        }
    }
).then(function () {...});
```

## List all users with pending checkouts

```js
axios.get("/api/checkouts", {
    headers: {
        authorization: "86b89440-bb1d-11e9-8a28-0f10265f69af"
    },
    params: {
        status: "pending"
    }
}).then(function (checkouts) {
    // Generate array of concurrent GET /api/users/:_id requests for each pending checkout
    const requests = checkouts.map(checkout => axios.get(`/api/users/${checkout.user}`));
    axios.all(requests)
        .then(axios.spread(function () {...}));
});
```

## List all overdue checkouts

```js
axios.get("/api/checkouts", {
    headers: {
        authorization: "86b89440-bb1d-11e9-8a28-0f10265f69af"
    },
    params: {
        return: {
            $lt: "2019-08-13T00:00:00.000Z" // Today's datetime
        }
    }
}).then(function () {...});
```
