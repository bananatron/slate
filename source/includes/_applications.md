
# Applications

<strong>Applications</strong> are resources which represent a candidate submission to a specific position. A candidate <a href="#profile">Profile</a> must exist in order to create an Application.

## The Application Resource

Attribute | Type | Description
--------- | ------- | -----------
<code>id</code> | <span class="o-60">string</span> | The unique ID for an Application
<code>works_profile_id</code> | <span class="o-60">string</span> | The unique ID for the associated WorksProfile
<code>state</code> | <span class="o-60">string</span> | The current <i>state</i> of the Application. Can be one of: <code>submitted</code>, <code>in_review</code>, <code>offer</code>, <code>accepted</code>, <code>rejected</code>, <code>withdrawn</code>
<code>rejection_reason</code> | <span class="o-60">string</span> | The rejection reason for a rejected Application.
<code>rejection_reason_description</code> | <span class="o-60">string</span> | A humanized rejection reason for a rejected Application.
<code>notes</code> | <span class="o-60">string</span> | The notes left by the <span class="red">hiring partner</span> for an Application.
<code>timeoff_availability</code> | <span class="o-60">string</span> | The request for time off from the candidate.
<code>interview_availability</code> | <span class="o-60">string</span> | Notes on the availability for a candidate interview.
<code>available_to_start_at</code> | <span class="o-60">timestamp</span> | The first available start date for a candidate.
<code>state_changed_at</code> | <span class="o-60">timestamp</span> | The timestamp of the last occurance of a state change on the Application.
<code>created_at</code> | <span class="o-60">timestamp</span> | The creation timestamp of the Application.

## Get All Applications

```shell
curl "https://api.workshealth.com/v1/applications" \
  -H "Authorization: my_api_token"
```

> The above command returns JSON structured like this:

```json
[
  {
    "total_records": 2,
    "page": 1,
    "has_more": false,
    "results": [
      {
        "id": "cd169aff-1379-42d4-bf06-ccf3ff31cbde",
        "works_profile_id": "c9ad0e93-09d4-4683-946a-a2c163cd9338",
        "state": "accepted",
        "rejection_reason": null,
        "notes": "A nice note from your hiring partner",
        "timeoff_description": "A few days",
        "interview_availability": "Flexible",
        "available_to_start_at": "2021-03-03",
        "state_changed_at": "2021-03-03T08:23:20-03:35",
        "created_at": "2021-03-03T08:23:20-03:35"
      },
      {
        "id": "0372bc25-6a6e-4f0f-80f8-8c38ed641830",
        "works_profile_id": "c9ad0e93-09d4-4683-946a-a2c163cd9338",
        "state": "rejected",
        "rejection_reason": "license_certification_requirements",
        "rejection_reason_description": "License/certifications requirements not met",
        "notes": null,
        "timeoff_description": "None requesteed",
        "interview_availability": "Tuesday afternoons",
        "available_to_start_at": "2021-03-06",
        "state_changed_at": "2021-06-03T08:23:20-03:35",
        "created_at": "2021-03-03T08:23:20-03:35"
      }
    ]
  }
]
```

This endpoint retrieves all WorksProfiles.

### HTTP Request

`GET https://api.workshealth.com/v1/applications`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
limit <i class="o-60">(optional)</i> | 10 | A limit on the number of resources to be returned, between 1 and 100.
starting_after <i class="o-60">(optional)</i> |  | A cursor for use in pagination. <code>starting_after</code> is the WorksProfile ID that defines your place in the list. For instance, if you make a list request and receive 100 WorksProfiles, where the last profile has the ID of <code>m83-1234</code>, your subsequent call can include <code>starting_after=m83-1234</code> in order to fetch the next page of the list.
order <i class="o-60">(optional)</i> | created_at | A limit on the number of resources to be returned, between 1 and 100.

<aside class="notice">
The <code>has_more</code> field indicates if there are more records after the specified cursor.
</aside>

## Get a Specific Application

```shell
curl "https://api.workshealth.com/v1/applications/cd169aff-1379-42d4-bf06-ccf3ff31cbde" \
  -H "Authorization: my_api_token"
```

> The above command returns JSON structured like this:

```json
{
  "id": "cd169aff-1379-42d4-bf06-ccf3ff31cbde",
  "works_profile_id": "c9ad0e93-09d4-4683-946a-a2c163cd9338",
  "state": "accepted",
  "rejection_reason": null,
  "notes": "A nice note from your hiring partner",
  "timeoff_description": "A few days",
  "interview_availability": "Flexible",
  "available_to_start_at": "2021-03-03",
  "state_changed_at": "2021-03-03T08:23:20-03:35",
  "created_at": "2021-03-03T08:23:20-03:35",
}
```

This endpoint retrieves a specific Application.


### HTTP Request

`GET https://api.workshealth.com/v1/applications/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the WorksProfile to retrieve

