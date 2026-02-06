
# Accounts V1 Auth Token Promotion

*This model accepts additional fields of type object.*

## Structure

`AccountsV1AuthTokenPromotion`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that the secondary Auth Token was created for.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `AuthToken` | `string` | Optional | The promoted Auth Token that must be used to authenticate future API requests. |
| `DateCreated` | `DateTime?` | Optional | The date and time in UTC when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `DateUpdated` | `DateTime?` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `Url` | `string` | Optional | The URI for this resource, relative to `https://accounts.twilio.com` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "account_sid": "account_sid0",
  "auth_token": "auth_token0",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "url": "url8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

