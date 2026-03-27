
# Workers Cumulative Statistics

*This model accepts additional fields of type object.*

## Structure

`WorkersCumulativeStatistics`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Worker resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `StartTime` | `DateTime?` | Optional | The beginning of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `EndTime` | `DateTime?` | Optional | The end of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `ActivityDurations` | `object` | Optional | The minimum, average, maximum, and total time (in seconds) that Workers spent in each Activity. |
| `ReservationsCreated` | `int?` | Optional | The total number of Reservations that were created.<br><br>**Default**: `0` |
| `ReservationsAccepted` | `int?` | Optional | The total number of Reservations that were accepted.<br><br>**Default**: `0` |
| `ReservationsRejected` | `int?` | Optional | The total number of Reservations that were rejected.<br><br>**Default**: `0` |
| `ReservationsTimedOut` | `int?` | Optional | The total number of Reservations that were timed out.<br><br>**Default**: `0` |
| `ReservationsCanceled` | `int?` | Optional | The total number of Reservations that were canceled.<br><br>**Default**: `0` |
| `ReservationsRescinded` | `int?` | Optional | The total number of Reservations that were rescinded.<br><br>**Default**: `0` |
| `WorkspaceSid` | `string` | Optional | The SID of the Workspace that contains the Workers.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `Url` | `string` | Optional | The absolute URL of the Workers statistics resource. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "reservations_created": 0,
  "reservations_accepted": 0,
  "reservations_rejected": 0,
  "reservations_timed_out": 0,
  "reservations_canceled": 0,
  "reservations_rescinded": 0,
  "account_sid": "account_sid2",
  "start_time": "2016-03-13T12:52:32.123Z",
  "end_time": "2016-03-13T12:52:32.123Z",
  "activity_durations": [
    {
      "key1": "val1",
      "key2": "val2"
    }
  ],
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

