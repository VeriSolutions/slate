# Sensor Readings

## Sensor Readings - Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/sensor-readings"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Sensor Readings that you have access to.

### Filtering

Almost all attributes are filterable. The following contains special-case information. Refer to the Filtering section for definitions and examples.

Parameter | Type | Details
--------- | ---- | -----------
`battery` | Number Range
`humidity` | Number Range
`reading-time` | Time Range
`rolling-humidity` | Number Range
`rssi` | Number Range
`temp` | Number Range
