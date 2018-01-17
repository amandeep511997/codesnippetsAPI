# Snippets

## Get All Snippets


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

This endpoint retrieves all the public snippets.

### HTTP Request

`GET http://codesnippets.org/api/v1/snippets`

### Query Parameters

Parameters can be set for pagination.

Parameter | Default | Description
--------- | ------- | -----------
page | None | Set this to get snippets on a particular page number. 
per_page | None | Set this for limiting the number of snippets per page.



## Get a Specific Snippet


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

This endpoint retrieves a specific snippet. 

<aside class="notice" style="font-weight: bold;">
You can access any private snippet of the authenticated user by passing the authentication token in header.<br> 
You may not pass the authentication token to get a public snippet.
</aside>

### HTTP Request

`GET http://codesnippets.org/api/v1/snippets/<id>`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to retrieve.


## Create a Snippet

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

This endpoint creates a new snippet for authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`POST http://codesnippets.org/api/v1/snippets`

### URL Parameters

<aside class="warning" style="font-weight: bold;">
If you don't pass all the Required parameters, you may get a validation error message, that parameter can't be blank. With status 422 - unprocessible entity. 
</aside>

Required Parameter | Data Type | Description
------------------ | ----------| ------------
title | string | The 'title' of the snippet to be created.
description| text | The 'description' about the snippet to be created.
language| string | The 'language' of the snippet.
code | text | The 'code' of the snippet to be created.

<br>

Optional Parameter | Data Type | Description
------------------ | ----------| ------------
version | decimal | The 'version' of the language of snippet.
tag_names| string | The 'tags' of the snippet to be created.
private | boolean | Creates a public snippet by default. If 'true' creates a private snippet.

### Some Important Instructions
1. codesnippets is NOT a Debugging tool; it is intended for finished, working pieces of code.
2. By posting a public snippet, you agree to let anyone make use of the code.
3. You can use Markdown syntax for description, but raw HTML will be removed. Guide about markdown [here](https://guides.github.com/features/mastering-markdown/).
4. Use spaces between tag names, and hyphens for multiple words, example - "tag1 tag2 tag3-with-long-name"
5. Private snippet will not be visible to other users, and will only be shown on your profile.

## Update a Snippet

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

This endpoint updates an existing snippet of authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`PUT http://codesnippets.org/api/v1/snippets/<id>`

### URL Parameters

<aside class="warning" style="font-weight: bold;">
If you don't pass the id, you may get an unexpected response.
</aside>

Required Parameter | Data Type | Description
------------------ | ----------| ------------
id | integer | The 'id' of the snippet to be updated.

<br>

Optional Parameter | Data Type | Description
------------------ | ----------| ------------
title | string | The 'title' of the snippet to be updated.
description| text | The 'description' about the snippet to be updated.
language| string | The 'language' of the snippet.
code | text | The 'code' of the snippet to be updated.
version | decimal | The 'version' of the language of snippet.
tag_names| string | The 'tags' of the snippet to be created.
private | boolean | Creates a public snippet by default. If 'true' creates a private snippet.

## Delete a Specific Snippet


```http
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific snippet of authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`DELETE http://codesnippets.org/api/v1/snippets/<id>`

### URL Parameters

<aside class="success" style="font-weight: bold;">
A successful deletion returns with status 204.
</aside>

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to be deleted.

## Search on Snippets


```http
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint searches all snippets for the passed parameters.

### HTTP Request

`GET http://codesnippets.org/api/v1/snippets/<search>`

### URL Parameters

<aside class="notice" style="font-weight: bold;">
Empty search parameter will return all public snippets
</aside>

Parameter | Data Type | Description
--------- | ----------| ------------
search | text | Returns all snippets having content related to search parameters. 

### Content which can be searched upon
* Title of snippet
* Description of snippet
* Language of snippet
* Tags of snippet
* Comments on snippet

## Upvote a Snippet


```http
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint can be used to upvote a snippet by authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`PUT http://codesnippets.org/api/v1/snippets/<id>/upvote`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to be upvoted.

## Downvote a Snippet


```http
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint can be used to downvote a snippet by authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`PUT http://codesnippets.org/api/v1/snippets/<id>/downvote`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to be downvoted.

## Bookmark a Snippet


```http
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint can be used to bookmark a snippet by authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`PUT http://codesnippets.org/api/v1/snippets/<id>/bookmark`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to be bookmarked.

## Download a Snippet


```http
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint can be used to get a download link of a snippet. For a download link of a private snippet, you need to pass the authentication token in headers.

### HTTP Request

`GET http://codesnippets.org/api/v1/snippets/<id>/download`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to be downloaded.
