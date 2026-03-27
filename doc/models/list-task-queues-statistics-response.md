
# List Task Queues Statistics Response

*This model accepts additional fields of type object.*

## Structure

`ListTaskQueuesStatisticsResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `TaskQueuesStatistics` | [`List<TaskQueuesStats>`](../../doc/models/task-queues-stats.md) | Optional | - |
| `Meta` | [`Meta`](../../doc/models/meta.md) | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "task_queues_statistics": [
    {
      "account_sid": "account_sid0",
      "cumulative": {
        "key1": "val1",
        "key2": "val2"
      },
      "realtime": {
        "key1": "val1",
        "key2": "val2"
      },
      "task_queue_sid": "task_queue_sid8",
      "workspace_sid": "workspace_sid2",
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

