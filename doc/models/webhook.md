
# Webhook

*This model accepts additional fields of type object.*

## Structure

`Webhook`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Sid` | `string` | Optional | The unique string that we created to identify the Webhook resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^YW[0-9a-fA-F]{32}$` |
| `ServiceSid` | `string` | Optional | The unique SID identifier of the Service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Service resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `FriendlyName` | `string` | Optional | The string that you assigned to describe the webhook. **This value should not contain PII.** |
| `EventTypes` | `List<string>` | Optional | The array of events that this Webhook is subscribed to. Possible event types: `*, factor.deleted, factor.created, factor.verified, challenge.approved, challenge.denied` |
| `Status` | [`WebhookEnumStatus?`](../../doc/models/webhook-enum-status.md) | Optional | The webhook status. Default value is `enabled`. One of: `enabled` or `disabled` |
| `Version` | [`WebhookEnumVersion?`](../../doc/models/webhook-enum-version.md) | Optional | The webhook version. Default value is `v2` which includes all the latest fields. Version `v1` is legacy and may be removed in the future. |
| `WebhookUrl` | `string` | Optional | The URL associated with this Webhook. |
| `WebhookMethod` | [`ConfigurationWebhookMethod?`](../../doc/models/configuration-webhook-method.md) | Optional | The method to be used when calling the webhook's URL. |
| `DateCreated` | `DateTime?` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `DateUpdated` | `DateTime?` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `Url` | `string` | Optional | The absolute URL of the Webhook resource. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "sid": "sid2",
  "service_sid": "service_sid6",
  "account_sid": "account_sid2",
  "friendly_name": "friendly_name8",
  "event_types": [
    "event_types4",
    "event_types5"
  ],
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

