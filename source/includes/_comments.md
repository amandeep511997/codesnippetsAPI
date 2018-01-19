# Comments

Following are the attributes available on the comment entity.

Attribute | Data Type | Description
--------- | ----------| ------------
id | integer | Id of the comment
text | text | Text of the comment
created_at | datetime | Creation time of the comment
updated_at | datetime | Last time when comment was updated
snippet_id | integer | Id of the snippet on which the comment is posted
author_id | integer | Id of the user who has posted the comment

## Get All Comments on a Snippet


```http
http POST http://codesnippets.org/api/v1/snippets/3/all/commments "Authorization: [user-auth-token]"
```

```shell
curl "http://codesnippets.org/api/v1/snippets/3/all/commments"
  -X POST
  -H "Authorization: [user-auth-token]"
```

> The above command returns JSON structured like this - status 200:

```json
{
    "comments": [
        {
            "author_id": 2,
            "created_at": "2017-12-26T05:32:59.888Z",
            "id": 2,
            "snippet_id": 3,
            "text": "This is a useful snippet\r\n",
            "updated_at": "2017-12-26T05:32:59.888Z"
        },
        {
            "author_id": 1,
            "created_at": "2018-01-13T16:56:25.310Z",
            "id": 3,
            "snippet_id": 3,
            "text": "I found it helpful! Thanks :)",
            "updated_at": "2018-01-13T16:56:25.310Z"
        }
    ]
}

```

This endpoint retrieves all the comments on a snippets. Requires authentication token to be passed in headers.

### HTTP Request

`POST http://codesnippets.org/api/v1/snippets/<snippet_id>/all/comments`

### Query Parameters

Parameter | Data Type | Description
----------- | ----------| ------------
snippet_id | integer | The 'id' of the snippet whose comments you want to retrieve.

### Status 
* 200 - OK

## Get a specific Comment

```http
http POST http://codesnippets.org/api/v1/snippets/3/commments/2 "Authorization:[user-auth-token]"
```

```shell
curl "http://codesnippets.org/api/v1/snippets/3/commments/2"
  -X POST
  -H "Authorization:[user-auth-token]"
```

> The above command returns JSON structured like this:

```json
{
    "comment": {
        "author_id": 2,
        "created_at": "2017-12-26T05:32:59.888Z",
        "id": 2,
        "snippet_id": 3,
        "text": "This is a useful snippet\r\n",
        "updated_at": "2017-12-26T05:32:59.888Z"
    }
}
```

This endpoint retrieves a specific comment on a specific snippet. Requires authentication token to be passed in headers.


### HTTP Request

`POST http://codesnippets.org/api/v1/snippets/<snippet_id>/commments/<id>`

### URL Parameters

Parameter | Data Type | Description
----------- | ----------| ------------
snippet_id | integer | The 'id' of the snippet whose comment you want to retrieve.
id | integer | The 'id' of the comment you want to retrieve.

### Status
* 200 - OK
* 404 - Not Found

## Create a Comment

```http
http POST http://codesnippets.org/api/v1/snippets/3/comments text="This snippet is cool!" "Authorization:[user-auth-token]"
```

```shell
curl "http://codesnippets.org/api/v1/snippets/3/comments"
  -X POST
  -H "Authorization:[user-auth-token]"
  -d { "text":"This snippet is cool!" }
```

> The above command returns JSON structured like this - status 201:

```json
{
    "comment": {
        "author_id": 2,
        "created_at": "2018-01-18T16:20:24.428Z",
        "id": 4,
        "snippet_id": 3,
        "text": "This snippet is cool!",
        "updated_at": "2018-01-18T16:20:24.594Z"
    }
}
```

> The above command returns JSON structured like this - status 422:

```json
{
    "message": "Validation failed: Text can't be blank"
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

### Status
* 201 - Created
* 422 - Unprocessable Entity - Errors related to validations.


## Update a Comment

```http
http PUT http://codesnippets.org/api/v1/snippets/3/comments/4 text="" "Authorization: [user-auth-token]"
```

```shell
curl "http://codesnippets.org/api/v1/snippets/3/comments/4"
  -X PUT
  -H "Authorization: [user-auth-token]"
  -d { text:"" }
```

> The above command returns JSON structured like this - status 422:

```json
{
    "message": "Validation failed: Text can't be blank"
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

### Status
* 204 - No Content - Successfully Updated
* 422 - Unprocessable Entity - Errors related to validations