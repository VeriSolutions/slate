# Errors

The VS API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- You have failed to provide valid credentials.
403 | Forbidden -- The requested resource is forbidden from access.
404 | Not Found -- The requested resource cannot be found.
405 | Method Not Allowed -- You tried to access a resource with an invalid method.
406 | Not Acceptable -- You requested a format that isn't JSON. Refer to the Requirements section.
415 | Unsupported Media Type -- Make sure to add the correct Content-Type header. Refer to the Requirements section.
422 | Unprocessable Entity -- Your request was in the correct format and syntax, however could not be processed. This is most likely due to validation errors.
429 | Too Many Requests -- The rate of that you're sending requests exceeds our API limits. Throttle the request volume.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
