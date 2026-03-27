
# List Binding Response

*This model accepts additional fields of type object.*

## Structure

`ListBindingResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Bindings` | [`List<Binding>`](../../doc/models/binding.md) | Optional | - |
| `Meta` | [`Meta`](../../doc/models/meta.md) | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "bindings": [
    {
      "sid": "sid0",
      "account_sid": "account_sid4",
      "service_sid": "service_sid6",
      "credential_sid": "credential_sid8",
      "date_created": "2016-03-13T12:52:32.123Z",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    }
  ],
  "meta": {
    "first_page_url": "first_page_url0",
    "key": "key2",
    "next_page_url": "next_page_url4",
    "page": 240,
    "page_size": 56,
    "exampleAdditionalProperty": {
      "key1": "val1",
      "key2": "val2"
    }
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

