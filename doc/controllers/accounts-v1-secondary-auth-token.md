# Accounts V1 Secondary Auth Token

```csharp
AccountsV1SecondaryAuthTokenApi accountsV1SecondaryAuthTokenApi = client.AccountsV1SecondaryAuthTokenApi;
```

## Class Name

`AccountsV1SecondaryAuthTokenApi`

## Methods

* [Create Secondary Auth Token](../../doc/controllers/accounts-v1-secondary-auth-token.md#create-secondary-auth-token)
* [Delete Secondary Auth Token](../../doc/controllers/accounts-v1-secondary-auth-token.md#delete-secondary-auth-token)


# Create Secondary Auth Token

Create a new secondary Auth Token

```csharp
CreateSecondaryAuthTokenAsync()
```

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.AccountsV1SecondaryAuthToken](../../doc/models/accounts-v1-secondary-auth-token.md).

## Example Usage

```csharp
try
{
    ApiResponse<AccountsV1SecondaryAuthToken> result = await accountsV1SecondaryAuthTokenApi.CreateSecondaryAuthTokenAsync();
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "secondary_auth_token": "bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb",
  "url": "https://accounts.twilio.com/v1/AuthTokens/Secondary"
}
```


# Delete Secondary Auth Token

Delete the secondary Auth Token from your account

```csharp
DeleteSecondaryAuthTokenAsync()
```

## Response Type

`Task`

## Example Usage

```csharp
try
{
    await accountsV1SecondaryAuthTokenApi.DeleteSecondaryAuthTokenAsync();
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

