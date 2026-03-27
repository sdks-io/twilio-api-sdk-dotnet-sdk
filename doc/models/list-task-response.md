
# List Task Response

*This model accepts additional fields of type object.*

## Structure

`ListTaskResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Tasks` | [`List<TaskRouterTask>`](../../doc/models/task-router-task.md) | Optional | - |
| `Meta` | [`Meta`](../../doc/models/meta.md) | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "tasks": [
    {
      "account_sid": "account_sid6",
      "age": 162,
      "assignment_status": "assigned",
      "attributes": "attributes4",
      "addons": "addons8",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    {
      "account_sid": "account_sid6",
      "age": 162,
      "assignment_status": "assigned",
      "attributes": "attributes4",
      "addons": "addons8",
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

