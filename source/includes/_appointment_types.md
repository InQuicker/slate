# Appointment Types

## Get All Appointment Types

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.appointment_types.get
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.appointment_types.get()
```

```shell
curl "http://example.com/api/v3/{hostname}/appointment_types"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let appointment_types = api.appointment_types.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "checkup",
    "type": "appointment_types",
    "attributes": {
      "name": "Checkup",
      "priority": 10
    }
  }
]
```

This endpoint retrieves all appointment types for a given Partner.

### HTTP Request

`GET http://example.com/api/v3/{hostname}/appointment_types`

### Query Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all appointment types for that subdomain.

## Get a Specific Appointment Type

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.appointment_types.get(2)
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.appointment_types.get(2)
```

```shell
curl "http://example.com/api/v3/{hostname}/appointment_types/{appointment_type_id}"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let max = api.appointment_types.get('checkup');
```

> The above command returns JSON structured like this:

```json
{
  "id": "checkup",
  "type": "appointment_types",
  "attributes": {
    "name": "Checkup",
    "priority": 10
  }
}
```

This endpoint retrieves a specific appointment type. This call is useful for getting certain attributes associated with a appointment type (for example, if a provider only sees patients younger than 18, or the service associated with the appointment type).

### HTTP Request

`GET http://example.com/api/v3/{hostname}/appointment_types/{appointment_type_id}`

### URL Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all appointment types for that subdomain.
appointment_type_id | true | nil | The unique identifier for the appointment type to retrieve.
