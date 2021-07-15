---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  # - ruby
  # - python
  # - javascript

toc_footers:
  - <a href='#'>Get started with Works</a>
  - © 2021 Trusted, Inc.

includes:
  - applications
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the <strong>Trusted Works API</strong>! You can use our API to access Trusted Works API endpoints, which can get information on various Trusted entities.

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: my_api_token"
```

> Make sure to replace `my_api_token` with your API key.

Trusted Works API uses API keys to allow access to the API. You can register a new Trusted Works API key in your [Works admin page](https://app.workshealth.com/works/).

Your API keys carry many privileges, so be sure to keep them secure! Do not share your secret API keys in publicly accessible areas such as GitHub, client-side code, and so forth.

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail.

Trusted Works API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <token>`

<aside class="notice">
You must replace <code>&lsaquo;token&rsaquo;</code> with your personal API key.
</aside>

# Profile

<strong>Profiles</strong> are resources which represent a candidate in the Works platform. They can be submitted to jobs via an <a href="#applications">Application</a>.

## The Profile Resource

Attribute | Type | Description
--------- | ------- | -----------
<code>id</code> | <span class="o-60">string</span> | The unique ID for a Profile
<code>first_name</code> | <span class="o-60">string</span> | The candidate's first name
<code>last_name</code> | <span class="o-60">string</span> | The candidate's last name
<code>email</code> | <span class="o-60">string</span> | The candidate's email
<code>phone</code> | <span class="o-60">string</span> | The candidate's phone number. Must be provided in xxx-xxx-xxxx format.
<code>created_at</code> | <span class="o-60">timestamp</span> | The creation timestamp of the Profile.

## Get All Profiles

```shell
curl "https://api.workshealth.com/v1/profiles" \
  -H "Authorization: my_api_token"
```

> The above command returns JSON structured like this:

```json
[
  {
    "total_records": 149,
    "page": 1,
    "has_more": true,
    "results": [
      {
        "id": "c9ad0e93-09d4-4683-946a-a2c163cd9338",
        "first_name": "Bart",
        "last_name": "Simpson",
        "email": "bart@moes_tavern.com",
        "phone": "661-555-1234",
        "created_at": "2021-03-03T08:23:20-03:35"
      },
      {
        "id": "c9ad0e93-09d4-4683-946a-a2c163cd9338",
        "first_name": "Lisa",
        "last_name": "Simpson",
        "email": "lisa@springfield.edu",
        "phone": "661-555-1234",
        "profile_summary": "Straight A's last quarter",
        "created_at": "2021-06-03T02:08:20-07:00"
      }
    ]
  }
]
```

This endpoint retrieves all Profiles.

### HTTP Request

`GET https://api.workshealth.com/v1/profiles`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
limit <i class="o-60">(optional)</i> | 10 | A limit on the number of resources to be returned, between 1 and 100.
starting_after <i class="o-60">(optional)</i> |  | A cursor for use in pagination. <code>starting_after</code> is the Profile ID that defines your place in the list. For instance, if you make a list request and receive 100 Profiles, where the last profile has the ID of <code>m83-1234</code>, your subsequent call can include <code>starting_after=m83-1234</code> in order to fetch the next page of the list.
order <i class="o-60">(optional)</i> | created_at | A limit on the number of resources to be returned, between 1 and 100.

<aside class="notice">
The <code>has_more</code> field indicates if there are more records after the specified cursor.
</aside>

## Get a Specific Profile

```shell
curl "https://api.workshealth.com/v1/profiles/c9ad0e93-09d4-4683-946a-a2c163cd9338" \
  -H "Authorization: my_api_token"
```

> The above command returns JSON structured like this:

```json
{
  "id": "c9ad0e93-09d4-4683-946a-a2c163cd9338",
  "supplier_id": 1,
  "first_name": "Bart",
  "last_name": "Simpson",
  "email": "bart@moes_tavern.com",
  "phone": "661-555-1234",
  "created_at": "2021-03-03T08:23:20-03:35"
}
```

This endpoint retrieves a specific Profile.


### HTTP Request

`GET https://api.workshealth.com/v1/profiles/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the Profile to retrieve

