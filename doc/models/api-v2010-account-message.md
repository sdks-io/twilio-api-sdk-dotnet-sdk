
# Api V2010 Account Message

*This model accepts additional fields of type object.*

## Structure

`ApiV2010AccountMessage`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Body` | `string` | Optional | The text content of the message |
| `NumSegments` | `string` | Optional | The number of segments that make up the complete message. SMS message bodies that exceed the [character limit](https://www.twilio.com/docs/glossary/what-sms-character-limit) are segmented and charged as multiple messages. Note: For messages sent via a Messaging Service, `num_segments` is initially `0`, since a sender hasn't yet been assigned. |
| `Direction` | [`MessageEnumDirection?`](../../doc/models/message-enum-direction.md) | Optional | The direction of the message. Can be: `inbound` for incoming messages, `outbound-api` for messages created by the REST API, `outbound-call` for messages created during a call, or `outbound-reply` for messages created in response to an incoming message. |
| `From` | `string` | Optional | The sender's phone number (in [E.164](https://en.wikipedia.org/wiki/E.164) format), [alphanumeric sender ID](https://www.twilio.com/docs/sms/quickstart), [Wireless SIM](https://www.twilio.com/docs/iot/wireless/programmable-wireless-send-machine-machine-sms-commands), [short code](https://www.twilio.com/en-us/messaging/channels/sms/short-codes), or  [channel address](https://www.twilio.com/docs/messaging/channels) (e.g., `whatsapp:+15554449999`). For incoming messages, this is the number or channel address of the sender. For outgoing messages, this value is a Twilio phone number, alphanumeric sender ID, short code, or channel address from which the message is sent. |
| `To` | `string` | Optional | The recipient's phone number (in [E.164](https://en.wikipedia.org/wiki/E.164) format) or [channel address](https://www.twilio.com/docs/messaging/channels) (e.g. `whatsapp:+15552229999`) |
| `DateUpdated` | `string` | Optional | The [RFC 2822](https://datatracker.ietf.org/doc/html/rfc2822#section-3.3) timestamp (in GMT) of when the Message resource was last updated |
| `Price` | `string` | Optional | The amount billed for the message in the currency specified by `price_unit`. The `price` is populated after the message has been sent/received, and may not be immediately availalble. View the [Pricing page](https://www.twilio.com/en-us/pricing) for more details. |
| `ErrorMessage` | `string` | Optional | The description of the `error_code` if the Message `status` is `failed` or `undelivered`. If no error was encountered, the value is `null`. The value returned in this field for a specific error cause is subject to change as Twilio improves errors. Users should not use the `error_code` and `error_message` fields programmatically. |
| `Uri` | `string` | Optional | The URI of the Message resource, relative to `https://api.twilio.com`. |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) associated with the Message resource<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `NumMedia` | `string` | Optional | The number of media files associated with the Message resource. |
| `Status` | [`VerificationAttemptEnumMessageStatus?`](../../doc/models/verification-attempt-enum-message-status.md) | Optional | The status of the Message. Possible values: `accepted`, `scheduled`, `canceled`, `queued`, `sending`, `sent`, `failed`, `delivered`, `undelivered`, `receiving`, `received`, or `read` (WhatsApp only). For more information, See [detailed descriptions](https://www.twilio.com/docs/sms/api/message-resource#message-status-values). |
| `MessagingServiceSid` | `string` | Optional | The SID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) associated with the Message resource. A unique default value is assigned if a Messaging Service is not used.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `Sid` | `string` | Optional | The unique, Twilio-provided string that identifies the Message resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^(SM\|MM)[0-9a-fA-F]{32}$` |
| `DateSent` | `string` | Optional | The [RFC 2822](https://datatracker.ietf.org/doc/html/rfc2822#section-3.3) timestamp (in GMT) of when the Message was sent. For an outgoing message, this is when Twilio sent the message. For an incoming message, this is when Twilio sent the HTTP request to your incoming message webhook URL. |
| `DateCreated` | `string` | Optional | The [RFC 2822](https://datatracker.ietf.org/doc/html/rfc2822#section-3.3) timestamp (in GMT) of when the Message resource was created |
| `ErrorCode` | `int?` | Optional | The [error code](https://www.twilio.com/docs/api/errors) returned if the Message `status` is `failed` or `undelivered`. If no error was encountered, the value is `null`. The value returned in this field for a specific error cause is subject to change as Twilio improves errors. Users should not use the `error_code` and `error_message` fields programmatically. |
| `PriceUnit` | `string` | Optional | The currency in which `price` is measured, in [ISO 4127](https://www.iso.org/iso/home/standards/currency_codes.htm) format (e.g. `usd`, `eur`, `jpy`). |
| `ApiVersion` | `string` | Optional | The API version used to process the Message |
| `SubresourceUris` | `object` | Optional | A list of related resources identified by their URIs relative to `https://api.twilio.com` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "body": "body4",
  "num_segments": "num_segments4",
  "direction": "inbound",
  "from": "from4",
  "to": "to8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

