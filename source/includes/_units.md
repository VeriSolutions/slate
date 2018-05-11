# Units

## Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/units"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Units that you have access to.

## Create

```shell
curl --request POST \
  --url https://cloud.verisolutions.co/api/v7/units \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"units","attributes":{"name":"<name>","account-id":<account-id>}}}'
```

### Validations

Parameter | Rule
--------- | ----
`account-id` | Must be an integer
`name` | Cannot be blank

## Update

```shell
curl --request PATCH \
  --url http://localhost:9292/api/v7/units/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"units","id":"<id>","attributes":{"name":"<name>"}}}'
```

### Validations

Parameter | Rule
--------- | ----
`account-id` | Must be an integer
`name` | Cannot be blank

## Destroy

```shell
curl --request DELETE \
  --url http://localhost:9292/api/v7/units/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
```

<aside class="warning">
This functionality is only for Admins.
</aside>
