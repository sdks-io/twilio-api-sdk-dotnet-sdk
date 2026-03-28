
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| Environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.Production`** |
| Timeout | `TimeSpan` | Http client timeout.<br>*Default*: `TimeSpan.FromSeconds(30)` |
| HttpClientConfiguration | [`Action<HttpClientConfiguration.Builder>`](../doc/http-client-configuration-builder.md) | Action delegate that configures the HTTP client by using the HttpClientConfiguration.Builder for customizing API call settings.<br>*Default*: `new HttpClient()` |
| LogBuilder | [`LogBuilder`](../doc/log-builder.md) | Represents the logging configuration builder for API calls |
| BasicAuthCredentials | [`BasicAuthCredentials`](auth/basic-authentication.md) | The Credentials Setter for Basic Authentication |

The API client can be initialized as follows:

## Code-Based Initialization

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

## Configuration-Based Initialization

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

See the [Configuration-Based Initialization](../doc/configuration-based-initialization.md) section for details.

## Twilio APIsClient Class

The gateway for the SDK. This class acts as a factory for the Apis and also holds the configuration of the SDK.

### Controllers

| Name | Description |
|  --- | --- |
| AccountsV1AuthTokenPromotionApi | Gets AccountsV1AuthTokenPromotionApi. |
| AccountsV1AwsApi | Gets AccountsV1AwsApi. |
| AccountsV1BulkConsentsApi | Gets AccountsV1BulkConsentsApi. |
| AccountsV1BulkContactsApi | Gets AccountsV1BulkContactsApi. |
| AccountsV1MessagingGeopermissionsApi | Gets AccountsV1MessagingGeopermissionsApi. |
| AccountsV1PublicKeyApi | Gets AccountsV1PublicKeyApi. |
| AccountsV1SafelistApi | Gets AccountsV1SafelistApi. |
| AccountsV1SecondaryAuthTokenApi | Gets AccountsV1SecondaryAuthTokenApi. |
| ChatV3ChannelApi | Gets ChatV3ChannelApi. |
| ConversationsV1AddressConfigurationApi | Gets ConversationsV1AddressConfigurationApi. |
| ConversationsV1BindingApi | Gets ConversationsV1BindingApi. |
| ConversationsV1ConfigurationApi | Gets ConversationsV1ConfigurationApi. |
| ConversationsV1ConversationApi | Gets ConversationsV1ConversationApi. |
| ConversationsV1ConversationWithParticipantsApi | Gets ConversationsV1ConversationWithParticipantsApi. |
| ConversationsV1CredentialApi | Gets ConversationsV1CredentialApi. |
| ConversationsV1DeliveryReceiptApi | Gets ConversationsV1DeliveryReceiptApi. |
| ConversationsV1MessageApi | Gets ConversationsV1MessageApi. |
| ConversationsV1NotificationApi | Gets ConversationsV1NotificationApi. |
| ConversationsV1ParticipantApi | Gets ConversationsV1ParticipantApi. |
| ConversationsV1ParticipantConversationApi | Gets ConversationsV1ParticipantConversationApi. |
| ConversationsV1RoleApi | Gets ConversationsV1RoleApi. |
| ConversationsV1ServiceApi | Gets ConversationsV1ServiceApi. |
| ConversationsV1UserApi | Gets ConversationsV1UserApi. |
| ConversationsV1UserConversationApi | Gets ConversationsV1UserConversationApi. |
| ConversationsV1WebhookApi | Gets ConversationsV1WebhookApi. |
| NotifyV1BindingApi | Gets NotifyV1BindingApi. |
| NotifyV1CredentialApi | Gets NotifyV1CredentialApi. |
| NotifyV1NotificationApi | Gets NotifyV1NotificationApi. |
| NotifyV1ServiceApi | Gets NotifyV1ServiceApi. |
| TaskrouterV1ActivityApi | Gets TaskrouterV1ActivityApi. |
| TaskrouterV1EventApi | Gets TaskrouterV1EventApi. |
| TaskrouterV1TaskApi | Gets TaskrouterV1TaskApi. |
| TaskrouterV1TaskChannelApi | Gets TaskrouterV1TaskChannelApi. |
| TaskrouterV1TaskQueueApi | Gets TaskrouterV1TaskQueueApi. |
| TaskrouterV1TaskQueueBulkRealTimeStatisticsApi | Gets TaskrouterV1TaskQueueBulkRealTimeStatisticsApi. |
| TaskrouterV1TaskQueueCumulativeStatisticsApi | Gets TaskrouterV1TaskQueueCumulativeStatisticsApi. |
| TaskrouterV1TaskQueueRealTimeStatisticsApi | Gets TaskrouterV1TaskQueueRealTimeStatisticsApi. |
| TaskrouterV1TaskQueueStatisticsApi | Gets TaskrouterV1TaskQueueStatisticsApi. |
| TaskrouterV1TaskQueuesStatisticsApi | Gets TaskrouterV1TaskQueuesStatisticsApi. |
| TaskrouterV1TaskReservationApi | Gets TaskrouterV1TaskReservationApi. |
| TaskrouterV1WorkerApi | Gets TaskrouterV1WorkerApi. |
| TaskrouterV1WorkerChannelApi | Gets TaskrouterV1WorkerChannelApi. |
| TaskrouterV1WorkerReservationApi | Gets TaskrouterV1WorkerReservationApi. |
| TaskrouterV1WorkerStatisticsApi | Gets TaskrouterV1WorkerStatisticsApi. |
| TaskrouterV1WorkersCumulativeStatisticsApi | Gets TaskrouterV1WorkersCumulativeStatisticsApi. |
| TaskrouterV1WorkersRealTimeStatisticsApi | Gets TaskrouterV1WorkersRealTimeStatisticsApi. |
| TaskrouterV1WorkersStatisticsApi | Gets TaskrouterV1WorkersStatisticsApi. |
| TaskrouterV1WorkflowApi | Gets TaskrouterV1WorkflowApi. |
| TaskrouterV1WorkflowCumulativeStatisticsApi | Gets TaskrouterV1WorkflowCumulativeStatisticsApi. |
| TaskrouterV1WorkflowRealTimeStatisticsApi | Gets TaskrouterV1WorkflowRealTimeStatisticsApi. |
| TaskrouterV1WorkflowStatisticsApi | Gets TaskrouterV1WorkflowStatisticsApi. |
| TaskrouterV1WorkspaceApi | Gets TaskrouterV1WorkspaceApi. |
| TaskrouterV1WorkspaceCumulativeStatisticsApi | Gets TaskrouterV1WorkspaceCumulativeStatisticsApi. |
| TaskrouterV1WorkspaceRealTimeStatisticsApi | Gets TaskrouterV1WorkspaceRealTimeStatisticsApi. |
| TaskrouterV1WorkspaceStatisticsApi | Gets TaskrouterV1WorkspaceStatisticsApi. |
| VerifyV2ServiceApi | Gets VerifyV2ServiceApi. |
| VerifyV2VerificationApi | Gets VerifyV2VerificationApi. |
| VerifyV2VerificationCheckApi | Gets VerifyV2VerificationCheckApi. |
| SmsApi | Gets SmsApi. |

### Properties

| Name | Description | Type |
|  --- | --- | --- |
| HttpClientConfiguration | Gets the configuration of the Http Client associated with this client. | [`IHttpClientConfiguration`](../doc/http-client-configuration.md) |
| Timeout | Http client timeout. | `TimeSpan` |
| Environment | Current API environment. | `Environment` |
| BasicAuthCredentials | Gets the credentials to use with BasicAuth. | [`IBasicAuthCredentials`](auth/basic-authentication.md) |

### Methods

| Name | Description | Return Type |
|  --- | --- | --- |
| `GetBaseUri(Server alias = Server.Default)` | Gets the URL for a particular alias in the current environment and appends it with template parameters. | `string` |
| `ToBuilder()` | Creates an object of the Twilio APIsClient using the values provided for the builder. | `Builder` |

## Twilio APIsClient Builder Class

Class to build instances of Twilio APIsClient.

### Methods

| Name | Description | Return Type |
|  --- | --- | --- |
| `HttpClientConfiguration(Action<`[`HttpClientConfiguration.Builder`](../doc/http-client-configuration-builder.md)`> action)` | Gets the configuration of the Http Client associated with this client. | `Builder` |
| `Timeout(TimeSpan timeout)` | Http client timeout. | `Builder` |
| `Environment(Environment environment)` | Current API environment. | `Builder` |
| `BasicAuthCredentials(Action<BasicAuthModel.Builder> action)` | Sets credentials for BasicAuth. | `Builder` |

