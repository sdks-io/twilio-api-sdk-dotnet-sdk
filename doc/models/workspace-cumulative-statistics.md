
# Workspace Cumulative Statistics

*This model accepts additional fields of type object.*

## Structure

`WorkspaceCumulativeStatistics`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Workspace resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `AvgTaskAcceptanceTime` | `int?` | Optional | The average time in seconds between Task creation and acceptance.<br><br>**Default**: `0` |
| `StartTime` | `DateTime?` | Optional | The beginning of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `EndTime` | `DateTime?` | Optional | The end of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `ReservationsCreated` | `int?` | Optional | The total number of Reservations that were created for Workers.<br><br>**Default**: `0` |
| `ReservationsAccepted` | `int?` | Optional | The total number of Reservations accepted by Workers.<br><br>**Default**: `0` |
| `ReservationsRejected` | `int?` | Optional | The total number of Reservations that were rejected.<br><br>**Default**: `0` |
| `ReservationsTimedOut` | `int?` | Optional | The total number of Reservations that were timed out.<br><br>**Default**: `0` |
| `ReservationsCanceled` | `int?` | Optional | The total number of Reservations that were canceled.<br><br>**Default**: `0` |
| `ReservationsRescinded` | `int?` | Optional | The total number of Reservations that were rescinded.<br><br>**Default**: `0` |
| `SplitByWaitTime` | `object` | Optional | A list of objects that describe the number of Tasks canceled and reservations accepted above and below the thresholds specified in seconds. |
| `WaitDurationUntilAccepted` | `object` | Optional | The wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks that were accepted. |
| `WaitDurationUntilCanceled` | `object` | Optional | The wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks that were canceled. |
| `TasksCanceled` | `int?` | Optional | The total number of Tasks that were canceled.<br><br>**Default**: `0` |
| `TasksCompleted` | `int?` | Optional | The total number of Tasks that were completed.<br><br>**Default**: `0` |
| `TasksCreated` | `int?` | Optional | The total number of Tasks created.<br><br>**Default**: `0` |
| `TasksDeleted` | `int?` | Optional | The total number of Tasks that were deleted.<br><br>**Default**: `0` |
| `TasksMoved` | `int?` | Optional | The total number of Tasks that were moved from one queue to another.<br><br>**Default**: `0` |
| `TasksTimedOutInWorkflow` | `int?` | Optional | The total number of Tasks that were timed out of their Workflows (and deleted).<br><br>**Default**: `0` |
| `WorkspaceSid` | `string` | Optional | The SID of the Workspace.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `Url` | `string` | Optional | The absolute URL of the Workspace statistics resource. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "avg_task_acceptance_time": 0,
  "reservations_created": 0,
  "reservations_accepted": 0,
  "reservations_rejected": 0,
  "reservations_timed_out": 0,
  "reservations_canceled": 0,
  "reservations_rescinded": 0,
  "tasks_canceled": 0,
  "tasks_completed": 0,
  "tasks_created": 0,
  "tasks_deleted": 0,
  "tasks_moved": 0,
  "tasks_timed_out_in_workflow": 0,
  "account_sid": "account_sid4",
  "start_time": "2016-03-13T12:52:32.123Z",
  "end_time": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

