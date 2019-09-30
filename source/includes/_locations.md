## Locations

Locations, also called Facilities, correspond to the physical locations where services are provided. Locations have one or more related [Schedules](#schedules).

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/locations"
  -H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
```

> The above command returns JSON structured like this:

```json
[{
  "id": "feestport",
  "type": "locations",
  "attributes": {
    "address": "101 Some Street",
    "city": "Portland",
    "facility-name": "Sample Facility 4",
    "latitude": 36.1659,
    "longitude": -86.7844,
    "name": "Feestport",
    "phone": "12223332323",
    "state": "Oregon",
    "zip": "57616"
  }
}]
```

### GET /locations

Retrieve all locations for a given Health System, and links to all related active [schedules](#schedules).

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/locations/feestport"
  -H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
```

> The above command returns JSON structured like this:

```json
{
  "id": "feestport",
  "type": "locations",
  "attributes": {
    "address": "101 Some Street",
    "city": "Portland",
    "facility-name": "Sample Facility 4",
    "latitude": 36.1659,
    "longitude": -86.7844,
    "name": "Feestport",
    "phone": "12223332323",
    "state": "Oregon",
    "zip": "57616"
  }
}
```

### GET /locations/{location_id}

Retrieve a specific location, along with links to related [schedules](#schedules).


Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
location_id | true | null | The unique identifier for the location to retrieve.

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/locations/feestport/schedules"
  -H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
```

> The above command returns JSON structured like this:

```json
...
[{
  "id": "065210e4-be1d-4862-bf1d-3dbb9f55e0de",
  "type": "schedules",
  "attributes": {
    "age-limit-direction": null,
    "age-limit-threshold": null,
    "hours": null,
    "name": null,
    "schedule-type": "online",
    "service": "Emergency Room",
    "sort-order": 9999,
    "time-zone-name": "America/New_York"
  }
}]
...
```

### GET /locations/{location_id}/schedules

Retrieve active schedules for a location. This endpoint returns links to the [provider](#providers), [service](#services), and [insurance plans](#insurance-plans) for each schedule returned.
