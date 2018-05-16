# Sensor Readings

## Sensor Readings - Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/sensor-readings"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

### Filtering

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/sensor-readings"
  -d "filter[reading-time-min]=2018-05-07T12:00:00-04:00"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

Parameter | Default | Description
--------- | ------- | -----------
`filter[reading-time-max]` | (null) | Returns results that have a `reading_time` value less than the time given. The time must be in ISO8601 format.
`filter[reading-time-min]` | (null) | Returns results that have a `reading_time` value greater than the time given. The time must be in ISO8601 format.

This endpoint retrieves all Sensor Readings that you have access to.
