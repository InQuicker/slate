## Medical Groups

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/medical_groups"
  -H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "family-health-group-1",
    "type": "medical-groups",
    "attributes": {
      "name": "Family Health Group 1"
    }
  }
]
```

### GET /medical_groups

Retrieve all medical groups for a given Health System.

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/medical_groups/family-health-group-1"
-H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
```

> The above command returns JSON structured like this:

```json
{
  "id": "family-health-group-1",
  "type": "medical-groups",
  "attributes": {
    "name": "Family Health Group 1"
  }
}
```

### GET /medical_groups/{id}

Retrieve a specific medical_group.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
id | true | null | The unique identifier for the medical group to retrieve.
