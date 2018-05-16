# Sensors

## Sensors - Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/sensors"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Sensors that you have access to.

## Sensors - Create

```shell
curl --request POST \
  --url https://cloud.verisolutions.co/api/v7/sensors \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"sensors","attributes":{"name":"<name>","unit-id":<unit-id>}}}'
```

### Validations

Parameter | Rule
--------- | ----
`unit-id` | Must be an integer

<aside class="warning">
This functionality is only for Admins.
</aside>

## Sensors - Update

```shell
curl --request PATCH \
  --url http://localhost:9292/api/v7/sensors/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"sensors","id":"<id>","attributes":{"name":"<name>"}}}'
```

### Validations

Parameter | Rule
--------- | ----
`unit-id` | If provided, must be an integer

## Sensors - Destroy

```shell
curl --request DELETE \
  --url http://localhost:9292/api/v7/sensors/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
```

### Validations

Cannot destroy Sensors that have `hardware-status: 'active'`. Change this before destorying.

<aside class="warning">
This functionality is only for Admins.
</aside>
