# Users

Following are the attributes available on the user entity.

Attribute | Data Type | Description
--------- | ----------| ------------
id | integer | Id of the user
email | string | Email of the user
name | string | Name of the user
languages | string | Programming Languages user knows
github_link | string | Github profile link of the user
blog_link | string | Blog link of the user
linkedin_link | string | Likedin profile link of the user
twitter_link | string | Twitter profile link of the user
contributions | integer | Contributions of the user
bio | text | About user
user_image_url | string | Link of the user's profile image
created_at | datetime | Creation time of the snippet

## Get All Users

```http
http GET https://codesnippets-org.herokuapp.com/api/v1/users
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/users"
```


> The above command returns JSON structured like this:

```json
{
    "users": [
        {
            "bio": "Administrator Codesnippets",
            "blog_link": "[blog-link]",
            "contributions": 2,
            "created_at": "2017-12-23T17:02:14.423Z",
            "email": "[email]",
            "github_link": "[github-link]",
            "id": 1,
            "languages": "C++ Rails Ruby",
            "linkedin_link": "[linkedin-link]",
            "name": "Admin",
            "twitter_link": "[twitter-link]",
            "user_image_url": "[user-image-link]"
        },
        {
            "bio": "I am Rails Developer",
            "blog_link": "[blog-link]",
            "contributions": 0,
            "created_at": "2017-12-23T17:02:14.423Z",
            "email": "[email]",
            "github_link": "[github-link]",
            "id": 2,
            "languages": "Rails Ruby",
            "linkedin_link": "[linkedin-link]",
            "name": "Andrew",
            "twitter_link": "[twitter-link]",
            "user_image_url": "[user-image-link]"
        }
    ]
}
```

This endpoint retrieves all the registered users, excluding the archived users, in decreasing order of their contributions. 

### HTTP Request

`GET https://codesnippets-org.herokuapp.com/api/v1/users`

### Query Parameters

Parameters can be set for pagination.

Parameter | Data Type | Description
--------- | ----------| ------------
page | integer | Set this to get users on a particular page number. It is None by default.
per_page | integer | Set this for limiting the number of users per page. It is None by default.


## Get a Specific User

```http
http GET https://codesnippets-org.herokuapp.com/api/v1/users/2
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/users/2"
```

> The above command returns JSON structured like this:

```json
{
    "user": {
        "bio": "I am Rails Developer",
        "blog_link": "[blog-link]",
        "contributions": 0,
        "created_at": "2017-12-23T17:02:14.423Z",
        "email": "[email]",
        "github_link": "[github-link]",
        "id": 2,
        "languages": "Rails Ruby",
        "linkedin_link": "[linkedin-link]",
        "name": "Andrew",
        "twitter_link": "[twitter-link]",
        "user_image_url": "[user-image-link]"
    }
}

```

This endpoint retrieves details of a specific user. 

<aside class="notice" style="font-weight: bold;">
You can get details of an archived user also.
</aside>

### HTTP Request

`GET https://codesnippets-org.herokuapp.com/api/v1/users/<id>`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the user.

## Get Snippets of User

```http
http POST https://codesnippets-org.herokuapp.com/api/v1/users/2/snippets "Authorization:[user-auth-token]"
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/users/2/snippets"
  -X POST
  -H "Authorization:[user-auth-token]"
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
            "private": true,
            "tags": [],
            "title": "Linked List Reversal",
            "updated_at": "2018-01-16T13:39:20.141Z",
            "upvotes": 0,
            "version": null
        },
        {
            "author_id": 2,
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

This endpoint retrieves all public snippets of a user. If the requested user is authenticated user then this request returns both public and private snippets of the user. Requires authentication token to be passed in headers.  

### HTTP Request

`POST https://codesnippets-org.herokuapp.com/api/v1/users/<id>/snippets`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the user.

## Get Bookmarks of User

```http
http POST https://codesnippets-org.herokuapp.com/api/v1/users/2/bookmarks "Authorization:[user-auth-token]"
```

```shell
curl "https://codesnippets-org.herokuapp.com/api/v1/users/2/bookmarks"
  -X POST
  -H "Authorization:[user-auth-token]"
```

> The above command returns JSON structured like this:

```json
{
    "snippet": {
        "author_id": 1,
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

This endpoint retrieves all the bookmarks of the authenticated user. Requires authentication token to be passed in headers. 

### HTTP Request

`POST https://codesnippets-org.herokuapp.com/api/v1/users/<id>/bookmarks`

### URL Parameters

Parameter | Data Type | Description
--------- | ----------| ------------
id | integer | The 'id' of the user.