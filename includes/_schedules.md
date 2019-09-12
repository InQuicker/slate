# Schedules

## Get All Schedules

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.schedules.get
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.schedules.get()
```

```shell
curl "http://example.com/api/v3/{hostname}/schedules"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let schedules = api.schedules.get();
```

> The above command returns JSON structured like this:

```json
{
  "id": "2528d709-5ab9-444e-bfec-0e1e9d4666a6",
  "type": "schedules",
  "attributes": {
    "age-limit-threshold": 18,
    "age-limit-direction": "older",
    "hours": "null",
    "name": "My Doc Schedule",
    "schedule-type": "online",
    "service": "Primary Care",
    "sort-order": 9999,
    "time-zone-name": "America/Los_Angeles"
  }
}
```

This endpoint retrieves all schedules for a given Partner.

### HTTP Request

`GET http://example.com/api/v3/{hostname}/schedules`

### Query Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all schedules for that subdomain.

## Get a Specific Schedule

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.schedules.get(2)
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.schedules.get(2)
```

```shell
curl "http://example.com/api/v3/{hostname}/schedules/{schedule_id}"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let max = api.schedules.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": "2528d709-5ab9-444e-bfec-0e1e9d4666a6",
  "type": "schedules",
  "attributes": {
    "age-limit-threshold": 18,
    "age-limit-direction": "older",
    "hours": "null",
    "name": "My Doc Schedule",
    "schedule-type": "online",
    "service": "Primary Care",
    "sort-order": 9999,
    "time-zone-name": "America/Los_Angeles"
  }
}
```

This endpoint retrieves a specific schedule. This call is useful for getting certain attributes associated with a schedule (for example, if a provider only sees patients younger than 18, or the service associated with the schedule).

### HTTP Request

`GET http://example.com/api/v3/{hostname}/schedules/{schedule_id}`

### URL Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all schedules for that subdomain.
schedule_id | true | nil | The unique identifier for the schedule to retrieve.

