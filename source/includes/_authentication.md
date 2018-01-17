# Authentication

> To authorize, use this code:

```http
# With http, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```


> Make sure to replace `meowmeowmeow` with your API key.

<aside class="success" style="font-weight: bold;">
Remember — a happy user is an authenticated user!
</aside>

To authenticate against codesnippets, you need an API access token, which you can get by following the code example given on the right once you have the account registered. If you are a new member you can register [here](http://codesnippets.org/users/sign_up).

codesnippets expects for the API access token to be included in some API requests to the server in a header that looks like the following:

`Authorization: [your-auth-token]`

In the future, we are planning to add a proper OAuth handshake for third party applications.

<aside class="notice" style="font-weight: bold;">
You must replace <code>[your-auth-token]</code> with your personal API access token. <br>
Token gets expired in 24hrs, and you need to login again after that to issue a new token.
</aside>
