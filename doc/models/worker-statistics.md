
# Worker Statistics

*This model accepts additional fields of type object.*

## Structure

`WorkerStatistics`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Realtime` | `object` | Optional | An object that contains the real-time statistics for the Worker. |
| `Cumulative` | `object` | Optional | An object that contains the cumulative statistics for the Worker. |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Worker resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `WorkspaceSid` | `string` | Optional | The SID of the Workspace that contains the Worker.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `Url` | `string` | Optional | The absolute URL of the Worker statistics resource. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "realtime": {
    "key1": "val1",
    "key2": "val2"
  },
  "cumulative": {
    "key1": "val1",
    "key2": "val2"
  },
  "account_sid": "account_sid2",
  "workspace_sid": "workspace_sid6",
  "url": "url0",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

