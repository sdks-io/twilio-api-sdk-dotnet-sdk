# Accounts V1 Bulk Contacts

```csharp
AccountsV1BulkContactsApi accountsV1BulkContactsApi = client.AccountsV1BulkContactsApi;
```

## Class Name

`AccountsV1BulkContactsApi`


# Create Bulk Contacts

```csharp
CreateBulkContactsAsync(
    object items)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `items` | `object` | Form, Required | A list of objects where each object represents a contact's details. Each object includes the following fields: `contact_id`, which must be a string representing phone number in [E.164 format](https://www.twilio.com/docs/glossary/what-e164); `correlation_id`, a unique 32-character UUID that maps the response to the original request; `country_iso_code`, a string representing the country using the ISO format (e.g., US for the United States); and `zip_code`, a string representing the postal code. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.AccountsV1BulkContacts](../../doc/models/accounts-v1-bulk-contacts.md).

## Example Usage

```csharp
List<object> items = new List<object>
{
    ApiHelper.JsonDeserialize<object>("\"{\\\"contact_id\\\":\\\"+19999999999\\\",\\\"correlation_id\\\":\\\"ad388b5a46b33b874b0d41f7226db2eh\\\",\\\"country_iso_code\\\":\\\"US\\\",\\\"zip_code\\\":\\\"12345\\\"}\""),
    ApiHelper.JsonDeserialize<object>("\"{\\\"contact_id\\\":\\\"+19\\\",\\\"correlation_id\\\":\\\"02520cfa6c432f0e3ec3a38c122d428a\\\",\\\"country_iso_code\\\":\\\"US\\\",\\\"zip_code\\\":\\\"12345\\\"}\""),
};

try
{
    ApiResponse<AccountsV1BulkContacts> result = await accountsV1BulkContactsApi.CreateBulkContactsAsync(items);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

