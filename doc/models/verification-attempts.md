
# Verification Attempts

*This model accepts additional fields of type object.*

## Structure

`VerificationAttempts`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `TotalAttempts` | `int?` | Optional | Total of attempts made according to the provided filters<br><br>**Default**: `0` |
| `TotalConverted` | `int?` | Optional | Total of  attempts made that were confirmed by the end user, according to the provided filters.<br><br>**Default**: `0` |
| `TotalUnconverted` | `int?` | Optional | Total of attempts made that were not confirmed by the end user, according to the provided filters.<br><br>**Default**: `0` |
| `ConversionRatePercentage` | `string` | Optional | Percentage of the confirmed messages over the total, defined by (total_converted/total_attempts)*100. |
| `Url` | `string` | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "total_attempts": 0,
  "total_converted": 0,
  "total_unconverted": 0,
  "conversion_rate_percentage": "conversion_rate_percentage2",
  "url": "url6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

