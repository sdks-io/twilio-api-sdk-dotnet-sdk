
# Service Notification

*This model accepts additional fields of type object.*

## Structure

`ServiceNotification`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccountSid` | `string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this configuration.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `ChatServiceSid` | `string` | Optional | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Configuration applies to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `NewMessage` | `object` | Optional | The Push Notification configuration for New Messages. |
| `AddedToConversation` | `object` | Optional | The Push Notification configuration for being added to a Conversation. |
| `RemovedFromConversation` | `object` | Optional | The Push Notification configuration for being removed from a Conversation. |
| `LogEnabled` | `bool?` | Optional | Weather the notification logging is enabled. |
| `Url` | `string` | Optional | An absolute API resource URL for this configuration. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "account_sid": "account_sid6",
  "chat_service_sid": "chat_service_sid0",
  "new_message": {
    "key1": "val1",
    "key2": "val2"
  },
  "added_to_conversation": {
    "key1": "val1",
    "key2": "val2"
  },
  "removed_from_conversation": {
    "key1": "val1",
    "key2": "val2"
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

