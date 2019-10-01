## Insurance Plans

Insurance plans are used to determine whether a patient's health insurance is
accepted by a particular schedule.

Each plan belongs to an insurance company, and insurance companies can have many
plans. Every health system has its own unique list of insurance companies and
plans.

Each schedule, facility, region, and health system can specify which insurance
plans are accepted for a particular service. If the accepted insurance plans are
specified for a schedule, that will override the facility's accepted insurance
plans, which overrides the region's accepted insurance plans, which overrides
the health system's accepted insurance plans.

To get insurance plans available for a schedule, use the [Schedules](#schedules)
endpoint.

```shell
curl "https://api.inquicker.com/api/v3/winter-health.inquicker.com/insurance_plans"
  -H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "ultra-premium-plan",
    "type": "insurance_plans",
    "attributes": {
      "company": "My Insurance Company",
      "name": "Ultra Premium Plan"
    }
  }
]
```

### `GET /insurance_plans`

Retrieve all insurance plans associated with active schedules for a given Health
System.

```shell
curl "https://api.inquicker.com/api/v3/winter-health.inquicker.com/insurance_plans/ultra-premium-plan"
  -H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
```

> The above command returns JSON structured like this:

```json
{
  "id": "ultra-premium-plan",
  "type": "insurance_plans",
  "attributes": {
    "company": "My Insurance Company",
    "name": "Ultra Premium Plan"
  }
}
```

### `GET /insurance_plans/{id}`

Retrieve a specific insurance plan.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
id | true | null | The unique identifier for the insurance plan to retrieve.
