
# Getting Started with Twilio APIs

## Introduction

This is the public Twilio REST API.

## Install the Package

If you are building with .NET CLI tools then you can also use the following command:

```bash
dotnet add package apimatic-twilio-sdk --version 1.0.9
```

You can also view the package at:
https://www.nuget.org/packages/apimatic-twilio-sdk/1.0.9

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| Environment | [`Environment`](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/README.md#environments) | The API environment. <br> **Default: `Environment.Production`** |
| Timeout | `TimeSpan` | Http client timeout.<br>*Default*: `TimeSpan.FromSeconds(30)` |
| HttpClientConfiguration | [`Action<HttpClientConfiguration.Builder>`](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/http-client-configuration-builder.md) | Action delegate that configures the HTTP client by using the HttpClientConfiguration.Builder for customizing API call settings.<br>*Default*: `new HttpClient()` |
| LogBuilder | [`LogBuilder`](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/log-builder.md) | Represents the logging configuration builder for API calls |
| BasicAuthCredentials | [`BasicAuthCredentials`](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/auth/basic-authentication.md) | The Credentials Setter for Basic Authentication |

The API client can be initialized as follows:

### Code-Based Initialization

```csharp
using Microsoft.Extensions.Logging;
using TwilioApIs.Standard;
using TwilioApIs.Standard.Authentication;

namespace ConsoleApp;

TwilioApIsClient client = new TwilioApIsClient.Builder()
    .BasicAuthCredentials(
        new BasicAuthModel.Builder(
            "BasicAuthUserName",
            "BasicAuthPassword"
        )
        .Build())
    .HttpClientConfig(httpClientConfig =>
        httpClientConfig.Timeout(TimeSpan.FromSeconds(100)))
    .Environment(TwilioApIs.Standard.Environment.Production)
    .LoggingConfig(config => config
        .LogLevel(LogLevel.Information)
        .RequestConfig(reqConfig => reqConfig.Body(true))
        .ResponseConfig(respConfig => respConfig.Headers(true))
    )
    .Build();
```

### Configuration-Based Initialization

```csharp
using TwilioApIs.Standard;
using Microsoft.Extensions.Configuration;

namespace ConsoleApp;

// Build the IConfiguration using .NET conventions (JSON, environment, etc.)
var configuration = new ConfigurationBuilder()
    .AddJsonFile("config.json")
    .AddEnvironmentVariables() // [optional] read environment variables
    .Build();

// Instantiate your SDK and configure it from IConfiguration
var client = TwilioApIsClient
    .FromConfiguration(configuration.GetSection("TwilioApIs"));
```

See the [Configuration-Based Initialization](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/configuration-based-initialization.md) section for details.

## Environments

The SDK can be configured to use a different environment for making API calls. Available environments are:

### Fields

| Name | Description |
|  --- | --- |
| Production | **Default** |

## Authorization

This API uses the following authentication schemes.

* [`accountSid_authToken (Basic Authentication)`](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/auth/basic-authentication.md)

## List of APIs

* [Accounts V1 Auth Token Promotion](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/accounts-v1-auth-token-promotion.md)
* [Accounts V1 Aws](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/accounts-v1-aws.md)
* [Accounts V1 Bulk Consents](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/accounts-v1-bulk-consents.md)
* [Accounts V1 Bulk Contacts](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/accounts-v1-bulk-contacts.md)
* [Accounts V1 Messaging Geopermissions](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/accounts-v1-messaging-geopermissions.md)
* [Accounts V1 Public Key](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/accounts-v1-public-key.md)
* [Accounts V1 Safelist](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/accounts-v1-safelist.md)
* [Accounts V1 Secondary Auth Token](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/accounts-v1-secondary-auth-token.md)
* [Chat V3 Channel](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/chat-v3-channel.md)
* [Conversations V1 Address Configuration](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-address-configuration.md)
* [Conversations V1 Binding](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-binding.md)
* [Conversations V1 Configuration](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-configuration.md)
* [Conversations V1 Conversation](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-conversation.md)
* [Conversations V1 Conversation with Participants](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-conversation-with-participants.md)
* [Conversations V1 Credential](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-credential.md)
* [Conversations V1 Delivery Receipt](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-delivery-receipt.md)
* [Conversations V1 Message](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-message.md)
* [Conversations V1 Notification](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-notification.md)
* [Conversations V1 Participant](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-participant.md)
* [Conversations V1 Participant Conversation](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-participant-conversation.md)
* [Conversations V1 Role](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-role.md)
* [Conversations V1 Service](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-service.md)
* [Conversations V1 User](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-user.md)
* [Conversations V1 User Conversation](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-user-conversation.md)
* [Conversations V1 Webhook](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/conversations-v1-webhook.md)
* [Notify V1 Binding](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/notify-v1-binding.md)
* [Notify V1 Credential](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/notify-v1-credential.md)
* [Notify V1 Notification](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/notify-v1-notification.md)
* [Notify V1 Service](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/notify-v1-service.md)
* [Taskrouter V1 Activity](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-activity.md)
* [Taskrouter V1 Event](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-event.md)
* [Taskrouter V1 Task](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-task.md)
* [Taskrouter V1 Task Channel](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-task-channel.md)
* [Taskrouter V1 Task Queue](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-task-queue.md)
* [Taskrouter V1 Task Queue Bulk Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-task-queue-bulk-real-time-statistics.md)
* [Taskrouter V1 Task Queue Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-task-queue-cumulative-statistics.md)
* [Taskrouter V1 Task Queue Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-task-queue-real-time-statistics.md)
* [Taskrouter V1 Task Queue Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-task-queue-statistics.md)
* [Taskrouter V1 Task Queues Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-task-queues-statistics.md)
* [Taskrouter V1 Task Reservation](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-task-reservation.md)
* [Taskrouter V1 Worker](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-worker.md)
* [Taskrouter V1 Worker Channel](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-worker-channel.md)
* [Taskrouter V1 Worker Reservation](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-worker-reservation.md)
* [Taskrouter V1 Worker Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-worker-statistics.md)
* [Taskrouter V1 Workers Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-workers-cumulative-statistics.md)
* [Taskrouter V1 Workers Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-workers-real-time-statistics.md)
* [Taskrouter V1 Workers Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-workers-statistics.md)
* [Taskrouter V1 Workflow](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-workflow.md)
* [Taskrouter V1 Workflow Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-workflow-cumulative-statistics.md)
* [Taskrouter V1 Workflow Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-workflow-real-time-statistics.md)
* [Taskrouter V1 Workflow Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-workflow-statistics.md)
* [Taskrouter V1 Workspace](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-workspace.md)
* [Taskrouter V1 Workspace Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-workspace-cumulative-statistics.md)
* [Taskrouter V1 Workspace Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-workspace-real-time-statistics.md)
* [Taskrouter V1 Workspace Statistics](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/taskrouter-v1-workspace-statistics.md)
* [Verify V2 Service](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/verify-v2-service.md)
* [Verify V2 Verification](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/verify-v2-verification.md)
* [Verify V2 Verification Check](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/verify-v2-verification-check.md)
* [SMS](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/controllers/sms.md)

## SDK Infrastructure

### Configuration

* [Configuration-Based Initialization](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/configuration-based-initialization.md)
* [HttpClientConfiguration](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/http-client-configuration.md)
* [HttpClientConfigurationBuilder](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/http-client-configuration-builder.md)
* [LogBuilder](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/log-builder.md)
* [LogRequestBuilder](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/log-request-builder.md)
* [LogResponseBuilder](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/log-response-builder.md)
* [ProxyConfigurationBuilder](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/proxy-configuration-builder.md)

### HTTP

* [HttpCallback](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/http-callback.md)
* [HttpContext](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/http-context.md)
* [HttpRequest](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/http-request.md)
* [HttpResponse](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/http-response.md)
* [HttpStringResponse](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/http-string-response.md)

### Utilities

* [ApiException](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/api-exception.md)
* [ApiResponse](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/api-response.md)
* [ApiHelper](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/api-helper.md)
* [CustomDateTimeConverter](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/custom-date-time-converter.md)
* [UnixDateTimeConverter](https://www.github.com/sdks-io/twilio-api-sdk-dotnet-sdk/tree/1.0.9/doc/unix-date-time-converter.md)

