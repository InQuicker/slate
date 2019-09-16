# Health Systems

## Get All Health Systems

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.health_systems.get
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.health_systems.get()
```

```shell
curl "http://example.com/api/v3/{hostname}/health_systems"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let health_systems = api.health_systems.get();
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

This endpoint retrieves all health systems for a given Partner.

### HTTP Request

`GET http://example.com/api/v3/{hostname}/health_systems`

### Query Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all health_systems for that subdomain.

## Get a Specific Health System

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.health_systems.get(2)
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.health_systems.get(2)
```

```shell
curl "http://example.com/api/v3/{hostname}/health_systems/{health_system_id}"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let max = api.health_systems.get('feestport');
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

This endpoint retrieves a specific health system. This call is useful for getting certain attributes associated with a health system (for example, if a provider only sees patients younger than 18, or the service associated with the health system).

### HTTP Request

`GET http://example.com/api/v3/{hostname}/health_systems/{health_system_id}`

### URL Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all health systems for that subdomain.
health_system_id | true | nil | The unique identifier for the health system to retrieve.
