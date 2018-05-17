# Filtering

> Example of filtering Accounts to just show the ones with IDs of 5 and 8

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/accounts?filter[id]=5,8"
  --globoff
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

Almost all data attributes returned can be used as a filter. The example to the right shows filtering Accounts to just show two specific ones (the Account with ID of 5 and the Account with ID of 8).

## Background Information

Allow filterable fields follow under one of the following categories:

* Standard
* Enumerable/Boolean
* Time Range
* Number Range

### Standard

> Standard example

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/units?filter[name]=<unit 1 name>,<unit 2 name>"
  --globoff
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This is the default filter. Set the result to be an exact match. These can be comma-separated to match multiple queries.

### Enumerable/Boolean

> Enumerable example

```shell
# A User's measurement units has 0 for metric and 1 for U.S. Customary
# This would return all Users who use metric
curl -X GET "https://cloud.verisolutions.co/api/v7/users?filter[default_units]=0"
  --globoff
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

> Boolean example

```shell
# Some Coolers do not track humidity data.
# This would return all Coolers where humidity is tracked.
curl -X GET "https://cloud.verisolutions.co/api/v7/coolers?filter[humidity_notifications]=1"
  --globoff
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

For enumerables, the documentation will tell you what number coincidences with what value. For booleans, `1` is true and `0` is false.

### Time Range

> Time range example

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/sensor-readings?filter[reading-time-min]=2018-05-07T12:00:00-04:00"
  --globoff
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

If the documentation for that endpoint mentions that a field is filterable via time range, this means that two fields are available -- max and min.

Example: Sensor Readings' `reading-time` is filterable via Time Range. This means they can be filtered by `reading-time-min` and `reading-time-max`. Both of which require a time in ISO8601 format.

### Number Range

> Number range example

```shell
# This example gets all readings where the temperature was greater than the freezing temperature of water (0 Celsius, 32 Fahrenheit)
curl -X GET "https://cloud.verisolutions.co/api/v7/sensor-readings?filter[temp-min]=0"
  --globoff
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

Similar to Time Range, however the format is a number.

Example: Sensor Readings' `temp` is filterable via Number Range. This means they can be filtered by `temp-min` and `temp-max`. Both of which require a numerical format. Decimal places are with a period `.` and there is no comma-separation allowed for large numbers.

Note: All temperatures are in Celsius.

## Common Options

Parameter | Default | Description
--------- | ------- | -----------
`filter[account-id]` | (null) | Returns results under the given Account(s). Note: For the Users resource, this does not include Unit Users whose Units fall under the given Account(s).
`filter[created-at-max]` | (null) | Returns results that have a `created_at` value less than the time given. The time must be in ISO8601 format.
`filter[created-at-min]` | (null) | Returns results that have a `created_at` value greater than the time given. The time must be in ISO8601 format.
`filter[id]=<ids>` | (null) | Takes a comma-separated list of ids (such as `5,8`) and returns the results with those IDs.
`filter[search]=<term>` | (null) | Filters the results by a certain term. This is not a fuzzy search but is case insensitive
`filter[updated-at-max]` | (null) | Returns results that have a `updated_at` value less than the time given. The time must be in ISO8601 format.
`filter[updated-at-min]` | (null) | Returns results that have a `updated_at` value greater than the time given. The time must be in ISO8601 format.
`page[number]=<number>` | 1 | Results are broken up into pages, where the first 10 (or the value of `page[size]`) are on page 1 and 11 through 20 are on page 2.
`page[size]=<size>` | 10 | Identify how many results you would like returned. Max of 50.


<aside class="notice">
If you would like more filter options, contact the developers via the link on the left.
</aside>

## Errors

> If you get an error message similar to the following, please contact the VS developers

```json
{
    "errors": [
        {
            "title": "Filter not allowed",
            "detail": "<field> is not allowed.",
            "code": "102",
            "status": "400"
        }
    ]
}
```

If you receive an error message similar to the one on the right, contact the VS developers and we will resolve this issue within 48 hours.
