
# Conversation with Participants

*This model accepts additional fields of type object.*

## Structure

`ConversationWithParticipants`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccountSid` | `string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `ChatServiceSid` | `string` | Optional | The unique ID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `MessagingServiceSid` | `string` | Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `Sid` | `string` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CH[0-9a-fA-F]{32}$` |
| `FriendlyName` | `string` | Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `UniqueName` | `string` | Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `Attributes` | `string` | Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `State` | [`ConversationWithParticipantsState?`](../../doc/models/conversation-with-participants-state.md) | Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `DateCreated` | `DateTime?` | Optional | The date that this resource was created. |
| `DateUpdated` | `DateTime?` | Optional | The date that this resource was last updated. |
| `Timers` | `object` | Optional | Timer date values representing state update for this conversation. |
| `Links` | `object` | Optional | Contains absolute URLs to access the [participants](https://www.twilio.com/docs/conversations/api/conversation-participant-resource), [messages](https://www.twilio.com/docs/conversations/api/conversation-message-resource) and [webhooks](https://www.twilio.com/docs/conversations/api/conversation-scoped-webhook-resource) of this conversation. |
| `Bindings` | `object` | Optional | - |
| `Url` | `string` | Optional | An absolute API resource URL for this conversation. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "account_sid": "account_sid0",
  "chat_service_sid": "chat_service_sid4",
  "messaging_service_sid": "messaging_service_sid6",
  "sid": "sid6",
  "friendly_name": "friendly_name0",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

