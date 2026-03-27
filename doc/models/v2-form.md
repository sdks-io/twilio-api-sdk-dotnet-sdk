
# V2 Form

*This model accepts additional fields of type object.*

## Structure

`V2Form`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `FormType` | [`FormEnumFormTypes?`](../../doc/models/form-enum-form-types.md) | Optional | The Type of this Form. Currently only `form-push` is supported. |
| `Forms` | `object` | Optional | Object that contains the available forms for this type. This available forms are given in the standard [JSON Schema](https://json-schema.org/) format |
| `FormMeta` | `object` | Optional | Additional information for the available forms for this type. E.g. The separator string used for `binding` in a Factor push. |
| `Url` | `string` | Optional | The URL to access the forms for this type. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "form_type": "form-push",
  "forms": {
    "key1": "val1",
    "key2": "val2"
  },
  "form_meta": {
    "key1": "val1",
    "key2": "val2"
  },
  "url": "url8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

