
# List Service Participant Conversation Response

*This model accepts additional fields of type object.*

## Structure

`ListServiceParticipantConversationResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Conversations` | [`List<ServiceParticipantConversation>`](../../doc/models/service-participant-conversation.md) | Optional | - |
| `Meta` | [`Meta`](../../doc/models/meta.md) | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "conversations": [
    {
      "account_sid": "account_sid6",
      "chat_service_sid": "chat_service_sid0",
      "participant_sid": "participant_sid8",
      "participant_user_sid": "participant_user_sid6",
      "participant_identity": "participant_identity2",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    {
      "account_sid": "account_sid6",
      "chat_service_sid": "chat_service_sid0",
      "participant_sid": "participant_sid8",
      "participant_user_sid": "participant_user_sid6",
      "participant_identity": "participant_identity2",
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

