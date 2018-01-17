---
title: codesnippetsAPI

language_tabs: # must be one of https://git.io/vQNgJ
  - http

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the [**codesnippets**](http://codesnippets.org/) API! documentation. This is a RESTful API using which you can get information on various snippets and users in our database. You can view code examples in the dark area to the right.

<aside class="notice"> 
Our most recent API is V1.
</aside>



# Authentication

> To authorize, use this code:

```http
# With http, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```


> Make sure to replace `meowmeowmeow` with your API key.

<aside class="success">
Remember — a happy user is an authenticated user!
</aside>

To authenticate against codesnippets, you need an API access token, which you can get by following the code example given on the right once you have the account registered. If you are a new member you can register [here](http://codesnippets.org/users/sign_up).

codesnippets expects for the API access token to be included in some API requests to the server in a header that looks like the following:

`Authorization: [your-auth-token]`

In the future, we are planning to add a proper OAuth handshake for third party applications.

<aside class="notice">
You must replace <code>[your-auth-token]</code> with your personal API access token.
</aside>

# Kittens

## Get All Kittens


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

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Kitten


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

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten


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

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

