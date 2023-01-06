# Errors

The Pirkx API uses the following error codes:


Error Code | Meaning | Description
---------- | ------- | -----------
400 | Bad Request | Your request is invalid.
401 | Unauthorized | Your API key is wrong.
403 | Forbidden | The entity requested is hidden for administrators only.
404 | Not Found | The specified entity could not be found.
422 | Unprocessable Entity | Unable to process the contained instructions
500 | Internal Server Error | We had a problem with our server. Try again later.
