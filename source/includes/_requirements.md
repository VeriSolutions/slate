# Requirements

> On each request, send the Basic Auth credentials and correct MIME type:

```shell
# Generate the token
echo -n <your email>:<your password> | base64

# Structure of API requests
curl "api_endpoint_here"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

> For your convenience, we have created a Sanity Check endpoint to help troubleshoot basic requests. Use this to confirm your Authorization and Content-Type headers are valid.

```shell
curl "https://cloud.verisolutions.co/api/v7/sanity-check"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

Authentication is done via Basic Auth, where `username` is your email address and `password` is your password. Basic Auth credentials must be sent on each request.

<aside class="notice">
Replace <code>&lt;username&gt;</code> and <code>&lt;password&gt;</code> with your email address and password, respectively.
</aside>

