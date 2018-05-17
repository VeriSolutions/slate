# Accounts

## Accounts - Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/accounts"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Accounts that you have access to.

### Filtering

Almost all attributes are filterable. The following contains special-case information. Refer to the Filtering section for definitions and examples.

Parameter | Type | Details
--------- | ---- | -----------
`account-type` | Enumerable | `0` is for `"customers"`, `1` is for `"pilot"`, `2` is for `"partner"`, `3` is for `"test"`
`confirmed-at` | Time Range

## Accounts - Create

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

## Accounts - Update

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

## Accounts - Destroy

```shell
curl --request DELETE \
  --url http://localhost:9292/api/v7/accounts/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
```

<aside class="warning">
This functionality is only for Admins.
</aside>
