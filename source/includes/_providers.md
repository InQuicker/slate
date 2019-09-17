# Providers

## Get All Providers

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.providers.get
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.providers.get()
```

```shell
curl "http://example.com/api/v3/my-host.inquicker.com/providers"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let providers = api.providers.get();
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

This endpoint retrieves all appointment types for a given Partner.

### HTTP Request

`GET http://example.com/api/v3/{hostname}/providers`

### Query Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all providers for that subdomain.

## Get a Specific Appointment Type

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.providers.get('miss-kent-cormier')
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.providers.get('miss-kent-cormier')
```

```shell
curl "http://example.com/api/v3/my-host.inquicker.com/providers/{provider_id}"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let max = api.providers.get('miss-kent-cormier');
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

This endpoint retrieves a specific appointment type. This call is useful for getting certain attributes associated with a provider.

### HTTP Request

`GET http://example.com/api/v3/{hostname}/providers/{provider_id}`

### URL Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all providers for that subdomain.
provider_id | true | nil | The unique identifier for the provider to retrieve.
