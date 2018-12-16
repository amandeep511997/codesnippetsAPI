# Snippets

Following are the attributes available on the snippet entity.

Attribute | Data Type | Description
--------- | ----------| ------------
id | integer | Id of the snippet
title | string | Title of the snippet
description | text | Description of the snippet
code | text | Code of the snippet
language | string | Programming Language of the snippet
version | decimal | Version of the language
bookmark_count | integer | Number of users who have bookmarked
upvotes | integer | Number of upvotes on snippet
downvotes | integer | Number of downvotes on snippet
created_at | datetime | Creation time of the snippet
updated_at | datetime | Last time when snippet was updated
private | boolean | The snippet is public if 'false'
author_id | integer | Id of the author who has posted the snippet
tags | list | All tags on the snippet


## Get All Snippets

```http
http GET https://codesnippets-org.herokuapp.com/api/v1/snippets
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/snippets"
```


> The above command returns JSON structured like this:

```json
{
    "snippets": [
        {
            "author_id": 2,
            "bookmark_count": 0,
            "code": "[code-here]",
            "created_at": "2018-01-16T13:39:20.026Z",
            "description": "This code is to reverse a LL",
            "downvotes": 0,
            "id": 1,
            "language": "C++",
            "private": false,
            "tags": [],
            "title": "Linked List Reversal",
            "updated_at": "2018-01-16T13:39:20.141Z",
            "upvotes": 0,
            "version": null
        },
        {
            "author_id": 1,
            "bookmark_count": 0,
            "code": "[code-here]",
            "created_at": "2018-01-16T14:01:13.747Z",
            "description": "Code to reverse an Array.",
            "downvotes": 0,
            "id": 2,
            "language": "C++",
            "private": false,
            "tags": [],
            "title": "Reverse an array",
            "updated_at": "2018-01-16T14:01:13.774Z",
            "upvotes": 0,
            "version": null
        }
    ]
}
```

This endpoint retrieves all the public snippets.

### HTTP Request

`GET https://codesnippets-org.herokuapp.com/api/v1/snippets`

### Query Parameters

Parameters can be set for pagination.

Parameter | Data Type | Description
--------- | ----------| ------------
page | integer | Set this to get snippets on a particular page number. It is None by default.
per_page | integer | Set this for limiting the number of snippets per page. It is None by default.

### Status
* 200 - OK - returns all snippets

## Get a Specific Snippet

```http
http POST https://codesnippets-org.herokuapp.com/api/v1/snippets/2 "Authorization:[user-auth-token]"
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/snippets/2"
  -X POST
  -H "Authorization: [user-auth-token]"
```

> The above command returns JSON structured like this - status 200:

```json
{
    "snippet": {
        "author_id": 1,
        "bookmark_count": 0,
        "code": "[code-here]",
        "created_at": "2018-01-16T14:01:13.747Z",
        "description": "Code to reverse an Array.",
        "downvotes": 0,
        "id": 2,
        "language": "C++",
        "private": false,
        "tags": [],
        "title": "Reverse an array",
        "updated_at": "2018-01-16T14:01:13.774Z",
        "upvotes": 0,
        "version": null
    }
}
```

> The above command returns JSON structured like this - status 404:

```
{
    "message": "Sorry, record not found."
}
```

This endpoint retrieves a specific snippet. Requires authentication token to be passed in headers. 

### HTTP Request

`POST https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to retrieve.

### Status
* 200 - OK - returns snippet
* 404 - Not Found


## Create a Snippet

```http
http POST https://codesnippets-org.herokuapp.com/api/v1/snippets 
title="BST traversal" description="Traverse BST in inorder fashion." language="C" code="[code-here]"
"Authorization:[user-auth-token]"
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/snippets"
  -X POST
  -H "Authorization:[user-auth-token]"
  -d { "title":"BST traversal", 
       "description":"Traverse BST in inorder fashion.", 
       "language":"C", 
       "code":"[code-here]" 
     }
```

> The above command returns JSON structured like this - status 201:

```json
{
    "snippet": {
        "author_id": 2,
        "bookmark_count": 0,
        "code": "[code-here]",
        "created_at": "2018-01-18T13:58:59.144Z",
        "description": "Traverse a BST in inorder fashion",
        "downvotes": 0,
        "id": 3,
        "language": "C++",
        "private": false,
        "tags": [],
        "title": "BST Traversal",
        "updated_at": "2018-01-18T13:58:59.320Z",
        "upvotes": 0,
        "version": null
    }
}
```

> The above command returns JSON structured like this - status 422:

```json
{
    "message": "Validation failed: Description can't be blank, Language can't be blank, Code can't be blank"
}

```

This endpoint creates a new snippet for authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`POST https://codesnippets-org.herokuapp.com/api/v1/snippets`

### URL Parameters

<aside class="warning" style="font-weight: bold;">
If you don't pass all the Required parameters, you will get a validation error message, that parameter can't be blank. With status 422 - unprocessible entity. 
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

### Status
* 201 - Created
* 422 - Unprocessable Entity - Errors related to validations.

## Update a Snippet

```http
http PUT https://codesnippets-org.herokuapp.com/api/v1/snippets/3 title="" "Authorization: [user-auth-token]"
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/snippets/3"
  -X PUT
  -H "Authorization: [user-auth-token]"
  -d { title:"" }
```

> The above command returns JSON structured like this - status 422:

```json
{
    "message": "Validation failed: Title can't be blank"
}

```

This endpoint updates an existing snippet of authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`PUT https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>`

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
private | boolean | If 'true' makes a snippet private.

### Status
* 204 - No Content - Successfully Updated
* 422 - Unprocessable Entity - Errors related to validations
* 404 - Not Found - If snippet with 'id' does not exists

## Delete a Specific Snippet

```http
http DELETE https://codesnippets-org.herokuapp.com/api/v1/snippets/2 "Authorization: [user-auth-token]"
```


```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/snippets/2"
  -X DELETE
  -H "Authorization: [user-auth-token]"
```

This endpoint deletes a specific snippet of authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`DELETE https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>`

### URL Parameters

<aside class="success" style="font-weight: bold;">
A successful deletion returns with status 204.
</aside>

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to be deleted.

### Status
* 204 - No Content - Successfully Deleted
* 404 - Not Found - If snippet with 'id' does not exists

## Search on Snippets

```http
http GET https://codesnippets-org.herokuapp.com/api/v1/snippets/search search="BST"
```


```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/snippets/search?search='BST'"
```


> The above command returns JSON structured like this:

```json
{
    "snippets": [
        {
            "author_id": 2,
            "bookmark_count": 0,
            "code": "[code-here]",
            "created_at": "2018-01-18T14:30:38.944Z",
            "description": "Traverse a BST in inorder fashion",
            "downvotes": 0,
            "id": 3,
            "language": "C++",
            "private": false,
            "tags": [],
            "title": "BST Traversal",
            "updated_at": "2018-01-18T14:30:38.968Z",
            "upvotes": 0,
            "version": null
        }
    ]
}
```

This endpoint searches all snippets for the passed parameters.

### HTTP Request

`GET https://codesnippets-org.herokuapp.com/api/v1/snippets/search/<search>`

### URL Parameters

<aside class="notice" style="font-weight: bold;">
Empty search parameter will return all public snippets
</aside>

Parameters can be set for pagination.

Parameter | Data Type | Description
--------- | ----------| ------------
search | string | Returns all snippets having content related to search parameters. 
page | integer | Set this to get snippets on a particular page number. It is None by default.
per_page | integer | Set this for limiting the number of snippets per page. It is None by default.

### Content which can be searched upon
* Title of snippet
* Description of snippet
* Language of snippet
* Tags of snippet
* Comments on snippet

### Status
* 200 - OK

## Upvote a Snippet

```http
http PUT https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>/upvote "Authorization: [user-auth-token]"
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>/upvote"
  -X PUT
  -H "Authorization: [user-auth-token]"
```


> The above command returns JSON structured like this - status 422:

```json
# If authenticated user tries to upvote his own snippet
{
    "message": "You cannot vote your own snippet"
}

# If authenticated user has already upvoted the snippet.
{
    "message": "You have already voted"
}
```

This endpoint can be used to upvote a snippet by authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`PUT https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>/upvote`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to be upvoted.

### Status
* 422 - Unprocessible Entity - returns messages.
* 200 - OK - successfully upvoted.

## Downvote a Snippet

```http
http PUT https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>/downvote "Authorization: [user-auth-token]"
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>/downvote"
  -X PUT
  -H "Authorization: [user-auth-token]"
```

> The above command returns JSON structured like this:

```json
# If authenticated user tries to downvote his own snippet
{
    "message": "You cannot vote your own snippet"
}

# If authenticated user has already downvoted the snippet.
{
    "message": "You have already voted"
}
```

This endpoint can be used to downvote a snippet by authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`PUT https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>/downvote`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to be downvoted.

### Status
* 422 - Unprocessible Entity - returns messages.
* 200 - OK - successfully downvoted.


## Bookmark a Snippet

```http
http PUT https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>/bookmark "Authorization: [user-auth-token]"
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>/bookmark"
  -X PUT
  -H "Authorization: [user-auth-token]"
```

> The above command returns JSON structured like this - status 200:

```json
{
    "message": "Snippet has been added to your bookmarks"
}

# If snippet was in bookmarks of the authenticated user.
{
    "message": "Snippet has been removed from your bookmarks"
}
```

> The above command returns JSON structured like this - status 422:

```json
{
    "message": "Unable to bookmark"
}
```

This endpoint can be used to bookmark a snippet by authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`PUT https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>/bookmark`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to be bookmarked.

### Status
* 200 - OK - successfully done bookmark operations.
* 422 - Unprocessible Entity.

## Download a Snippet

```http
http POST https://codesnippets-org.herokuapp.com/api/v1/snippets/3/download "Authorization: [user-auth-token]"
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/snippets/3/download"
  -X POST
  -H "Authorization: [user-auth-token]"
```


> The above command returns JSON structured like this:

```json
{
    "snippet": {
        "download_link": "https://codesnippets-org.herokuapp.com/snippets/3/download",
        "id": "3"
    }
}
```

This endpoint can be used to get a download link of a snippet. Requires authentication token to be passed in headers.

### HTTP Request

`POST https://codesnippets-org.herokuapp.com/api/v1/snippets/<id>/download`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the snippet to be downloaded.

### Status 
* 200 - OK
