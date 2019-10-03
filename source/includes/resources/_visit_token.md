## Visit Token

As an extra layer of security, Visit creation requires JSON Web Token (JWT)
authorization. The `/visit-token` endpoint provides a one-time token that is
used in the `Authorization` header for calls to the `/visits` endpoint. The
token has a 30-minute timeout, and can only be used for the specified
appointment slot.

```shell
curl 'https://api.inquicker.com/v3/winter-health.inquickerlocal.com/visit-token' -G -H "Authorization: 33ce69eec6e9869294f3899e60c26c72c2fa56ef" -H "ACCEPT: application/vnd.api+json" --data-urlencode 'schedule_id=065210e4-be1d-4862-bf1d-3dbb9f55e0de' --data-urlencode 'appointment_at="2019-01-30T20:00:00-04:00"'
```

> The above command returns the raw JSON Web Token (JWT):

```
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJkYXRhIjp7InNjaGVkdWxlX2lkIjoiMDY1MjEwZTQtYmUxZC00ODYyLWJmMWQtM2RiYjlmNTVlMGRlIiwiYXBwb2ludG1lbnRfYXQiOiJcIjIwMTktMDktMzBUMjA6MDA6MDAtMDQ6MDBcIiJ9LCJleHAiOjE1Njk4NzM2MDYsImp0aSI6ImUwOWUyY2Q5LTlmYWMtNGFmNC1hM2NkLTgyY2JhYjBjMjIyZSJ9.l0WmLmZXAln6JH6cnX3VBwBqlWHmo5Ua0tXsZWomsYI
```

### `GET /visit-token`

Get a JSON Web Token to use to authorize a call to `POST /visits`.

Parameter | Required | Example | Description
--------- | -------- | ------- | -----------
schedule_id | true | `065210e4-be1d-4862-bf1d-3dbb9f55e0de` | The UUID of the schedule containing the time slot.
appointment_at | true | `2019-01-15T20:00:00-04:00` | The time slot in ISO 8601 format.

<aside class="notice">
This endpoint does not return a JSON value. It returns the raw JWT data.
</aside>
