## Visits

The Visit API allows health systems to make their own visit creation forms,
enabling them to integrate visit creation into their own websites and
applications. The Health System’s application or website can collect a patient’s
visit details and submit these to InQuicker through the Visit API. In the past,
visit creation was handled exclusively through InQuicker’s online visit creation
forms. The Visit API involves transferring patient details as shown below.

**Personal and Contact Information:**

- Full name
- Date of birth
- Gender
- Full address
- Phone number
- Email
- Caregiver name

**Appointment and Care Information:**

- Date, time, and type of appointment
- Patient complaint and comments
- Primary care physician indicator and name
- Insurance plan name, group number, member number, and insurance phone number
- Translator needed and language
- Pregnancy status and number of weeks pregnant
- Standing assistance required
- New patient indicator

**Analytics:**

- URL
- Referer
- User agent

**Other:**

- Remote UID
- Opt in

Health systems can access this feature by coordinating with their InQuicker
Implementation Manager (IM).

<aside class="notice">
The feature.api.v3_visit_create setting must be enabled at the Health System
level within the InQuicker console.*
</aside>

### Authorization

This endpoint uses a JWT token from the [`/visit-token`](#visit-token) endpoint
instead of the API key. This token is limited to the time slot that it is
created for, and expires in 30 minutes.

### Usage Notes

- Although screening questions can be used to prevent a patient from scheduling
  online, answers cannot be sent through the Visit Creation call. Since
  InQuicker's forms are bypassed, the Partner is responsible for doing their own
  validations as well as creating and linking their own "Terms of Service" form.
  Although the Terms of Service (terms-tos) and Terms 911 (terms-911) fields may
  be returned as required when querying Visit Settings, they *must not* be
  passed when creating a visit. It is included to remind the Partner of it's
  requirement. When setting up a schedule in InQuicker (to be used by API V3),
  do not require any visit fields that are not supported by API V3. Before using
  API V3 for a schedule, make sure the schedule does not require any visit
  fields that are not supported by the API. Doing so will cause validation to
  fail if the field is not submitted, but if included, will trigger an error. A
  schedule can be configured within InQuicker to use keyword filtering to
  prevent a visit from being created. For example, if the patient complaint
  contains "shortness of breath," the InQuicker scheduling page would prevent
  the patient from scheduling and would direct the patient to page about when to
  call 911. When using API V3 for visit creation the Partner is now responsible
  for such rules. If using the translator language field (translator-language),
  the list of available languages for the schedule can be retrieved using the
  [Schedules endpoint](#schedules). The API won't validate this field, so the
  Partner is responsible for doing this if desired.

### Validations

Field validations can be set up on the schedule level. However, some have
behavior that cannot be changed. Please see the validation section in the Visit
Settings call for more specific information.

### Attributes

Attribute                    | Description                                                        | Type     | Validations
---------------------------- | ------------------------------------------------------------------ | -------- | -------------------------------------------------------------------------------------------------------
address                      | First line of patient's address                                    | String   | Required if visit.full_address feature enabled
address_2                    | Second line of patient's address                                   | String   |
appointment-at               | Date and time of appointment                                       | ISO 8601 | Required
appointment-type             | Appointment type ID                                                | String   | Required if schedule has appointment types
birthdate                    | Patient's birthdate                                                | ISO 8601 | Required
caregiver-name               | Name of patient’s primary caregiver                                | String   | Required if patient’s age is 13 or younger
city                         | City of patient's address                                          | String   | Required if visit.full_address feature is enabled
comments                     | Additional comments                                                | String   |
email                        | Patient's email address                                            | String   | Required
first-name                   | Patient's first name                                               | String   | Required
gender                       | Patient's gender                                                   | String   | Required - must be "female" or "male"
has-physician                | Indicates if patient has a physician                               | String   | Required if visit.has_physician is enabled - must be "true" or "false"
insurance-group-number       | Patient's insurance plan group number                              | String   | Required if visit.insurance_group_number is set to required
insurance-member-number      | Patient's insurance plan member number                             | String   | Required if visit.insurance_member_number is set to required
insurance-plan-name          | Patient's insurance plan name                                      | String   | Required if visit.insurance_plan_name is set to required
insurance-plan-permalink     | Patient's insurance plan permalink (corresponds to InQuicker plan) | String   | Required if visit.insurance_plan_name is set to required (maps to InQuicker plan)
insurance-plan-phone-number  | Patient's insurance plan provider phone number                     | String   | Required if visit.insurance_plan_phone_number is set to required
last-name                    | Patient's last name                                                | String   | Required
middle-initial               | Patient's middle initial                                           | String   |
new-patient                  | Indicates if the patient new to the system                         | String   | Required - Must be "yes" or "no"
optin                        | Indicate if user wishes to receive health system marketing emails  | Number   | 1 indicates true, 0 indicates false
patient-complaint            | Patient's health complaint                                         | String   | Required if visit.patient_complaint is set to required
phone-number                 | Patient's contact phone number                                     | String   | Required
pregnant                     | Indicates if patient is pregnant                                   | String   | Required if patient's gender is female and visit.pregnant is set to required - Must be "yes" or "no"
primary-care-physician       | Name of patient's primary care physician                           | String   | Required if patient indicated they have a physician and visit.primary_care_physician is set to required
referer                      | Full URL that brought the user to the site                         | String   |
remote-uid                   | Passthrough field associate with visit (ex. Healthgrades / GECB)   | String   |
requires-standing-assistance | Indicates if patient requires standing assistance                  | String   | Required if visit.requires_standing_assistance is set to required - Must be "yes" or "no"
requires-translator          | Indicates if patient requires a translator                         | String   | Must be "yes" or "no"
state                        | Patient's state                                                    | String   | Required if visit.full_address is set required
translator-language          | Language requested for patient's translator                        | String   |
url                          | Full URL the user first visited on the site                        | String   | Includes UTM parameters if applicable
user-agent                   | User agent of the user who booked the appointment                  | String   |
weeks-pregnant               | Number of weeks pregnant                                           | String   | Required if patient has indicated pregnancy
zip                          | Patient's zip code                                                 | String   | Required if visit.full_address is set to required

```shell
curl "http://api.inquicker.com/api/v3/winter-health.inquicker.com/visits"
  -H "Authorization: jwt-token-from-visit-token-endpoint" -H "ACCEPT: application/vnd.api+json" --data-urlencode data='{"attributes": {"appointment-at": "2018-06-11T19:20:00-07:00", ...}, "relationships": {"schedule": {"data": {"id": "2528d709-5ab9-444e-bfec-0e1e9d4666a6", "type": "schedules"}}}}'
```

```json
{
  "data": {
    "id": "d8fc721b6c26a40658ce1b884109bf41",
    "type": "visits",
    "links": {
      "self": "http://api.inquicker.com/v3/winter_health.inquickerhost.com/visits/d8fc721b6c26a40658ce1b884109bf41"
    },
    "attributes": {
      "appointment-at": "2018-06-11T20:20:00.000-06:00",
      "appointment-type": null,
      "appointment-type-name": null,
      "confirmation-number": 1,
      "remote-visit-ids": ""
    },
    "relationships": {
      "schedule": {
        "links": {
          "self": "http://api.inquicker.com/v3/winter_health.inquickerhost.com/visits/d8fc721b6c26a40658ce1b884109bf41/relationships/schedule",
          "related": "http://api.inquicker.com/v3/winter_health.inquickerhost.com/visits/d8fc721b6c26a40658ce1b884109bf41/schedule"
        }
      },
      "location": {
        "links": {
          "self": "http://api.inquicker.com/v3/winter_health.inquickerhost.com/visits/d8fc721b6c26a40658ce1b884109bf41/relationships/location",
          "related": "http://api.inquicker.com/v3/winter_health.inquickerhost.com/visits/d8fc721b6c26a40658ce1b884109bf41/location"
        }
      },
      "provider": {
        "links": {
          "self": "http://api.inquicker.com/v3/winter_health.inquickerhost.com/visits/d8fc721b6c26a40658ce1b884109bf41/relationships/provider",
          "related": "http://api.inquicker.com/v3/winter_health.inquickerhost.com/visits/d8fc721b6c26a40658ce1b884109bf41/provider"
        }
      }
    }
  }
}
```

### POST /visits

The visits resource is a POST only endpoint which allows partners to create
visits. Visit resources cannot be queried in any way and the visit resource will
not return any patient information.

Parameter | Required | Description
--------- | -------- | -----------
attributes | true  | See below.
relationships | true | See below.

The `attributes` parameter provides the visit data to be created.

Attribute | Type | Example | Description
--------- | ---- | ------- | -----------
address | string | 1234 Main Street | First line of patient's address
address-2 | string | PO Box 123 | Second line of patient's address
birthdate | string | 1901-01-01 | Patient's birthdate
caregiver-name | string | John Doe | Name of patient’s primary caregiver
city | string | Anytown | City of patient's address
comments | string | comments | Additional comments
email | string | email@example.com | Patient's email address
first-name | string | Alice | Patient's first name
insurance-group-number | string | 123 | Patient's insurance plan group number
insurance-member-number | string | 45678 | Patient's insurance plan member number
insurance-plan-name | string | Insurance Plan Name | Patient's insurance plan name
insurance-plan-permalink | string | insurance-plan-permalink | Patient's insurance plan permalink (should correspond to an InQuicker insurance plan)
insurance-plan-phone-number | string | 250-555-555 | Patient's insurance plan provider phone number
last-name | string | Doe | Patient's last name
middle-initial | string | A | Patient's middle initial
patient-complaint | string | complaint | Patient's health complaint
phone-number | string | 250-555-5555 | Patient's contact phone number
primary-care-physician | string | Dr Bob | Name of patient's primary care physician
referer | string | https://www.google.com/search?q=book+appointment+online | Full URL that brought the user to the site
remote-uid | string | 12345 | Passthrough field associated with visit (for example, the unique identifier for visits to be exported via Healthgrades export / GECB integration)
state | string | AZ | Patient's state
translator-language | string | spanish | Language requested for patient's translator
url | string | https://example.com/?utm_medium=search&utm_source=Google&utm_campaign=fall2018 | Full URL the user first visited on the site
user-agent | string | Mozilla/5.0 (iPad; U; CPU OS 3_2_1 like Mac OS X; en-us) AppleWebKit/531.21.10 (KHTML, like Gecko) Mobile/7B405 | User agent of the user who booked the appointment
weeks-pregnant | number | 0 | Number of weeks pregnant
zip | string | 12345 | Patient's zip code

The `relationships` parameter provides the schedule to book into.

Attribute | Type | Example | Description
--------- | ---- | ------- | -----------
schedule  | object | See below | The schedule that the appointment being booked belongs to.

The schedule relationship object follows the JSON:API format for relationships,
for example:

```json
{
  "schedule": {
    "data": {
      "id": "2528d709-5ab9-444e-bfec-0e1e9d4666a6",
      "type": "schedules"
    }
  }
}
```
