
# Conversation Message

*This model accepts additional fields of type object.*

## Structure

`ConversationMessage`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccountSid` | `string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this message.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `ConversationSid` | `string` | Optional | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CH[0-9a-fA-F]{32}$` |
| `Sid` | `string` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `Index` | `int?` | Optional | The index of the message within the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource).  Indices may skip numbers, but will always be in order of when the message was received.<br><br>**Default**: `0` |
| `Author` | `string` | Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `Body` | `string` | Optional | The content of the message, can be up to 1,600 characters long. |
| `Media` | `object` | Optional | An array of objects that describe the Message's media, if the message contains media. Each object contains these fields: `content_type` with the MIME type of the media, `filename` with the name of the media, `sid` with the SID of the Media resource, and `size` with the media object's file size in bytes. If the Message has no media, this value is `null`. |
| `Attributes` | `string` | Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `ParticipantSid` | `string` | Optional | The unique ID of messages's author participant. Null in case of `system` sent message.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MB[0-9a-fA-F]{32}$` |
| `DateCreated` | `DateTime?` | Optional | The date that this resource was created. |
| `DateUpdated` | `DateTime?` | Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `Url` | `string` | Optional | An absolute API resource API URL for this message. |
| `Delivery` | `object` | Optional | An object that contains the summary of delivery statuses for the message to non-chat participants. |
| `Links` | `object` | Optional | Contains an absolute API resource URL to access the delivery & read receipts of this message. |
| `ContentSid` | `string` | Optional | The unique ID of the multi-channel [Rich Content](https://www.twilio.com/docs/content) template.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HX[0-9a-fA-F]{32}$` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "index": 0,
  "account_sid": "account_sid2",
  "conversation_sid": "conversation_sid2",
  "sid": "sid8",
  "author": "author6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

