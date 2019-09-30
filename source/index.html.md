---
title: InQuicker API V3 Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://docs.inquicker.com/api/v2/'>APIv2 Documentation</a>

includes:
  - appointment_types
  - health_systems
  - insurance_plans
  - locations
  - medical_groups
  - providers
  - schedules
  - services
  - visit_settings
  - visits
  - errors

search: true
---

# Introduction

This is the reference documentation for the InQuicker API. You can use our API to enable patient scheduling in your business or application.

The InQuicker API follows the [JSON:API](https://jsonapi.org/) Specification. See their site to get started with JSON:API.

# Document Conventions

# Making Requests

The API endpoint URL is

`https://api.inquicker.com/api/v3/{partner_hostname}`

where

<dl>
  <dt>api_hostname</dt>
  <dd><code>api.inquicker.com</code> for production, <code>api.inquickerstaging.com</code> for staging</dd>

  <dt>partner_hostname</dt>
  <dd>your client-facing domain name, eg. <code>my-site.inquicker.com</code>.</dd>
</dl>

### Request headers

* When developing your own integrations, be sure to set your **User-Agent** header to something informative, eg. `MyClient/1.0.0`.
* Always set the **Accept** header to `application/vnd.api+json`.

# Authentication

InQuicker uses API keys to allow access to the API. You can retrieve your InQuicker API key by contacting your Account Representative.

InQuicker expects for the API key to be included in all API requests to the server in as a query parameter that looks like the following:

`api_key=this-is-your-api-key`

<aside class="notice">
You must replace <code>this-is-your-api-key</code> with your personal API key.
</aside>

# Resources

The code samples use the "Winter Health" health system for demonstration purposes.
