# Insurance Plans

## Get All Insurance Plans

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.insurance_plans.get
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.insurance_plans.get()
```

```shell
curl "http://example.com/api/v3/{hostname}/insurance_plans"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let insurance_plans = api.insurance_plans.get();
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

This endpoint retrieves all insurance plans for a given Partner.

### HTTP Request

`GET http://example.com/api/v3/{hostname}/insurance_plans`

### Query Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all insurance plans for that subdomain.

## Get a Specific Insurance Plan

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.insurance_plans.get('checkup')
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.insurance_plans.get(2)
```

```shell
curl "http://example.com/api/v3/{hostname}/insurance_plans/{insurance_plan_id}"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let max = api.insurance_plans.get(2);
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

This endpoint retrieves a specific insurance plan.

### HTTP Request

`GET http://example.com/api/v3/{hostname}/insurance_plans/{insurance_plan_id}`

### URL Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all insurance plans for that subdomain.
insurance_plan_id | true | nil | The unique identifier for the insurance plan to retrieve.
