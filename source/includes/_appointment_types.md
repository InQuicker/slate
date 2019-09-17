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
curl "http://example.com/api/v3/my-host.inquicker.com/appointment_types"
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
filter | false | nil | See [Filter parameters](#filter-parameters).

### Filter Parameters

The filter query parameter takes a JSON object with the following possible keys:

key | Default | Description
--------- | ------- | -----------
context | nil | The Schedule Context to limit results from. Can be either "Patient", "Discharge", or "Internal"
service | nil | The name of the Service to limit results from, for example, "Primary Care".

## Get a Specific Appointment Type

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.appointment_types.get('checkup')
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.appointment_types.get('checkup')
```

```shell
curl "http://example.com/api/v3/my-host.inquicker.com/appointment_types/checkup"
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

This endpoint retrieves a specific appointment type. The priority of an appointment type determines which appointment type is selected by default for new visits and provider links, with 1 being the highest priority, and 10 being the lowest.

### HTTP Request

`GET http://example.com/api/v3/{hostname}/appointment_types/{appointment_type_id}`

### URL Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all appointment types for that subdomain.
appointment_type_id | true | nil | The unique identifier for the appointment type to retrieve.
