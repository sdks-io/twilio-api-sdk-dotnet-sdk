
# List Worker Response

*This model accepts additional fields of type object.*

## Structure

`ListWorkerResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Workers` | [`List<Worker>`](../../doc/models/worker.md) | Optional | - |
| `Meta` | [`Meta`](../../doc/models/meta.md) | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "workers": [
    {
      "account_sid": "account_sid0",
      "activity_name": "activity_name2",
      "activity_sid": "activity_sid2",
      "attributes": "attributes8",
      "available": false,
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

