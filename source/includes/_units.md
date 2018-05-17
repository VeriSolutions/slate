# Units

## Units - Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/units"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Units that you have access to.

### Filtering

Almost all attributes are filterable. The following contains special-case information. Refer to the Filtering section for definitions and examples.

Parameter | Type | Details
--------- | ---- | -----------
`compliant-temps-count` | Number Range
`default-units` | Enumerable | `0` is for `"metric"`, `1` is for `"english"` aka U.S. Customary
`humidity-notify-threshold` | Number Range
`humidity-recurring-notify-duration` | Number Range
`notify-threshold` | Number Range
`recurring-notify-duration` | Number Range
`temps-count` | Number Range
`unit-status` | Enumerable | `0` is for `"active"`, `1` is for `"inactive"`

## Units - Create

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

## Units - Update

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

## Units - Destroy

```shell
curl --request DELETE \
  --url http://localhost:9292/api/v7/units/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
```

<aside class="warning">
This functionality is only for Admins.
</aside>
