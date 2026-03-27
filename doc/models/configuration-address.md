
# Configuration Address

*This model accepts additional fields of type object.*

## Structure

`ConfigurationAddress`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Sid` | `string` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IG[0-9a-fA-F]{32}$` |
| `AccountSid` | `string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) the address belongs to<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `Type` | `string` | Optional | Type of Address, value can be `whatsapp` or `sms`. |
| `Address` | `string` | Optional | The unique address to be configured. The address can be a whatsapp address or phone number |
| `FriendlyName` | `string` | Optional | The human-readable name of this configuration, limited to 256 characters. Optional. |
| `AutoCreation` | `object` | Optional | Auto Creation configuration for the address. |
| `DateCreated` | `DateTime?` | Optional | The date that this resource was created. |
| `DateUpdated` | `DateTime?` | Optional | The date that this resource was last updated. |
| `Url` | `string` | Optional | An absolute API resource URL for this address configuration. |
| `AddressCountry` | `string` | Optional | An ISO 3166-1 alpha-2n country code which the address belongs to. This is currently only applicable to short code addresses. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "sid": "sid4",
  "account_sid": "account_sid8",
  "type": "type8",
  "address": "address8",
  "friendly_name": "friendly_name8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

