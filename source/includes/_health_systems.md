## Health Systems

Health Systems are the top level data type that connects all resources available to a partner.

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/health_systems"
  -H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "1",
    "type": "health_systems",
    "attributes": {
      "name": "Winter Health",
      "use-gtm-container": true,
      "disable-google-indexing": false,
      "gtm-container": null,
      "gtag-conversion-event-id": "1234567890",
      "gtag-id": "1123456-71"
    }
  }
]
```
### GET /health_systems

This endpoint retrieves all available health systems for a Partner.


```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/health_systems/north-dewaynechester"
  -H "Authorization: this-is-your-api-key" -H "ACCEPT: application/vnd.api+json"
```

> The above command returns JSON structured like this:

```json
{
  "id": "1",
  "type": "health_systems",
  "attributes": {
    "name": "Winter Health",
    "use-gtm-container": true,
    "disable-google-indexing": false,
    "gtm-container": null,
    "gtag-conversion-event-id": "1234567890",
    "gtag-id": "1123456-71"
  }
}
```

### GET /health_systems/{health_system_id}

This endpoint retrieves a specific health system. This call is useful for getting the Google Tag Manager settings for the health system.

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
health_system_id | true | null | The unique identifier for the health system to retrieve.
