## Insurance Plans

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/insurance_plans"
  -H "Authorization: this-is-your-api-key"
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

### GET /insurance_plans

Retrieve all insurance plans for a given Partner.

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/insurance_plans/{insurance_plan_id}"
  -H "Authorization: this-is-your-api-key"
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

### GET /insurance_plans/{insurance_plan_id}`

Retrieve a specific insurance plan.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all insurance plans for that subdomain.
insurance_plan_id | true | nil | The unique identifier for the insurance plan to retrieve.
