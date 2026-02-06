# Accounts V1 Messaging Geopermissions

```csharp
AccountsV1MessagingGeopermissionsApi accountsV1MessagingGeopermissionsApi = client.AccountsV1MessagingGeopermissionsApi;
```

## Class Name

`AccountsV1MessagingGeopermissionsApi`

## Methods

* [Update Messaging Geopermissions](../../doc/controllers/accounts-v1-messaging-geopermissions.md#update-messaging-geopermissions)
* [Fetch Messaging Geopermissions](../../doc/controllers/accounts-v1-messaging-geopermissions.md#fetch-messaging-geopermissions)


# Update Messaging Geopermissions

Manage Geo Permissions for each country.

```csharp
UpdateMessagingGeopermissionsAsync(
    object permissions)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `permissions` | `object` | Form, Required | A list of objects where each object represents the Geo Permission to be updated. Each object contains the following fields: `country_code`, unique code for each country of Geo Permission; `type`, permission type of the Geo Permission i.e. country; `enabled`, configure true for enabling the Geo Permission, false for disabling the Geo Permission. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.AccountsV1MessagingGeopermissions](../../doc/models/accounts-v1-messaging-geopermissions.md).

## Example Usage

```csharp
List<object> permissions = new List<object>
{
    ApiHelper.JsonDeserialize<object>("\"{\\\"country_code\\\": \\\"IN\\\",\\\"type\\\": \\\"country\\\", \\\"enabled\\\": false}\""),
    ApiHelper.JsonDeserialize<object>("\"{\\\"country_code\\\": \\\"PK\\\",\\\"type\\\": \\\"country\\\", \\\"enabled\\\": true}\""),
};

try
{
    ApiResponse<AccountsV1MessagingGeopermissions> result = await accountsV1MessagingGeopermissionsApi.UpdateMessagingGeopermissionsAsync(permissions);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Messaging Geopermissions

Manage Geo Permissions for each country.

```csharp
FetchMessagingGeopermissionsAsync(
    string countryCode = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `countryCode` | `string` | Query, Optional | The country code to filter the geo permissions. If provided, only the geo permission for the specified country will be returned. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.AccountsV1MessagingGeopermissions](../../doc/models/accounts-v1-messaging-geopermissions.md).

## Example Usage

```csharp
string countryCode = "IN,PK,US";
try
{
    ApiResponse<AccountsV1MessagingGeopermissions> result = await accountsV1MessagingGeopermissionsApi.FetchMessagingGeopermissionsAsync(countryCode);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

