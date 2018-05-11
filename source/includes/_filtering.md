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
