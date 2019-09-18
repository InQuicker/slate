## Providers

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/providers"
  -H "Authorization: this-is-your-api-key"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "checkup",
    "type": "providers",
    "attributes": {
      "name": "Checkup",
      "priority": 10
    }
  }
]
```

### GET /providers

Retrieve all appointment types for a given Partner.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all providers for that subdomain.

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/providers/{provider_id}"
  -H "Authorization: this-is-your-api-key"
```

> The above command returns JSON structured like this:

```json
{
  "id": "miss-kent-cormier",
  "type": "providers",
  "attributes": {
    "affiliation": "employed",
    "appointment-types": [{ "id": "new-patient-4", "name": "New Patient 4" }],
    "backgrounds": [],
    "bio": null,
    "card-image": null,
    "credentials": null,
    "gender": "m",
    "grad-school": null,
    "medical-groups": [],
    "name": "Miss Kent Cormier",
    "profile-image": null,
    "provider-type": "Practitioner",
    "subspecialties": [],
    "suffix": "MD",
    "undergrad-school": null
  }
}
```

### GET /providers/{provider_id}

Retrieve a specific appointment type. This call is useful for getting certain attributes associated with a provider.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all providers for that subdomain.
provider_id | true | nil | The unique identifier for the provider to retrieve.
