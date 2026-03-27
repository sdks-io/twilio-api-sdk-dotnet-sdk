
# Task Router Task

*This model accepts additional fields of type object.*

## Structure

`TaskRouterTask`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Task resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `Age` | `int?` | Optional | The number of seconds since the Task was created.<br><br>**Default**: `0` |
| `AssignmentStatus` | [`TaskStatus?`](../../doc/models/task-status.md) | Optional | The current status of the Task's assignment. Can be: `pending`, `reserved`, `assigned`, `canceled`, `wrapping`, or `completed`. |
| `Attributes` | `string` | Optional | The JSON string with custom attributes of the work. **Note** If this property has been assigned a value, it will only be displayed in FETCH action that returns a single resource. Otherwise, it will be null. |
| `Addons` | `string` | Optional | An object that contains the [Add-on](https://www.twilio.com/docs/add-ons) data for all installed Add-ons. |
| `DateCreated` | `DateTime?` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `DateUpdated` | `DateTime?` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `TaskQueueEnteredDate` | `DateTime?` | Optional | The date and time in GMT when the Task entered the TaskQueue, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `Priority` | `int?` | Optional | The current priority score of the Task as assigned to a Worker by the workflow. Tasks with higher priority values will be assigned before Tasks with lower values.<br><br>**Default**: `0` |
| `Reason` | `string` | Optional | The reason the Task was canceled or completed, if applicable. |
| `Sid` | `string` | Optional | The unique string that we created to identify the Task resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `TaskQueueSid` | `string` | Optional | The SID of the TaskQueue.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `TaskQueueFriendlyName` | `string` | Optional | The friendly name of the TaskQueue. |
| `TaskChannelSid` | `string` | Optional | The SID of the TaskChannel.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^TC[0-9a-fA-F]{32}$` |
| `TaskChannelUniqueName` | `string` | Optional | The unique name of the TaskChannel. |
| `Timeout` | `int?` | Optional | The amount of time in seconds that the Task can live before being assigned.<br><br>**Default**: `0` |
| `WorkflowSid` | `string` | Optional | The SID of the Workflow that is controlling the Task.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `WorkflowFriendlyName` | `string` | Optional | The friendly name of the Workflow that is controlling the Task. |
| `WorkspaceSid` | `string` | Optional | The SID of the Workspace that contains the Task.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `Url` | `string` | Optional | The absolute URL of the Task resource. |
| `Links` | `object` | Optional | The URLs of related resources. |
| `VirtualStartTime` | `DateTime?` | Optional | The date and time in GMT indicating the ordering for routing of the Task specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `IgnoreCapacity` | `bool?` | Optional | A boolean that indicates if the Task should respect a Worker's capacity and availability during assignment. This field can only be used when the `RoutingTarget` field is set to a Worker SID. By setting `IgnoreCapacity` to a value of `true`, `1`, or `yes`, the Task will be routed to the Worker without respecting their capacity and availability. Any other value will enforce the Worker's capacity and availability. The default value of `IgnoreCapacity` is `true` when the `RoutingTarget` is set to a Worker SID. |
| `RoutingTarget` | `string` | Optional | A SID of a Worker, Queue, or Workflow to route a Task to |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "age": 0,
  "priority": 0,
  "timeout": 0,
  "account_sid": "account_sid6",
  "assignment_status": "assigned",
  "attributes": "attributes4",
  "addons": "addons8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

