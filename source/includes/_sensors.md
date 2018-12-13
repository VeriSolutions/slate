# Sensors

## Sensors - Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/sensors"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Sensors that you have access to.

### Filtering

Almost all attributes are filterable. The following contains special-case information. Refer to the Filtering section for definitions and examples.

Parameter | Type | Details
--------- | ---- | -----------
`battery` | Number Range
`humidity` | Number Range
`last-online` | Time Range
`readings-count` | Number Range
`rssi` | Number Range
`successful-readings-count` | Number Range
`temp` | Number Range

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
`location-id` | If provided, must be a Cooler id or null. If provided, must set `location-type` to `"Cooler"` or `null`, respectively
`location-type` | Must be `"Cooler"` or `null`. If `"Cooler"` provided, then must set `location-id` to a Cooler id



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
