
# Accounts V1 Credential Credential Aws

*This model accepts additional fields of type object.*

## Structure

`AccountsV1CredentialCredentialAws`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Sid` | `string` | Optional | The unique string that we created to identify the AWS resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the AWS resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `FriendlyName` | `string` | Optional | The string that you assigned to describe the resource. |
| `DateCreated` | `DateTime?` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. |
| `DateUpdated` | `DateTime?` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. |
| `Url` | `string` | Optional | The URI for this resource, relative to `https://accounts.twilio.com` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "sid": "sid2",
  "account_sid": "account_sid2",
  "friendly_name": "friendly_name8",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

