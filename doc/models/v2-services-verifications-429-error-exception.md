
# V2 Services Verifications 429 Error Exception

*This model accepts additional fields of type object.*

## Structure

`V2ServicesVerifications429ErrorException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Code` | `int?` | Optional | Twilio-specific error code |
| `MessageProperty` | `string` | Optional | Error message |
| `MoreInfo` | `string` | Optional | Link to Error Code References |
| `Status` | `int?` | Optional | HTTP response status code |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "code": 0,
  "message": "message0",
  "more_info": "more_info2",
  "status": 178,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

