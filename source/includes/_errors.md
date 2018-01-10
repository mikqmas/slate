# Errors

<aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside>

The Kittn API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The kitten requested is hidden for administrators only.
404 | Not Found -- The specified kitten could not be found.
405 | Method Not Allowed -- You tried to access a kitten with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The kitten requested has been removed from our servers.
418 | I'm a teapot.
429 | Too Many Requests -- You're requesting too many kittens! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

## 429 - Rate Limit 
Most services provide documentation to understand their rate limiting policies. Let’s take a closer look at an example by examining Clover rate limiting policies. You can find the most up-to-date information on Clover’s Developer Guidelines.

Clover currently has two different rate limits: per token and per app. The more restrictive of the two will apply. For reference, these are the current limits as of January 2017:

16 requests/sec per token
50 requests/sec across tokens per app
These same limits apply to all production and sandbox environments. However, other services may have different limits for different environments.

### Handling 429 response codes by exponentially backing off
If your app’s number of requests has exceeded the rate limits, you may receive a 429 Too Many Request response code. Under certain circumstances rate limits may be reduced, system-wide or for particular tokens. We advise to design your app with the necessary fallbacks to gracefully handle receiving an unexpected 429 response.

After receiving a 429 response, your app should pause for a second from sending additional requests . If you continue to receive 429 responses, your app should then exponentially increase the time between request attempts until you receive a successful response.

Note: If your app is making API requests from multiple threads, you will need to make sure all threads are backing off their requests when receiving 429 responses.
If you ignore 429 responses and continue sending requests, you risk getting your service severely interrupted.
