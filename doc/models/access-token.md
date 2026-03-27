
# Access Token

*This model accepts additional fields of type object.*

## Structure

`AccessToken`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Sid` | `string` | Optional | A 34 character string that uniquely identifies this Access Token.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^YK[0-9a-fA-F]{32}$` |
| `AccountSid` | `string` | Optional | The unique SID identifier of the Account.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `ServiceSid` | `string` | Optional | The unique SID identifier of the Verify Service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` |
| `EntityIdentity` | `string` | Optional | The unique external identifier for the Entity of the Service. |
| `FactorType` | [`AccessTokenEnumFactorTypes?`](../../doc/models/access-token-enum-factor-types.md) | Optional | The Type of the Factor. Currently only `push` is supported. |
| `FactorFriendlyName` | `string` | Optional | A human readable description of this factor, up to 64 characters. For a push factor, this can be the device's name. |
| `Token` | `string` | Optional | The access token generated for enrollment, this is an encrypted json web token. |
| `Url` | `string` | Optional | The URL of this resource. |
| `Ttl` | `int?` | Optional | How long, in seconds, the access token is valid. Max: 5 minutes<br><br>**Default**: `0` |
| `DateCreated` | `DateTime?` | Optional | The date that this access token was created, given in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "ttl": 0,
  "sid": "sid8",
  "account_sid": "account_sid6",
  "service_sid": "service_sid2",
  "entity_identity": "entity_identity0",
  "factor_type": "push",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

