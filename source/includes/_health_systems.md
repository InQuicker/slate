## Health Systems

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/health_systems"
  -H "Authorization: this-is-your-api-key"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "north-dewaynechester",
    "type": "health_systems",
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
### GET /health_systems

This endpoint retrieves all health systems for a given Partner.


```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/health_systems/{health_system_id}"
  -H "Authorization: this-is-your-api-key"
```

> The above command returns JSON structured like this:

```json
{
  "id": "feestport",
  "type": "health_systems",
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

### GET /health_systems/{health_system_id}

This endpoint retrieves a specific health system. This call is useful for getting certain attributes associated with a health system (for example, if a provider only sees patients younger than 18, or the service associated with the health system).

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
health_system_id | true | nil | The unique identifier for the health system to retrieve.
