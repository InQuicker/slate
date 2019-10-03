## Schedules

Schedules can be queried from the `/schedules` endpoint, or from the
[`locations`](#locations) endpoint for schedules at a specific location.

```shell
curl "https://api.inquicker.com/api/v3/winter-health.inquicker.com/schedules"
  -H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
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

### `GET /schedules`

Retrieve all schedules for a given Health System.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
filter | false | null | See below.

The filter query parameter takes a JSON object with the following possible keys:

key | Default | Description
--------- | ------- | -----------
provider_type | null | The Provider Type to limit results to. Can be either "practitioner", or "healthresource"

```shell
curl "https://api.inquicker.com/api/v3/winter-health.inquicker.com/schedules/2528d709-5ab9-444e-bfec-0e1e9d4666a6"
  -H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
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

### `GET /schedules/{schedule_id}`

Retrieve a specific schedule. This call is useful for getting certain attributes
associated with a schedule (for example, if a provider only sees patients
younger than 18, or the service associated with the schedule).

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
schedule_id | true | null | The unique identifier for the schedule to retrieve.

### `GET /schedules/{schedule_id}/location`

Retrieve the related location for a schedule. The result is the same format as
the [`GET /locations/{location_id}`](#get-locations-location_id) call.

### `GET /schedules/{schedule_id}/provider`

Retrieve the related provider for a schedule. The result is the same format as
the [`GET /providers/{provider_id}`](#get-providers-provider_id) call.

### `GET /schedules/{schedule_id}/service`

Retrieve the related service for a schedule. The result is the same format as
the [`GET /services/{service_id}`](#get-services-service_id) call.

### `GET /schedules/{schedule_id}/insurance-plans`

Retrieve the related insurance plans for a schedule. The result is the same
format as the [`GET /insurance-plans`](#get-insurance-plans) call.
