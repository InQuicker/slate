## Appointment Types

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/appointment_types"
  -H "Authorization: this-is-your-api-key"
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

### GET /appointment_types

Retrieve all appointment types for a given Partner.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
filter | false | nil | See below.

The `filter` query parameter takes a JSON object with the following possible keys:

key | Default | Description
--------- | ------- | -----------
context | nil | The Schedule Context to limit results from. Can be either "Patient", "Discharge", or "Internal"
service | nil | The name of the Service to limit results from, for example, "Primary Care".

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/appointment_types/checkup"
  -H "Authorization: this-is-your-api-key"
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

### GET /appointment_types/{appointment_type_id}

Retrieve a specific appointment type. The priority of an appointment type determines which appointment type is selected by default for new visits and provider links, with 1 being the highest priority, and 10 being the lowest.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
appointment_type_id | true | nil | The unique identifier for the appointment type to retrieve.
