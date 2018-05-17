# Hubs

## Hubs - Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/hubs"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Hubs that you have access to.

### Filtering

Almost all attributes are filterable. The following contains special-case information. Refer to the Filtering section for definitions and examples.

Parameter | Type | Details
--------- | ---- | -----------
`battery` | Number Range
`current_battery_reading` | Number Range
`last_online` | Time Range
`previous_battery_reading` | Number Range
`rssi` | Number Range

## Hubs - Create

```shell
curl --request POST \
  --url https://cloud.verisolutions.co/api/v7/hubs \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"hubs","attributes":{"name":"<name>","unit-id":<unit-id>}}}'
```

### Validations

Parameter | Rule
--------- | ----
`name` | Cannot be blank
`unit-id` | Must be an integer

<aside class="warning">
This functionality is only for Admins.
</aside>

## Hubs - Update

```shell
curl --request PATCH \
  --url http://localhost:9292/api/v7/hubs/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"hubs","id":"<id>","attributes":{"name":"<name>"}}}'
```

### Validations

Parameter | Rule
--------- | ----
`name` | Cannot be blank
`unit-id` | If provided, must be an integer

<aside class="warning">
This functionality is only for Admins.
</aside>

## Hubs - Destroy

```shell
curl --request DELETE \
  --url http://localhost:9292/api/v7/hubs/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
```

<aside class="warning">
This functionality is only for Admins.
</aside>
