# Errors

The Whole Surplus API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The server understood the request but refuses to authorize it.
404 | Not Found -- The specified page could not be found.
405 | Method Not Allowed -- The method received in the request-line is known by the origin server but not supported by the target resource.
406 | Not Acceptable -- You requested a format that is not JSON.
429 | Too Many Requests -- You're sending too many requests! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
