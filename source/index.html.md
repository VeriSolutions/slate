---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://verisolutions.co/'>Sign Up for an Account</a>
  - <a href='mailto:developer@verisolutions.co'>Contact VS Developers</a>

includes: # adds different pages to the toc; found in ./source/includes
  - errors

search: true
---

# Introduction

Welcome to the VeriSolutions' API! VeriSolutions (VS) provides hardware and software for managing temperature and operational tasks.

The VS API is a [JSONAPI standards](http://jsonapi.org/) compliant API which aims to make this data available to anyone who has a user account.

Code examples can be found in the dark section on the right.

# Requirements

> On each request, send the Basic Auth credentials and correct MIME type:

```shell
# Generate the token
echo -n <your email>:<your password> | base64

# Structure of API requests
curl "api_endpoint_here"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

Authentication is done via Basic Auth, where `username` is your email address and `password` is your password. Basic Auth credentials must be sent on each request.

<aside class="notice">
Replace <code>&lt;username&gt;</code> and <code>&lt;password&gt;</code> with your email address and password, respectively.
</aside>

# Filtering

> Example of filtering Accounts to just show the ones with IDs of 5 and 8

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/accounts"
  -d "filter[id]=5,8"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

All data attributes returned can be used as a filter. The example to the right shows filtering Accounts to just show two specific ones (the Account with ID of 5 and the Account with ID of 8).

### Common Options

Parameter | Default | Description
--------- | ------- | -----------
`filter[created-at-max]` | (null) | Returns results that have a `created_at` value less than the time given. The time must be in ISO8601 format.
`filter[created-at-min]` | (null) | Returns results that have a `created_at` value greater than the time given. The time must be in ISO8601 format.
`filter[id]=<ids>` | (null) | Takes a comma-separated list of ids (such as `5,8`) and returns the results with those IDs.
`filter[updated-at-max]` | (null) | Returns results that have a `updated_at` value less than the time given. The time must be in ISO8601 format.
`filter[updated-at-min]` | (null) | Returns results that have a `updated_at` value greater than the time given. The time must be in ISO8601 format.
`page[number]=<number>` | 1 | Results are broken up into pages, where the first 10 (or the value of `page[size]`) are on page 1 and 11 through 20 are on page 2.
`page[size]=<size>` | 10 | Identify how many results you would like returned. Max of 50.


<aside class="notice">
If you would like more filter options, contact the developers via the link on the left.
</aside>

> If you get an error message similar to the following, please contact the VS developers

```json
{
    "errors": [
        {
            "title": "Filter not allowed",
            "detail": "name is not allowed.",
            "code": "102",
            "status": "400"
        }
    ]
}
```

### Error

If you receive an error message similar to the one on the right, contact the VS developers and we will resolve this issue within 48 hours.

# Accounts

## Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/accounts"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Accounts that you have access to.

## Create

```shell
curl --request POST \
  --url https://cloud.verisolutions.co/api/v7/accounts \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"accounts","attributes":{"name":"<name>"}}}'
```

<aside class="warning">
This functionality is only for Admins.
</aside>

### Validations

Parameter | Rule
--------- | ----
`name` | Cannot be blank

## Update

```shell
curl --request PATCH \
  --url http://localhost:9292/api/v7/accounts/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
  --data '{"data":{"type":"accounts","id":"<id>","attributes":{"name":"<name>"}}}'
```

<aside class="warning">
This functionality is only for Admins and Account Admins of that specific Account.
</aside>

### Validations

Parameter | Rule
--------- | ----
`name` | Cannot be blank

## Destroy

```shell
curl --request DELETE \
  --url http://localhost:9292/api/v7/accounts/<id> \
  --header 'Authorization: Basic <token>' \
  --header 'Content-Type: application/vnd.api+json' \
```

<aside class="warning">
This functionality is only for Admins.
</aside>

# Units

## Get All

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/units"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

This endpoint retrieves all Units that you have access to.

## Create

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
`name` | Cannot be blank
`account-id` | Must be an integer

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
`filter[show-temp]=<1 or 0>` | `1,0` | This identifies if the Cooler cares about temperature. `1` represents true and `0` represents false
`filter[show-humidity]=<1 or 0>` | `1,0` | This identifies if the Cooler cares about humidity. `1` represents true and `0` represents false
`filter[active-notifications]=<1 or 0>` | `1,0` | This identifies if a Cooler wants to be notified about temperature issues. `1` represents true and `0` represents false
`filter[humidity-notifications]=<1 or 0>` | `1,0` | This identifies if a Cooler wants to be notified about humidity issues. `1` represents true and `0` represents false

<aside class="warning">
Not every parameter of a Cooler can be filtered. If you would like to be able to filter off a parameter thas is not permitted, contact the VS developers and we will change that for you.
</aside>

# Sensor Readings

## Get All

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
