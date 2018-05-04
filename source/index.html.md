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

The VS API is a JSON:API standards compliant API which aims to make this data available to anyone who has a user account.

Code examples can be found in the dark section on the right.

# Requirements

> On each request, send the Basic Auth credentials and correct MIME type:

```shell
curl "api_endpoint_here"
  -H "Authorization: Basic `echo -n <username>:<password> | base64`"
  -H "Content-Type: application.json"
```

Authentication is done via Basic Auth, where `username` is your email address and `password` is your password. Basic Auth credentials must be sent on each request.

<aside class="notice">
Replace <code>&lt;username&gt;</code> and <code>&lt;password&gt;</code> with your email address and password, respectively.
</aside>

Sending `-H "Content-Type: application.json"` is not required, however, it could save you hours of troubleshooting. We recommend sending it on every request.

# Accounts

## Get All Accounts

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/accounts"
  -H "Authorization: Basic `echo -n <username>:<password> | base64`"
  -H "Content-Type: application.json"
```

This endpoint retrieves all Accounts that you have access to.

# Units

## Get All Units

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/units"
  -H "Authorization: Basic `echo -n <username>:<password> | base64`"
  -H "Content-Type: application.json"
```

This endpoint retrieves all Units that you have access to.

### Query Parameters

```shell
curl -X GET "https://cloud.verisolutions.co/api/v7/units"
  -d "filter[account-id]=<id>"
  -H "Authorization: Basic `echo -n <username>:<password> | base64`"
  -H "Content-Type: application.json"
```

Parameter | Default | Description
--------- | ------- | -----------
`filter[account-id]=<id>` | null | If provided an <code>&lt;id&gt;</code>, it will only show Units that belong to that Account

<aside class="success">
If you would like more filter options, contact the developers via the link on the left.
</aside>
