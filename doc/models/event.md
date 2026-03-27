
# Event

*This model accepts additional fields of type object.*

## Structure

`Event`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Event resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `ActorSid` | `string` | Optional | The SID of the resource that triggered the event.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^[a-zA-Z]{2}[0-9a-fA-F]{32}$` |
| `ActorType` | `string` | Optional | The type of resource that triggered the event. |
| `ActorUrl` | `string` | Optional | The absolute URL of the resource that triggered the event. |
| `Description` | `string` | Optional | A description of the event. |
| `EventData` | `object` | Optional | Data about the event. For more information, see [Event types](https://www.twilio.com/docs/taskrouter/api/event#event-types). |
| `EventDate` | `DateTime?` | Optional | The time the event was sent, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `EventDateMs` | `long?` | Optional | The time the event was sent in milliseconds. |
| `EventType` | `string` | Optional | The identifier for the event. |
| `ResourceSid` | `string` | Optional | The SID of the object the event is most relevant to, such as a TaskSid, ReservationSid, or a  WorkerSid.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^[a-zA-Z]{2}[0-9a-fA-F]{32}$` |
| `ResourceType` | `string` | Optional | The type of object the event is most relevant to, such as a Task, Reservation, or a Worker). |
| `ResourceUrl` | `string` | Optional | The URL of the resource the event is most relevant to. |
| `Sid` | `string` | Optional | The unique string that we created to identify the Event resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^EV[0-9a-fA-F]{32}$` |
| `Source` | `string` | Optional | Where the Event originated. |
| `SourceIpAddress` | `string` | Optional | The IP from which the Event originated. |
| `Url` | `string` | Optional | The absolute URL of the Event resource. |
| `WorkspaceSid` | `string` | Optional | The SID of the Workspace that contains the Event.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "account_sid": "account_sid8",
  "actor_sid": "actor_sid4",
  "actor_type": "actor_type8",
  "actor_url": "actor_url6",
  "description": "description8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

