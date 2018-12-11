# Notification Settings

## Notification Settings - Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/notification-settings"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Notification Settings that you have access to.

### Filtering

Almost all attributes are filterable. The following contains special-case information. Refer to the Filtering section for definitions and examples.

Parameter | Type | Details
--------- | ---- | -----------
`cooler_id` | Number Integer
`out_of_range_threshold` | Number Range
`recurring_notify_duration` | Number Range
`last_threshold_sent` | Time Range
`last_humidity_threshold_sent` | Time Range
