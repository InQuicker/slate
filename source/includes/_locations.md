# Locations

## Get All Locations

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.locations.get
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.locations.get()
```

```shell
curl "http://example.com/api/v3/my-host.inquicker.com/locations"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let locations = api.locations.get();
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

This endpoint retrieves all locations for a given Partner.

### HTTP Request

`GET http://example.com/api/v3/{hostname}/locations`

### Query Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all locations for that subdomain.

## Get a Specific Location

```ruby
require 'inquicker'

api = InQuicker::APIClient.authorize!('this-is-your-api-key')
api.locations.get('feestport')
```

```python
import inquicker

api = inquicker.authorize('this-is-your-api-key')
api.locations.get('feestport')
```

```shell
curl "http://example.com/api/v3/my-host.inquicker.com/locations/feestport"
  -H "Authorization: this-is-your-api-key"
```

```javascript
const inquicker = require('inquicker');

let api = inquicker.authorize('this-is-your-api-key');
let max = api.locations.get('feestport');
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

This endpoint retrieves a specific location.

### HTTP Request

`GET http://example.com/api/v3/{hostname}/locations/{location_id}`

### URL Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
hostname | true | nil | The hostname of the Partner aka. the InQuicker subdomain. Required to fetch all locations for that subdomain.
location_id | true | nil | The unique identifier for the location to retrieve.
