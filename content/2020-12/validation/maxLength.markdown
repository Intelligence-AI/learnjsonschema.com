---
keyword: "maxLength"
signature: "Integer"
summary: "A string instance is valid against this keyword if its length is less than, or equal to, the value of this keyword."
kind: [ "assertion" ]
instance: [ "string" ]
specification: "https://json-schema.org/draft/2020-12/json-schema-validation.html#section-6.3.1"
metaschema: "https://json-schema.org/draft/2020-12/meta/validation"
index: -9999
introduced_in: draft1
related:
  - vocabulary: validation
    keyword: minLength
  - vocabulary: validation
    keyword: pattern
  - vocabulary: format-annotation
    keyword: format
---

The `maxLength` keyword is used to specify the maximum length of a string instance. It is used to enforce a constraint on the maximum number of characters allowed for a string instance.

* Applies only to string data types.
* Value must be a non-negative integer.
* String length is counted in characters, not bytes.
* Validation succeeds if the string length is less than or equal to the specified `maxLength`.

## Examples

{{<schema `Schema restricting string length to a maximum of 10 characters`>}}
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "string",
  "maxLength": 10
}
{{</schema>}}

{{<instance-pass `An instance with a string length less than or equal to 10 is valid`>}}
"foo"
{{</instance-pass>}}

{{<instance-fail `An instance with a string length greater than 10 is invalid`>}}
"This is an invalid string"
{{</instance-fail>}}

{{<schema `Schema allowing either a string with a maximum of 20 characters or a numeric value`>}}
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": [ "string", "number" ],
  "maxLength": 20
}

{{</schema>}}

{{<instance-pass `An instance with a string length less than or equal to 20 is valid`>}}
"This is a valid string"
{{</instance-pass>}}

{{<instance-fail `An instance with a string length greater than 20 is invalid`>}}
"This description is too long"
{{</instance-fail>}}

{{<instance-pass `An instance with a numeric value is valid`>}}
55
{{</instance-pass>}}