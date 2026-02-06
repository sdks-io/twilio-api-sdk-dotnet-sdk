# Accounts V1 Safelist

```csharp
AccountsV1SafelistApi accountsV1SafelistApi = client.AccountsV1SafelistApi;
```

## Class Name

`AccountsV1SafelistApi`

## Methods

* [Create Safelist](../../doc/controllers/accounts-v1-safelist.md#create-safelist)
* [Fetch Safelist](../../doc/controllers/accounts-v1-safelist.md#fetch-safelist)
* [Delete Safelist](../../doc/controllers/accounts-v1-safelist.md#delete-safelist)


# Create Safelist

Add a new phone number or phone number 1k prefix to SafeList.

```csharp
CreateSafelistAsync(
    string phoneNumber)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `phoneNumber` | `string` | Form, Required | The phone number or phone number 1k prefix to be added in SafeList. Phone numbers must be in [E.164 format](https://www.twilio.com/docs/glossary/what-e164). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.AccountsV1Safelist](../../doc/models/accounts-v1-safelist.md).

## Example Usage

```csharp
string phoneNumber = "+18001234567";
try
{
    ApiResponse<AccountsV1Safelist> result = await accountsV1SafelistApi.CreateSafelistAsync(phoneNumber);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "GNaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "phone_number": "+18001234567"
}
```


# Fetch Safelist

Check if a phone number or phone number 1k prefix exists in SafeList.

```csharp
FetchSafelistAsync(
    string phoneNumber = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `phoneNumber` | `string` | Query, Optional | The phone number or phone number 1k prefix to be fetched from SafeList. Phone numbers must be in [E.164 format](https://www.twilio.com/docs/glossary/what-e164). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.AccountsV1Safelist](../../doc/models/accounts-v1-safelist.md).

## Example Usage

```csharp
string phoneNumber = "+18001234567";
try
{
    ApiResponse<AccountsV1Safelist> result = await accountsV1SafelistApi.FetchSafelistAsync(phoneNumber);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "GNaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "phone_number": "+18001234567"
}
```


# Delete Safelist

Remove a phone number or phone number 1k prefix from SafeList.

```csharp
DeleteSafelistAsync(
    string phoneNumber = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `phoneNumber` | `string` | Query, Optional | The phone number or phone number 1k prefix to be removed from SafeList. Phone numbers must be in [E.164 format](https://www.twilio.com/docs/glossary/what-e164). |

## Response Type

`Task`

## Example Usage

```csharp
string phoneNumber = "+18001234567";
try
{
    await accountsV1SafelistApi.DeleteSafelistAsync(phoneNumber);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

