# Users

## Get All Users


```http
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```


> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all the registered users, excluding the archived users. 

### HTTP Request

`GET http://codesnippets.org/api/v1/users`

### Query Parameters

Parameters can be set for pagination.

Parameter | Data Type | Description
--------- | ----------| ------------
page | integer | Set this to get users on a particular page number. It is None by default.
per_page | integer | Set this for limiting the number of users per page. It is None by default.

## Get a Specific User


```http
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves details of a specific user. 

<aside class="notice" style="font-weight: bold;">
You can get details of an archived user also.
</aside>

### HTTP Request

`GET http://codesnippets.org/api/v1/users/<id>`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the user.

## Get Snippets of User


```http
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves all public snippets of a user. If the requested user is authenticated user then this request returns both public and private snippets of the user, and in this case you need to pass the authentication token in headers.  

### HTTP Request

`GET http://codesnippets.org/api/v1/users/<id>/snippets`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the user.

## Get Bookmarks of User


```http
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves all the bookmarks of the authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`GET http://codesnippets.org/api/v1/users/<id>/bookmarks`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the user.