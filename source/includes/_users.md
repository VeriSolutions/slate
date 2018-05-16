# Users

## Users - Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/users"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Users that you have access to.

## Users - Create

```shell
# Admin
curl --request POST \
  --url https://cloud.verisolutions.co/api/v7/admins \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"admins","attributes":{"email":"<email>","account-id":<account-id>}}}'

# Account Admin
curl --request POST \
  --url https://cloud.verisolutions.co/api/v7/account-users \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"account-users","attributes":{"email":"<email>","account-id":<account-id>,"account-admin":true}}}'

# Account User
curl --request POST \
  --url https://cloud.verisolutions.co/api/v7/account-users \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"account-users","attributes":{"email":"<email>","account-id":<account-id>,"unit-ids":[<unit ids>]}}}'

# Unit User
curl --request POST \
  --url https://cloud.verisolutions.co/api/v7/unit-users \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"unit-users","attributes":{"email":"<email>","unit-id":<unit-id>}}}'
```

There are three different endpoints, depending on the user type being created.

<aside class="notice">
Each of these endpoints has different authorization rules. If you believe you should be authorized but receive a 403 error, contact the VS developers.
</aside>

### Validations

Parameter | Rule
--------- | ----
`account-id` | Must be an integer. Required for Account Admins and Account Users.
`email` | Must be a valid email address.
`unit-id` | Integer. Required for Unit Users.
`unit-ids` | An array of integers. Required for Account Users.

## Users - Update

```shell
curl --request PATCH \
  --url http://localhost:9292/api/v7/users/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"users","id":"<id>","attributes":{"email":"<email>"}}}'
```

Updates are done on the generic `users` route.

### Validations

Parameter | Rule
--------- | ----
`account-id` | Must be an integer. Required for Account Admins and Account Users.
`email` | Must be a valid email address.
`unit-id` | Integer. Required for Unit Users.
`unit-ids` | An array of integers. Required for Account Users. Note: This will overwrite all existing records. Every time this is called, all applicable Unit IDs must be included.

## Users - Destroy

```shell
curl --request DELETE \
  --url http://localhost:9292/api/v7/users/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
```
