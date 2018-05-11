# Coolers

## Get All

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

Coolers have a few extra parameters they can be filtered.

Parameter | Default | Description
--------- | ------- | -----------
`filter[active-notifications]=<1 or 0>` | `1,0` | This identifies if a Cooler wants to be notified about temperature issues. `1` represents true and `0` represents false
`filter[humidity-notifications]=<1 or 0>` | `1,0` | This identifies if a Cooler wants to be notified about humidity issues. `1` represents true and `0` represents false
`filter[show-humidity]=<1 or 0>` | `1,0` | This identifies if the Cooler cares about humidity. `1` represents true and `0` represents false
`filter[show-temp]=<1 or 0>` | `1,0` | This identifies if the Cooler cares about temperature. `1` represents true and `0` represents false

<aside class="warning">
Not every parameter of a Cooler can be filtered. If you would like to be able to filter off a parameter thas is not permitted, contact the VS developers and we will change that for you.
</aside>
