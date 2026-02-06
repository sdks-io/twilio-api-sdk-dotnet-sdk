
# Getting Started with Twilio - Accounts

## Introduction

This is the public Twilio REST API.

## Install the Package

If you are building with .NET CLI tools then you can also use the following command:

```bash
dotnet add package TwilioApiSdkSDK-apimatic --version 1.0.1
```

You can also view the package at:
https://www.nuget.org/packages/TwilioApiSdkSDK-apimatic/1.0.1

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| Timeout | `TimeSpan` | Http client timeout.<br>*Default*: `TimeSpan.FromSeconds(30)` |
| HttpClientConfiguration | [`Action<HttpClientConfiguration.Builder>`](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/http-client-configuration-builder.md) | Action delegate that configures the HTTP client by using the HttpClientConfiguration.Builder for customizing API call settings.<br>*Default*: `new HttpClient()` |
| LogBuilder | [`LogBuilder`](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/log-builder.md) | Represents the logging configuration builder for API calls |
| BasicAuthCredentials | [`BasicAuthCredentials`](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/auth/basic-authentication.md) | The Credentials Setter for Basic Authentication |

The API client can be initialized as follows:

### Code-Based Initialization

```csharp
using Microsoft.Extensions.Logging;
using TwilioAccounts.Standard;
using TwilioAccounts.Standard.Authentication;

namespace ConsoleApp;

TwilioAccountsClient client = new TwilioAccountsClient.Builder()
    .BasicAuthCredentials(
        new BasicAuthModel.Builder(
            "BasicAuthUserName",
            "BasicAuthPassword"
        )
        .Build())
    .HttpClientConfig(httpClientConfig =>
        httpClientConfig.Timeout(TimeSpan.FromSeconds(100)))
    .LoggingConfig(config => config
        .LogLevel(LogLevel.Information)
        .RequestConfig(reqConfig => reqConfig.Body(true))
        .ResponseConfig(respConfig => respConfig.Headers(true))
    )
    .Build();
```

### Configuration-Based Initialization

```csharp
using TwilioAccounts.Standard;
using Microsoft.Extensions.Configuration;

namespace ConsoleApp;

// Build the IConfiguration using .NET conventions (JSON, environment, etc.)
var configuration = new ConfigurationBuilder()
    .AddJsonFile("config.json")
    .AddEnvironmentVariables() // [optional] read environment variables
    .Build();

// Instantiate your SDK and configure it from IConfiguration
var client = TwilioAccountsClient
    .FromConfiguration(configuration.GetSection("TwilioAccounts"));
```

See the [Configuration-Based Initialization](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/configuration-based-initialization.md) section for details.

## Authorization

This API uses the following authentication schemes.

* [`accountSid_authToken (Basic Authentication)`](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/auth/basic-authentication.md)

## List of APIs

* [Accounts V1 Auth Token Promotion](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/controllers/accounts-v1-auth-token-promotion.md)
* [Accounts V1 Aws](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/controllers/accounts-v1-aws.md)
* [Accounts V1 Bulk Consents](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/controllers/accounts-v1-bulk-consents.md)
* [Accounts V1 Bulk Contacts](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/controllers/accounts-v1-bulk-contacts.md)
* [Accounts V1 Messaging Geopermissions](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/controllers/accounts-v1-messaging-geopermissions.md)
* [Accounts V1 Public Key](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/controllers/accounts-v1-public-key.md)
* [Accounts V1 Safelist](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/controllers/accounts-v1-safelist.md)
* [Accounts V1 Secondary Auth Token](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/controllers/accounts-v1-secondary-auth-token.md)

## SDK Infrastructure

### Configuration

* [Configuration-Based Initialization](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/configuration-based-initialization.md)
* [HttpClientConfiguration](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/http-client-configuration.md)
* [HttpClientConfigurationBuilder](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/http-client-configuration-builder.md)
* [LogBuilder](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/log-builder.md)
* [LogRequestBuilder](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/log-request-builder.md)
* [LogResponseBuilder](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/log-response-builder.md)
* [ProxyConfigurationBuilder](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/proxy-configuration-builder.md)

### HTTP

* [HttpCallback](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/http-callback.md)
* [HttpContext](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/http-context.md)
* [HttpRequest](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/http-request.md)
* [HttpResponse](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/http-response.md)
* [HttpStringResponse](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/http-string-response.md)

### Utilities

* [ApiException](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/api-exception.md)
* [ApiResponse](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/api-response.md)
* [ApiHelper](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/api-helper.md)
* [CustomDateTimeConverter](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/custom-date-time-converter.md)
* [UnixDateTimeConverter](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.1/doc/unix-date-time-converter.md)

