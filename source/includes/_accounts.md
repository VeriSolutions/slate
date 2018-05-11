# Accounts

## Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/accounts"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Accounts that you have access to.

## Create

```shell
curl --request POST \
  --url https://cloud.verisolutions.co/api/v7/accounts \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"accounts","attributes":{"name":"<name>"}}}'
```

<aside class="warning">
This functionality is only for Admins.
</aside>

### Validations

Parameter | Rule
--------- | ----
`name` | Cannot be blank

## Update

```shell
curl --request PATCH \
  --url http://localhost:9292/api/v7/accounts/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"accounts","id":"<id>","attributes":{"name":"<name>"}}}'
```

<aside class="warning">
This functionality is only for Admins and Account Admins of that specific Account.
</aside>

### Validations

Parameter | Rule
--------- | ----
`name` | Cannot be blank

## Destroy

```shell
curl --request DELETE \
  --url http://localhost:9292/api/v7/accounts/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
```

<aside class="warning">
This functionality is only for Admins.
</aside>
