# Accounts V1 Auth Token Promotion

```csharp
AccountsV1AuthTokenPromotionApi accountsV1AuthTokenPromotionApi = client.AccountsV1AuthTokenPromotionApi;
```

## Class Name

`AccountsV1AuthTokenPromotionApi`


# Update Auth Token Promotion

Promote the secondary Auth Token to primary. After promoting the new token, all requests to Twilio using your old primary Auth Token will result in an error.

```csharp
UpdateAuthTokenPromotionAsync()
```

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.AccountsV1AuthTokenPromotion](../../doc/models/accounts-v1-auth-token-promotion.md).

## Example Usage

```csharp
try
{
    ApiResponse<AccountsV1AuthTokenPromotion> result = await accountsV1AuthTokenPromotionApi.UpdateAuthTokenPromotionAsync();
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
  "auth_token": "bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb",
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "url": "https://accounts.twilio.com/v1/AuthTokens/Promote"
}
```

