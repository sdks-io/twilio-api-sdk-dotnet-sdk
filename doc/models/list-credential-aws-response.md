
# List Credential Aws Response

*This model accepts additional fields of type object.*

## Structure

`ListCredentialAwsResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Credentials` | [`List<AccountsV1CredentialCredentialAws>`](../../doc/models/accounts-v1-credential-credential-aws.md) | Optional | - |
| `Meta` | [`Meta`](../../doc/models/meta.md) | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "credentials": [
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

