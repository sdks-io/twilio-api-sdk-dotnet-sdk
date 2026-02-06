# Accounts V1 Aws

```csharp
AccountsV1AwsApi accountsV1AwsApi = client.AccountsV1AwsApi;
```

## Class Name

`AccountsV1AwsApi`

## Methods

* [List Credential Aws](../../doc/controllers/accounts-v1-aws.md#list-credential-aws)
* [Create Credential Aws](../../doc/controllers/accounts-v1-aws.md#create-credential-aws)
* [Fetch Credential Aws](../../doc/controllers/accounts-v1-aws.md#fetch-credential-aws)
* [Update Credential Aws](../../doc/controllers/accounts-v1-aws.md#update-credential-aws)
* [Delete Credential Aws](../../doc/controllers/accounts-v1-aws.md#delete-credential-aws)


# List Credential Aws

Retrieves a collection of AWS Credentials belonging to the account used to make the request

```csharp
ListCredentialAwsAsync(
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListCredentialAwsResponse](../../doc/models/list-credential-aws-response.md).

## Example Usage

```csharp
try
{
    ApiResponse<ListCredentialAwsResponse> result = await accountsV1AwsApi.ListCredentialAwsAsync();
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "credentials": [],
  "meta": {
    "first_page_url": "https://accounts.twilio.com/v1/Credentials/AWS?PageSize=50&Page=0",
    "key": "credentials",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://accounts.twilio.com/v1/Credentials/AWS?PageSize=50&Page=0"
  }
}
```


# Create Credential Aws

Create a new AWS Credential

```csharp
CreateCredentialAwsAsync(
    string credentials,
    string friendlyName = null,
    string accountSid = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `credentials` | `string` | Form, Required | A string that contains the AWS access credentials in the format `<AWS_ACCESS_KEY_ID>:<AWS_SECRET_ACCESS_KEY>`. For example, `AKIAIOSFODNN7EXAMPLE:wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY` |
| `friendlyName` | `string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |
| `accountSid` | `string` | Form, Optional | The SID of the Subaccount that this Credential should be associated with. Must be a valid Subaccount of the account issuing the request.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.AccountsV1CredentialCredentialAws](../../doc/models/accounts-v1-credential-credential-aws.md).

## Example Usage

```csharp
string credentials = "aws_credentials";
string friendlyName = "friendly_name";
string accountSid = "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
try
{
    ApiResponse<AccountsV1CredentialCredentialAws> result = await accountsV1AwsApi.CreateCredentialAwsAsync(
        credentials,
        friendlyName,
        accountSid
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
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "friendly_name": "friendly_name",
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://accounts.twilio.com/v1/Credentials/AWS/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Fetch Credential Aws

Fetch the AWS credentials specified by the provided Credential Sid

```csharp
FetchCredentialAwsAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the AWS resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.AccountsV1CredentialCredentialAws](../../doc/models/accounts-v1-credential-credential-aws.md).

## Example Usage

```csharp
string sid = "Sid8";
try
{
    ApiResponse<AccountsV1CredentialCredentialAws> result = await accountsV1AwsApi.FetchCredentialAwsAsync(sid);
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
  "friendly_name": "friendly_name",
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://accounts.twilio.com/v1/Credentials/AWS/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Update Credential Aws

Modify the properties of a given Account

```csharp
UpdateCredentialAwsAsync(
    string sid,
    string friendlyName = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the AWS resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `friendlyName` | `string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.AccountsV1CredentialCredentialAws](../../doc/models/accounts-v1-credential-credential-aws.md).

## Example Usage

```csharp
string sid = "Sid8";
string friendlyName = "friendly_name";
try
{
    ApiResponse<AccountsV1CredentialCredentialAws> result = await accountsV1AwsApi.UpdateCredentialAwsAsync(
        sid,
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
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "friendly_name": "friendly_name",
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://accounts.twilio.com/v1/Credentials/AWS/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Credential Aws

Delete a Credential from your account

```csharp
DeleteCredentialAwsAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the AWS resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

`Task`

## Example Usage

```csharp
string sid = "Sid8";
try
{
    await accountsV1AwsApi.DeleteCredentialAwsAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

