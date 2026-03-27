
# Workspace Real Time Statistics

*This model accepts additional fields of type object.*

## Structure

`WorkspaceRealTimeStatistics`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Workspace resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `ActivityStatistics` | `object` | Optional | The number of current Workers by Activity. |
| `LongestTaskWaitingAge` | `int?` | Optional | The age of the longest waiting Task.<br><br>**Default**: `0` |
| `LongestTaskWaitingSid` | `string` | Optional | The SID of the longest waiting Task.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `TasksByPriority` | `object` | Optional | The number of Tasks by priority. For example: `{"0": "10", "99": "5"}` shows 10 Tasks at priority 0 and 5 at priority 99. |
| `TasksByStatus` | `object` | Optional | The number of Tasks by their current status. For example: `{"pending": "1", "reserved": "3", "assigned": "2", "completed": "5"}`. |
| `TotalTasks` | `int?` | Optional | The total number of Tasks.<br><br>**Default**: `0` |
| `TotalWorkers` | `int?` | Optional | The total number of Workers in the Workspace.<br><br>**Default**: `0` |
| `WorkspaceSid` | `string` | Optional | The SID of the Workspace.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `Url` | `string` | Optional | The absolute URL of the Workspace statistics resource. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "longest_task_waiting_age": 0,
  "total_tasks": 0,
  "total_workers": 0,
  "account_sid": "account_sid0",
  "activity_statistics": [
    {
      "key1": "val1",
      "key2": "val2"
    }
  ],
  "longest_task_waiting_sid": "longest_task_waiting_sid8",
  "tasks_by_priority": {
    "key1": "val1",
    "key2": "val2"
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

