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
]
```

### GET /providers

Retrieve all providers for a given Health System.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
filter | false | null | See below.

The filter query parameter takes a JSON object with the following possible keys:

key | Default | Description
--------- | ------- | -----------
service | null | The id of the service to limit results to. For example "primary-care", or "emergency"
accepting-new-patients | null | Limit results to providers with schedules that are accepting new patients. Can be "true" or "false". If it is "true", only providers who are accepting new patients are returned. If it is "false", all matching providers are returned.
affiliation | null | Filter based on the provider's affiliation with the facility or health system. Can be either "employed" or "affiliated".
appointment-type | null | Limit results to providers who offer the given appointment type, eg. "primary-care".
gender | null | Limit results by gender. Can be either "male" or "female".
hours-availability | null | Filter results by availability. Can be either "morning", "afternoon", or "evening", where morning is 05:00-11:59, afternoon is 12:00-17:59, and evening is 18:00-23:59.
insurance | null | Filter results by insurance plan. Valid values are the id of any insurance plan returned by the `insurance_plans` endpoint, eg "ultra-premium-plan".
language | null | Limit results to providers who speak the given language.
medical-group | null | Limit results to providers in a specific medical group. Valid values are the id of any insurance plan returned by the `medical_groups` endpoint.
near | null | Orders results from nearest to farthest given geographic coordinates. Coordinates are given as an array, eg "[36.1659,-86.7844]"
provider-type | null | Limit to either practitioners or health resources. Can be either 'practitioner' or 'healthresource'.

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/providers/miss-kent-cormier"
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

Retrieve a specific provider. This call is useful for getting certain attributes associated with a provider.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
provider_id | true | null | The unique identifier for the provider to retrieve.
