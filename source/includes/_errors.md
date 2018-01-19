# Errors

These are some of the general error codes you may encounter.

Error Code | Meaning
---------- | -------
401 | Unauthorized -- You are not allowed to access the resource or Invalid credentials.
404 | Not Found -- The specified resource could not be found.
422 | Unprocessable Entity -- May be Missing token or Invalid Parameters
500 | Internal Server Error -- We had a problem with our server. Try again later.

All these will return a json response with a message attribute, indicating why the error occurred.

