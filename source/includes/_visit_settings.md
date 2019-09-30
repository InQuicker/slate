## Visit Settings

Settings within InQuicker have many effects on the visit scheduling process.
The Visit Settings endpoint exports many of these settings allowing Partners to
build forms having feature parity with InQuicker's own. The Visit Settings endpoint
returns settings for a specific schedule.

The following visit settings are exported using this endpoint:

  - Validations
  - Enabled Fields
  - Patient Instructions
  - Pre-registration Forms

#### Validations

Validations describe how some fields will be validated by the server when
attempting to create a visit object. The Validation details can be used to create
client side validation routines which match the InQuicker server. One benefit of
using this API is that custom validations can be added on the client side regardless
of the InQuicker setup.

<aside class="notice">
Not all validations used on the server are reported using this interface. For
example, some EHR integrations reference a database of valid phone numbers.
Visit creation should always check for errors.
</aside>

The following validations are reported with this endpoint:

```json
{
  "type": "validation",
  "attributes": {
    "kind": "acceptance",
    "attributes": [
      "terms-911"
    ],
    "accept": "1",
    "allow-nil": true
  }
},
```

##### Acceptance Validator

The acceptance validator ensures that the user has accepted a 'Yes/No' question.
Acceptable values for the attribute are '1' or 'True'.

<div style="clear:right"></div>

```json
{
  "type": "validation",
  "attributes": {
    "kind": "birthdate",
    "attributes": [
      "birthdate"
    ]
  }
},
```

##### Birthdate Validator

The birthdate validation checks that the attribute passed is any date before
the current date.

<div style="clear:right"></div>

```json
{
  "type": "validation",
  "attributes": {
    "kind": "email",
    "attributes": [
      "email"
    ]
  }
},
```

##### Email Validator

The email validation routine checks that the attribute passed is a parsable
 email address and attempts to verify the domain part DNS record.

 <div style="clear:right"></div>

```json
 {
   "type": "validation",
   "attributes": {
     "kind": "format",
     "attributes": [
       "middle-initial"
     ],
     "allow-blank": true,
     "with": "(?-mix:A[a-zA-Z]{1}z)"
   }
 },
 ```

##### Format Validator

The format routine checks the attribute against a regular expression which is
passed with the validator.

Parameters:

* **with**: a regular expression.

*Important* The regular expression is a Ruby regular expression. While we favor
simple regular expressions, we cannot guarantee that the regular expression
passed will work with other langauges.

<div style="clear:right"></div>

```json
{
  "type": "validation",
  "attributes": {
    "kind": "inclusion",
    "attributes": [
      "has-physician"
    ],
    "in": [
      true,
      false
    ]
  }
},
```

##### Inclusion Validator

The inclusion validation checks to see that the attribute is in a list of
acceptable values.

Parameters:

* **in**: array of acceptable values

<div style="clear:right"></div>

```json
{
  "type": "validation",
  "attributes": {
    "kind": "length",
    "attributes": [
      "zip"
    ],
    "is": "5"
  }
},
```

##### Length Validator

The length validator checks the length of the attribute.

Parameters:

* **is**: the number of characters required

<div style="clear:right"></div>

```json
{
  "type": "validation",
  "attributes": {
    "kind": "numericality",
    "attributes": [
      "zip"
    ]
  }
},
```

##### Numericality Validator

The numericality validator checks to see if the attribute is numeric.
<div style="clear:right"></div>

```json
{
  "type": "validation",
  "attributes": {
    "kind": "presence",
    "attributes": [
      "birthdate"
    ]
  }
}
```


##### Presence Validator

The presence routine validates that a value exists.

<div style="clear:right"></div>

```json
{
  "type": "validation",
  "attributes": {
    "kind": "phone",
    "attributes": [
      "phone-number"
    ]
  }
},
```

##### Phone Validator

The phone validator attempts to verify that the attribute passed is a North
American phone number with an included area code.

The value is stripped of any delimiters, and then checked to ensure that
10 digits remain.
