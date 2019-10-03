---
title: InQuicker API V3 Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://docs.inquicker.com/api/v2/'>APIv2 Documentation</a>

includes:
  - resources
  - resources/appointment_types
  - resources/health_systems
  - resources/insurance_plans
  - resources/locations
  - resources/medical_groups
  - resources/providers
  - resources/schedules
  - resources/services
  - resources/visit_settings
  - resources/visit_token
  - resources/visits
  - errors

search: true
---

# Introduction

This is the reference documentation for the InQuicker API. You can use our API
to enable patient scheduling in your business or application.

The InQuicker API follows the [JSON:API](https://jsonapi.org/) Specification.
See their site to get started with JSON:API, and with [client
libraries](https://jsonapi.org/implementations/) to help build your custom
solution.

# Document Conventions

# Making Requests

The v3 API endpoint URL is

`https://{api_hostname}/api/v3/{partner_hostname}`

where:

<dl>
  <dt>api_hostname</dt>
  <dd><code>api.inquicker.com</code> for production, <code>api.inquickerstaging.com</code> for staging</dd>

  <dt>partner_hostname</dt>
  <dd>your client-facing domain name, eg. <code>my-site.inquicker.com</code>.</dd>
</dl>

### Request headers

* When developing your own integrations, be sure to set your **User-Agent** header to something informative, eg. `MyClient/1.0.0`.
* Always set the **Accept** header to `application/vnd.api+json`.

### Side-Loading Related Data

The JSON:API specification allows for [side-loading associated
records](https://jsonapi.org/format/#fetching-includes) using the `include`
parameter. For example, the `/locations/{location_id}` endpoint can include
related schedules. The response payload follows the specification, but is
typically de-serialized by a [client
library](https://jsonapi.org/implementations/).

# Authentication

InQuicker uses API keys to allow access to the API. You can retrieve your
InQuicker API key by contacting your Account Representative.

InQuicker expects for the API key to be included in all API requests to the
server in as a query parameter that looks like the following:

`api_key=this-is-your-api-key`

The one exception for this rule is for the [`POST /visits`](#post-visits) endpoint, which uses a JWT token for authentication. See the [`GET /visit-token`](#get-visit-token) documentation for more information.

<aside class="notice">
You must replace <code>this-is-your-api-key</code> with your personal API key.
</aside>
