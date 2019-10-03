## Services

```shell
curl "https://api.inquicker.com/api/v3/winter-health.inquicker.com/services"
  -H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "family-medicine",
    "type": "services",
    "attributes": {
      "name": "Family Medicine"
    }
  }
]
```

### `GET /services`

Retrieve all services for a given Health System.

```shell
curl "https://api.inquicker.com/api/v3/winter-health.inquicker.com/services/family-medicine"
-H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
```

> The above command returns JSON structured like this:

```json
{
  "id": "family-medicine",
  "type": "services",
  "attributes": {
    "name": "Family Medicine"
  }
}
```

### `GET /services/{id}`

Retrieve a specific service.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
id | true | null | The unique identifier for the service to retrieve.
