
# Safelist 1

*This model accepts additional fields of type object.*

## Structure

`Safelist1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Sid` | `string` | Optional | The unique string that we created to identify the SafeList resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^GN[0-9a-fA-F]{32}$` |
| `PhoneNumber` | `string` | Optional | The phone number in SafeList. |
| `Url` | `string` | Optional | The absolute URL of the SafeList resource. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "sid": "sid4",
  "phone_number": "phone_number8",
  "url": "url8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

