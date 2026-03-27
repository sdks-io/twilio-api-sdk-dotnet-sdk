# Conversations V1 Credential

```csharp
ConversationsV1CredentialApi conversationsV1CredentialApi = client.ConversationsV1CredentialApi;
```

## Class Name

`ConversationsV1CredentialApi`

## Methods

* [Create Credential](../../doc/controllers/conversations-v1-credential.md#create-credential)
* [List Credential](../../doc/controllers/conversations-v1-credential.md#list-credential)
* [Update Credential](../../doc/controllers/conversations-v1-credential.md#update-credential)
* [Delete Credential](../../doc/controllers/conversations-v1-credential.md#delete-credential)
* [Fetch Credential](../../doc/controllers/conversations-v1-credential.md#fetch-credential)


# Create Credential

Add a new push notification credential to your account

```csharp
CreateCredentialAsync(
    Models.CredentialPushType type,
    string friendlyName = null,
    string certificate = null,
    string privateKey = null,
    bool? sandbox = null,
    string apiKey = null,
    string secret = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | [`CredentialPushType`](../../doc/models/credential-push-type.md) | Form, Required | The type of push-notification service the credential is for. Can be: `fcm`, `gcm`, or `apn`. |
| `friendlyName` | `string` | Form, Optional | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `certificate` | `string` | Form, Optional | [APN only] The URL encoded representation of the certificate. For example,<br>`-----BEGIN CERTIFICATE----- MIIFnTCCBIWgAwIBAgIIAjy9H849+E8wDQYJKoZIhvcNAQEF.....A== -----END CERTIFICATE-----`. |
| `privateKey` | `string` | Form, Optional | [APN only] The URL encoded representation of the private key. For example,<br>`-----BEGIN RSA PRIVATE KEY----- MIIEpQIBAAKCAQEAuyf/lNrH9ck8DmNyo3fG... -----END RSA PRIVATE KEY-----`. |
| `sandbox` | `bool?` | Form, Optional | [APN only] Whether to send the credential to sandbox APNs. Can be `true` to send to sandbox APNs or `false` to send to production. |
| `apiKey` | `string` | Form, Optional | [GCM only] The API key for the project that was obtained from the Google Developer console for your GCM Service application credential. |
| `secret` | `string` | Form, Optional | [FCM only] The **Server key** of your project from the Firebase console, found under Settings / Cloud messaging. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Credential](../../doc/models/credential.md).

## Example Usage

```csharp
CredentialPushType type = CredentialPushType.Apn;
try
{
    ApiResponse<Credential> result = await conversationsV1CredentialApi.CreateCredentialAsync(type);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Test slow create",
  "type": "apn",
  "sandbox": "False",
  "date_created": "2015-10-07T17:50:01Z",
  "date_updated": "2015-10-07T17:50:01Z",
  "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Credential

Retrieve a list of all push notification credentials on your account

```csharp
ListCredentialAsync(
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListCredentialResponse](../../doc/models/list-credential-response.md).

## Example Usage

```csharp
try
{
    ApiResponse<ListCredentialResponse> result = await conversationsV1CredentialApi.ListCredentialAsync();
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "credentials": [
    {
      "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Test slow create",
      "type": "apn",
      "sandbox": "False",
      "date_created": "2015-10-07T17:50:01Z",
      "date_updated": "2015-10-07T17:50:01Z",
      "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ],
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Credentials?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Credentials?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "credentials"
  }
}
```


# Update Credential

Update an existing push notification credential on your account

```csharp
UpdateCredentialAsync(
    string sid,
    Models.CredentialPushType? type = null,
    string friendlyName = null,
    string certificate = null,
    string privateKey = null,
    bool? sandbox = null,
    string apiKey = null,
    string secret = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `type` | [`CredentialPushType?`](../../doc/models/credential-push-type.md) | Form, Optional | The type of push-notification service the credential is for. Can be: `fcm`, `gcm`, or `apn`. |
| `friendlyName` | `string` | Form, Optional | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `certificate` | `string` | Form, Optional | [APN only] The URL encoded representation of the certificate. For example,<br>`-----BEGIN CERTIFICATE----- MIIFnTCCBIWgAwIBAgIIAjy9H849+E8wDQYJKoZIhvcNAQEF.....A== -----END CERTIFICATE-----`. |
| `privateKey` | `string` | Form, Optional | [APN only] The URL encoded representation of the private key. For example,<br>`-----BEGIN RSA PRIVATE KEY----- MIIEpQIBAAKCAQEAuyf/lNrH9ck8DmNyo3fG... -----END RSA PRIVATE KEY-----`. |
| `sandbox` | `bool?` | Form, Optional | [APN only] Whether to send the credential to sandbox APNs. Can be `true` to send to sandbox APNs or `false` to send to production. |
| `apiKey` | `string` | Form, Optional | [GCM only] The API key for the project that was obtained from the Google Developer console for your GCM Service application credential. |
| `secret` | `string` | Form, Optional | [FCM only] The **Server key** of your project from the Firebase console, found under Settings / Cloud messaging. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Credential](../../doc/models/credential.md).

## Example Usage

```csharp
string sid = "Sid8";
string friendlyName = "Test slow create";
try
{
    ApiResponse<Credential> result = await conversationsV1CredentialApi.UpdateCredentialAsync(
        sid,
        null,
        friendlyName
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Test slow create",
  "type": "apn",
  "sandbox": "False",
  "date_created": "2015-10-07T17:50:01Z",
  "date_updated": "2015-10-07T17:50:01Z",
  "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Credential

Remove a push notification credential from your account

```csharp
DeleteCredentialAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

`Task`

## Example Usage

```csharp
string sid = "Sid8";
try
{
    await conversationsV1CredentialApi.DeleteCredentialAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Credential

Fetch a push notification credential from your account

```csharp
FetchCredentialAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Credential](../../doc/models/credential.md).

## Example Usage

```csharp
string sid = "Sid8";
try
{
    ApiResponse<Credential> result = await conversationsV1CredentialApi.FetchCredentialAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Test slow create",
  "type": "apn",
  "sandbox": "False",
  "date_created": "2015-10-07T17:50:01Z",
  "date_updated": "2015-10-07T17:50:01Z",
  "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

