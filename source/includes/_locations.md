## Locations

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/locations"
  -H "Authorization: this-is-your-api-key"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "north-dewaynechester",
    "type": "locations",
    "attributes": {
      "address": "101 Some Street",
      "city": "Portland",
      "facility-name": "Sample Facility 2",
      "latitude": 36.1659,
      "longitude": -86.7844,
      "name": "North Dewaynechester",
      "phone": "12223332323",
      "state": "Oregon",
      "zip": "47495"
    }
  }
]
```

### GET /locations

Retrieve all locations for a given Health System.

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/locations/feestport"
  -H "Authorization: this-is-your-api-key"
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

Retrieve a specific location.


Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
location_id | true | null | The unique identifier for the location to retrieve.
