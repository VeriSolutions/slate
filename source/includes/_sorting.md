# Sorting

> Example of sorting Accounts to be in descending order of `created-at`

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/accounts"
  -d "sort=-name"
  -H "Authorization: Basic <token>"
  -H "Content-Type: application/vnd.api+json"
```

All attributes can be sorted.

The format for ascending is `sort=<attribute>`

The format for descending is `sort=-<attribute>` (note the `-`)
