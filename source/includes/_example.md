# Example

In this example, we will use the InQuicker APIv3 to fetch data and book an appointment. We will be using curl to illustrate the most basic use of the APIv3, but a typical integration will use a higher-level client library.

The examples use a dummy api key that you will have to replace with the api key of a Health System that you have console access to. The base API URL uses the sample Winter Health Health System. Replace this with the URL for your Health System, which can be found in the InQuicker console.

## Booking a visit

We will be booking an annual physical for an imaginary patient that has health insurance and uses the 'Feestport' location. These are the steps that we will be using:

- Get Insurance Plans
- Get the 'Annual Physical' Appointment Type record
- Get schedules for the location and include insurance plans
- Get available appointment times in those schedules
- Book the appointment

```shell
curl "https://api.inquicker.com/v3/winter-health.inquicker.com/insurance-plans" -G -H "Authorization: your-api-key" -H "ACCEPT: application/vnd.api+json"
```

```json
{
  "data": [{
    "id": "aarp-ppo-12",
    "type": "insurance-plans",
    "links": {
      "self": "https://api.inquicker.com/v3/winter-health.inquicker.com/insurance-plans/aarp-ppo-12"
    },
    "attributes": {
      "company": "AARP",
      "name": "AARP PPO"
    }
  }, {
    "id": "aetna-2",
    "type": "insurance-plans",
    "links": {
      "self": "https://api.inquicker.com/v3/winter-health.inquicker.com/insurance-plans/aetna-2"
    },
    "attributes": {
      "company": "Aetna",
      "name": "Aetna"
    }
  }],
  "meta": {
    "record-count": 2
  }
}
```

### Get Insurance Plans

We use the `GET /insurance-plans` endpoint to fetch insurance plans in order to get the id of the insurance plan that the patient uses.

This returns a list of all insurance plans in the health system.

<div style="clear:right"></div>

```shell
curl "https://api.inquicker.com/v3/winter-health.inquicker.com/appointment-types" -H "Authorization: your-api-key" -H "ACCEPT: application/vnd.api+json"
```

```json
{
  "data": [{
    "id": "new-patient-3",
    "type": "appointment-types",
    "links": {
      "self": "https://api.inquicker.com/v3/winter-health.inquicker.com/appointment-types/new-patient-3"
    },
    "attributes": {
      "name": "New Patient",
      "priority": 5
    }
  }, {
    "id": "annual-physical",
    "type": "appointment-types",
    "links": {
      "self": "https://api.inquicker.com/v3/winter-health.inquicker.com/appointment-types/annual-physical"
    },
    "attributes": {
      "name": "Annual Physical",
      "priority": 10
    }
  }],
  "meta": {
    "record-count": 2
  },
  "links": {
    "first": "https://api.inquicker.com/v3/winter-health.inquicker.com/appointment-types?page%5Bnumber%5D=1&page%5Bsize%5D=10",
    "last": "https://api.inquicker.com/v3/winter-health.inquicker.com/appointment-types?page%5Bnumber%5D=1&page%5Bsize%5D=10"
  }
}
```

### Get the 'Annual Physical' Appointment Type

We will be filtering schedules and availability by appointment type, so we use the `GET /appointment-types` endpoint to fetch appointment types to get the id for the 'Annual Physical' appointment type.

<div style="clear:right"></div>

```shell
curl "https://api.inquicker.com/v3/winter-health.inquicker.com/locations/cartersville/schedules" -G -H "Authorization: your-api-key" -H "ACCEPT: application/vnd.api+json" --data-urlencode 'include=insurance-plans'
```

```json
{
  "data": [{
    "id": "7b91ec6d-3d24-4478-97fc-fc4490e49b8d",
    "type": "schedules",
    "links": {
      "self": "https://api.inquicker.com/v3/winter-health.inquicker.com/schedules/7b91ec6d-3d24-4478-97fc-fc4490e49b8d"
    },
    "attributes": {
      "age-limit-direction": null,
      "age-limit-threshold": null,
      "hours": null,
      "name": "",
      "schedule-type": "online",
      "service": "Primary Care",
      "sort-order": 9999,
      "time-zone-name": "America/Chicago"
    },
    "relationships": {
      "location": {
        "links": {
          "self": "https://api.inquicker.com/v3/winter-health.inquicker.com/schedules/7b91ec6d-3d24-4478-97fc-fc4490e49b8d/relationships/location",
          "related": "https://api.inquicker.com/v3/winter-health.inquicker.com/schedules/7b91ec6d-3d24-4478-97fc-fc4490e49b8d/location"
        }
      },
      "provider": {
        "links": {
          "self": "https://api.inquicker.com/v3/winter-health.inquicker.com/schedules/7b91ec6d-3d24-4478-97fc-fc4490e49b8d/relationships/provider",
          "related": "https://api.inquicker.com/v3/winter-health.inquicker.com/schedules/7b91ec6d-3d24-4478-97fc-fc4490e49b8d/provider"
        }
      },
      "service": {
        "links": {
          "self": "https://api.inquicker.com/v3/winter-health.inquicker.com/schedules/7b91ec6d-3d24-4478-97fc-fc4490e49b8d/relationships/service",
          "related": "https://api.inquicker.com/v3/winter-health.inquicker.com/schedules/7b91ec6d-3d24-4478-97fc-fc4490e49b8d/service"
        }
      },
      "insurance-plans": {
        "links": {
          "self": "https://api.inquicker.com/v3/winter-health.inquicker.com/schedules/7b91ec6d-3d24-4478-97fc-fc4490e49b8d/relationships/insurance-plans",
          "related": "https://api.inquicker.com/v3/winter-health.inquicker.com/schedules/7b91ec6d-3d24-4478-97fc-fc4490e49b8d/insurance-plans"
        },
        "data": [{
          "type": "insurance-plans",
          "id": "aarp-ppo-12"
        }
      ]}
    }
  }],
  "included": [{
    "id": "aarp-ppo-12",
    "type": "insurance-plans",
    "links": {
      "self": "https://api.inquicker.com/v3/winter-health.inquicker.com/insurance-plans/aarp-ppo-12"
    },
    "attributes": {
      "company": "AARP",
      "name": "AARP PPO"
    }
  }],
    "meta": {
      "record-count": 1
    },
    "links": {
      "first": "https://api.inquicker.com/v3/winter-health.inquicker.com/locations/cartersville/schedules?include=insurance-plans&page%5Bnumber%5D=1&page%5Bsize%5D=10",
      "last": "https://api.inquicker.com/v3/winter-health.inquicker.com/locations/cartersville/schedules?include=insurance-plans&page%5Bnumber%5D=1&page%5Bsize%5D=10"
  }
}
```

### Get schedules for the location and include insurance plans

We fetch schedules or the Cartersville locations with the `GET /locations/{location_id}/schedules` endpoint. We want to display insurance plans for the schedules, so we side-load them with the `include` parameter.

<div style="clear:right"></div>

```shell
curl "https://api.inquicker.com/v3/winter-health.inquicker.com/available-appointment-times" -G -H "Authorization: your-api-key" -H "ACCEPT: application/vnd.api+json" --data-urlencode 'schedule_ids[]=7b91ec6d-3d24-4478-97fc-fc4490e49b8d' --data-urlencode 'appointment_type=annual-physical'
```

```json
[{
  "schedule-id": "065210e4-be1d-4862-bf1d-3dbb9f55e0de",
  "appointment-type": "annual-physical",
  "times": ["2019-09-21T13:00:00-04:00", "2019-09-21T13:15:00-04:00", "2019-09-21T13:30:00-04:00", "2019-09-21T13:45:00-04:00", "2019-09-21T14:00:00-04:00", "2019-09-21T14:15:00-04:00", "2019-09-21T14:30:00-04:00", "2019-09-21T14:45:00-04:00", "2019-09-21T15:00:00-04:00", "2019-09-21T15:15:00-04:00", "2019-09-21T15:30:00-04:00", "2019-09-21T15:45:00-04:00", "2019-09-21T16:00:00-04:00", "2019-09-21T16:15:00-04:00", "2019-09-21T16:30:00-04:00", "2019-09-21T16:45:00-04:00"]
}]
```
### Get available appointment times in those schedules

We use the `GET /available-appointment-times`, passing the schedule ids in the `shedule_ids` parameter, and the appointment type in the `appointment-type` parameter.

<div style="clear:right"></div>

### Book the appointment

<div style="clear:right"></div>

```shell
curl "https://api.inquicker.com/v3/winter-health.inquicker.com/visit-token" -G -H "Authorization: your-api-key" -H "ACCEPT: application/vnd.api+json" --data-urlencode 'schedule_id=065210e4-be1d-4862-bf1d-3dbb9f55e0de' --data-urlencode 'appointment_at=2019-09-21T13:00:00-04:00'
```

```
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJkYXRhIjp7InNjaGVkdWxlX2lkIjoiZjNjN2QwNDQtM2UyMy00YzcwLThlOTktYTUwNGExOWYyODc0IiwiYXBwb2ludG1lbnRfYXQiOiJcIjIwMTktMTAtMDNUMTQ6MTU6MDAtMDU6MDBcIiJ9LCJleHAiOjE1NzAxMTc4NDMsImp0aSI6IjcxYTg0YWQwLWMyOWYtNDNmYi1iZTVjLTJlZGUyNzBhZDQ3ZCJ9.MESqdi2QeQwcmab--ZAvRTRCMASiHtt51LLR7VfHm1M
```
#### Get a JWT (token) to allow us to create a visit resource

In order to create a visit resource, we need to get a JWT to use for authorization in the `POST /visits` endpoint. This call gives us the raw JWT data that we use in the `Authorization: Bearer` header to create the visit. The token is valid for 30 minutes, and can only be used to create a visit for the time slot specified in the token request.

<div style="clear:right"></div>

```shell
curl 'https://api.inquicker.com/v3/winter-health.inquicker.com/visits' -H 'Accept: application/vnd.api+json' -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJkYXRhIjp7InNjaGVkdWxlX2lkIjoiZjNjN2QwNDQtM2UyMy00YzcwLThlOTktYTUwNGExOWYyODc0IiwiYXBwb2ludG1lbnRfYXQiOiJcIjIwMTktMTAtMDNUMTQ6MTU6MDAtMDU6MDBcIiJ9LCJleHAiOjE1NzAxMTc4NDMsImp0aSI6IjcxYTg0YWQwLWMyOWYtNDNmYi1iZTVjLTJlZGUyNzBhZDQ3ZCJ9.MESqdi2QeQwcmab--ZAvRTRCMASiHtt51LLR7VfHm1M' -H 'Content-Type: application/vnd.api+json' --data-binary $'{"data":{"attributes":{"address":null,"address-2":null,"appointment-at":"2019-09-21T13:00:00-04:00","appointment-type":"annual-physical","birthdate":"1980-01-12T05:00:00.000Z","caregiver-name":null,"city":null,"comments":null,"email":"test@example.com","first-name":"John","gender":"male","has-physician":false,"insurance-group-number":null,"insurance-member-number":null,"insurance-plan-full-address":null,"insurance-plan-name":null,"insurance-plan-permalink":"1199-ppo","insurance-plan-phone-number":null,"last-name":"Doe","last-test-date":null,"last-test-location":null,"middle-initial":null,"new-patient":"false","optin":"0","patient-complaint":"gas","phone-number":"1231231231","pregnant":null,"primary-care-physician":null,"referring-provider-name":null,"requires-standing-assistance":null,"requires-translator":null,"state":null,"terms-tos":"1","translator-language":null,"weeks-pregnant":null,"zip":"90210"},"relationships":{"schedule":{"data":{"type":"schedules","id":"065210e4-be1d-4862-bf1d-3dbb9f55e0de"}}},"type":"visits"}}'
```

```json
{
  "data":
  {
    "id": "d8fc721b6c26a40658ce1b884109bf41",
    "type": "visits",
    "links":
    {
      "self": "http://api.inquicker.com/v3/winter-health.inquicker.com/visits/d8fc721b6c26a40658ce1b884109bf41"
    },
    "attributes":
    {
      "appointment-at": "2019-09-21T13:00:00-04:00",
      "appointment-type": "annual-physical",
      "appointment-type-name": "Annual Physical",
      "confirmation-number": 1,
      "remote-visit-ids": "1234"
    },
    "relationships":
    {
      "schedule":
      {
        "links":
        {
          "self": "http://api.inquicker.com/v3/winter-health.inquicker.com/visits/d8fc721b6c26a40658ce1b884109bf41/relationships/schedule",
          "related": "http://api.inquicker.com/v3/winter-health.inquicker.com/visits/d8fc721b6c26a40658ce1b884109bf41/schedule"
        }
      },
      "location":
      {
        "links":
        {
          "self": "http://api.inquicker.com/v3/winter-health.inquicker.com/visits/d8fc721b6c26a40658ce1b884109bf41/relationships/location",
          "related": "http://api.inquicker.com/v3/winter-health.inquicker.com/visits/d8fc721b6c26a40658ce1b884109bf41/location"
        }
      },
      "provider":
      {
        "links":
        {
          "self": "http://api.inquicker.com/v3/winter-health.inquicker.com/visits/d8fc721b6c26a40658ce1b884109bf41/relationships/provider",
          "related": "http://api.inquicker.com/v3/winter-health.inquicker.com/visits/d8fc721b6c26a40658ce1b884109bf41/provider"
        }
      }
    }
  }
}
```

#### Create the visit resource

We create the visit with the `POST /visits` endpoint, passing the JWT in the `Authorization: Bearer` header. The form data includes all required fields as described in the `POST /visits` endpoint documentation.
