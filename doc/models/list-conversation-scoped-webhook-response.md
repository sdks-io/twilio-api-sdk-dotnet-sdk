
# List Conversation Scoped Webhook Response

*This model accepts additional fields of type object.*

## Structure

`ListConversationScopedWebhookResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Webhooks` | [`List<ConversationScopedWebhook>`](../../doc/models/conversation-scoped-webhook.md) | Optional | - |
| `Meta` | [`Meta`](../../doc/models/meta.md) | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "webhooks": [
    {
      "sid": "sid2",
      "account_sid": "account_sid2",
      "conversation_sid": "conversation_sid8",
      "target": "target6",
      "url": "url0",
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

