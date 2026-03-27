
# Bucket

*This model accepts additional fields of type object.*

## Structure

`Bucket`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Sid` | `string` | Optional | A 34 character string that uniquely identifies this Bucket.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^BL[0-9a-fA-F]{32}$` |
| `RateLimitSid` | `string` | Optional | The Twilio-provided string that uniquely identifies the Rate Limit resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RK[0-9a-fA-F]{32}$` |
| `ServiceSid` | `string` | Optional | The SID of the [Service](https://www.twilio.com/docs/verify/api/service) the resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` |
| `AccountSid` | `string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Rate Limit resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `Max` | `int?` | Optional | Maximum number of requests permitted in during the interval.<br><br>**Default**: `0` |
| `Interval` | `int?` | Optional | Number of seconds that the rate limit will be enforced over.<br><br>**Default**: `0` |
| `DateCreated` | `DateTime?` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. |
| `DateUpdated` | `DateTime?` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. |
| `Url` | `string` | Optional | The URL of this resource. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "max": 0,
  "interval": 0,
  "sid": "sid6",
  "rate_limit_sid": "rate_limit_sid0",
  "service_sid": "service_sid0",
  "account_sid": "account_sid8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

