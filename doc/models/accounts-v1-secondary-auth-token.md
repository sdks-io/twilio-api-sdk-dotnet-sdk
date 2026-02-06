
# Accounts V1 Secondary Auth Token

*This model accepts additional fields of type object.*

## Structure

`AccountsV1SecondaryAuthToken`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that the secondary Auth Token was created for.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `DateCreated` | `DateTime?` | Optional | The date and time in UTC when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `DateUpdated` | `DateTime?` | Optional | The date and time in UTC when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `SecondaryAuthToken` | `string` | Optional | The generated secondary Auth Token that can be used to authenticate future API requests. |
| `Url` | `string` | Optional | The URI for this resource, relative to `https://accounts.twilio.com` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "account_sid": "account_sid6",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "secondary_auth_token": "secondary_auth_token8",
  "url": "url4",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

