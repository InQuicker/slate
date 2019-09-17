---
title: InQuicker API V3 Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - appointment_types
  - insurance_plans
  - locations
  - providers
  - schedules
  - errors

search: true
---

# Introduction

Welcome to the InQuicker API! You can use our API to enable patient scheduling in your business or application.

# Authentication

InQuicker uses API keys to allow access to the API. You can retrieve your InQuicker API key by contacting your Account Representative.

InQuicker expects for the API key to be included in all API requests to the server in as a query parameter that looks like the following:

`api_key=this-is-your-api-key`

<aside class="notice">
You must replace <code>this-is-your-api-key</code> with your personal API key.
</aside>
