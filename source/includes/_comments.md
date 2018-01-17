# Comments

## Get All Comments on a Snippet


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

This endpoint retrieves all the comments on a public snippets. For fetching comments on a private snippet you need to pass authentication token in headers.

### HTTP Request

`GET http://codesnippets.org/api/v1/snippets/<snippet_id>/comments`

### Query Parameters

Parameter | Data Type | Description
----------- | ----------| ------------
snippet_id | integer | The 'id' of the snippet whose comments you want to retrieve.

## Get a specific Comment


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

This endpoint retrieves a specific comment on a specific snippet. For fetching a specific comment on a private snippet you need to pass authentication token in headers.


### HTTP Request

`GET http://codesnippets.org/api/v1/snippets/<snippet_id>/commments/<id>`

### URL Parameters

Parameter | Data Type | Description
----------- | ----------| ------------
snippet_id | integer | The 'id' of the snippet whose comment you want to retrieve.
id | integer | The 'id' of the comment you want to retrieve.

## Create a Comment

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

This endpoint creates a new comment on a snippet for authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`POST http://codesnippets.org/api/v1/snippets/<snippet_id>/comments`

### URL Parameters

<aside class="warning" style="font-weight: bold;">
If you don't pass the text parameter, you will get a validation error message, that text can't be blank. With status 422 - unprocessible entity. 
</aside>

Parameter | Data Type | Description
----------- | ----------| ------------
snippet_id | integer | The 'id' of the snippet on which you want to comment
text | text | Content of the comment to be created. 

*You may use Markdown syntax in text parameter, but raw HTML will be removed.*

## Update a Comment

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

This endpoint updates an existing comment on a snippet of authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`PUT http://codesnippets.org/api/v1/snippets/<snippet_id>/comments/<id>`

### URL Parameters

<aside class="notice" style="font-weight: bold;">
Obviously, you can update comments created by the authenticated user only.
</aside>

Parameter | Data Type | Description
----------- | ----------| ------------
snippet_id | integer | The 'id' of the snippet on which you want to update comment.
id | integer | The 'id' of the comment you want to update. 
text | text | Content of the updated comment. 

