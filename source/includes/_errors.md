# Errors

The InQuicker API V3 uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The resource requested is hidden for administrators only.
404 | Not Found -- The specified resource could not be found.
422 | Unprocessable Entity -- The content type and syntax of the request are correct but still unable to process the contained instructions. Check the response for a detailed message.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
