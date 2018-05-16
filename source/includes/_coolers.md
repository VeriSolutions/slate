# Coolers

## Coolers - Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/coolers"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Coolers that you have access to.

### Filtering

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/coolers"
  -d "filter[show-temp]=1"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

Coolers have a few extra parameters that can be filtered.

Parameter | Default | Description
--------- | ------- | -----------
`filter[active-notifications]=<1 or 0>` | `1,0` | This identifies if a Cooler wants to be notified about temperature issues. `1` represents true and `0` represents false
`filter[humidity-notifications]=<1 or 0>` | `1,0` | This identifies if a Cooler wants to be notified about humidity issues. `1` represents true and `0` represents false
`filter[show-humidity]=<1 or 0>` | `1,0` | This identifies if the Cooler cares about humidity. `1` represents true and `0` represents false
`filter[show-temp]=<1 or 0>` | `1,0` | This identifies if the Cooler cares about temperature. `1` represents true and `0` represents false

<aside class="warning">
Not every parameter of a Cooler can be filtered. If you would like to be able to filter off a parameter thas is not permitted, contact the VS developers and we will change that for you.
</aside>

## Coolers - Create

```shell
curl --request POST \
  --url https://cloud.verisolutions.co/api/v7/coolers \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"coolers","attributes":{"name":"<name>","unit-id":<unit-id>}}}'
```

### Validations

Parameter | Rule
--------- | ----
`name` | Cannot be blank
`unit-id` | Must be an integer

<aside class="warning">
This functionality is only for Admins.
</aside>

## Coolers - Update

```shell
curl --request PATCH \
  --url http://localhost:9292/api/v7/coolers/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"coolers","id":"<id>","attributes":{"name":"<name>"}}}'
```

### Validations

Parameter | Rule
--------- | ----
`name` | Cannot be blank
`unit-id` | If provided, must be an integer

## Coolers - Destroy

```shell
curl --request DELETE \
  --url http://localhost:9292/api/v7/coolers/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
```

<aside class="warning">
This functionality is only for Admins.
</aside>
