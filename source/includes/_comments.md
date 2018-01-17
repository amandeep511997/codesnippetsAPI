# Comments

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
