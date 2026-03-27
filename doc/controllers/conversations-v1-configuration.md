# Conversations V1 Configuration

```csharp
ConversationsV1ConfigurationApi conversationsV1ConfigurationApi = client.ConversationsV1ConfigurationApi;
```

## Class Name

`ConversationsV1ConfigurationApi`

## Methods

* [Fetch Configuration](../../doc/controllers/conversations-v1-configuration.md#fetch-configuration)
* [Update Configuration](../../doc/controllers/conversations-v1-configuration.md#update-configuration)
* [Fetch Service Configuration](../../doc/controllers/conversations-v1-configuration.md#fetch-service-configuration)
* [Update Service Configuration](../../doc/controllers/conversations-v1-configuration.md#update-service-configuration)


# Fetch Configuration

Fetch the global configuration of conversations on your account

```csharp
FetchConfigurationAsync()
```

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Configuration](../../doc/models/configuration.md).

## Example Usage

```csharp
try
{
    ApiResponse<Configuration> result = await conversationsV1ConfigurationApi.FetchConfigurationAsync();
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
  "default_chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_inactive_timer": "PT1M",
  "default_closed_timer": "PT10M",
  "url": "https://conversations.twilio.com/v1/Configuration",
  "links": {
    "service": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
    "webhooks": "https://conversations.twilio.com/v1/Configuration/Webhooks"
  }
}
```


# Update Configuration

Update the global configuration of conversations on your account

```csharp
UpdateConfigurationAsync(
    string defaultChatServiceSid = null,
    string defaultMessagingServiceSid = null,
    string defaultInactiveTimer = null,
    string defaultClosedTimer = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `defaultChatServiceSid` | `string` | Form, Optional | The SID of the default [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to use when creating a conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `defaultMessagingServiceSid` | `string` | Form, Optional | The SID of the default [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) to use when creating a conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `defaultInactiveTimer` | `string` | Form, Optional | Default ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `defaultClosedTimer` | `string` | Form, Optional | Default ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Configuration](../../doc/models/configuration.md).

## Example Usage

```csharp
string defaultChatServiceSid = "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string defaultMessagingServiceSid = "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string defaultInactiveTimer = "PT1M";
string defaultClosedTimer = "PT10M";
try
{
    ApiResponse<Configuration> result = await conversationsV1ConfigurationApi.UpdateConfigurationAsync(
        defaultChatServiceSid,
        defaultMessagingServiceSid,
        defaultInactiveTimer,
        defaultClosedTimer
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
  "default_chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_inactive_timer": "PT1M",
  "default_closed_timer": "PT10M",
  "url": "https://conversations.twilio.com/v1/Configuration",
  "links": {
    "service": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
    "webhooks": "https://conversations.twilio.com/v1/Configuration/Webhooks"
  }
}
```


# Fetch Service Configuration

Fetch the configuration of a conversation service

```csharp
FetchServiceConfigurationAsync(
    string chatServiceSid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the Service configuration resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConfiguration](../../doc/models/service-configuration.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
try
{
    ApiResponse<ServiceConfiguration> result = await conversationsV1ConfigurationApi.FetchServiceConfigurationAsync(chatServiceSid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_creator_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_chat_service_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "reachability_enabled": false,
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
  "links": {
    "notifications": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Notifications",
    "webhooks": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
  }
}
```


# Update Service Configuration

Update configuration settings of a conversation service

```csharp
UpdateServiceConfigurationAsync(
    string chatServiceSid,
    string defaultConversationCreatorRoleSid = null,
    string defaultConversationRoleSid = null,
    string defaultChatServiceRoleSid = null,
    bool? reachabilityEnabled = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the Service configuration resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `defaultConversationCreatorRoleSid` | `string` | Form, Optional | The conversation-level role assigned to a conversation creator when they join a new conversation. See [Conversation Role](https://www.twilio.com/docs/conversations/api/role-resource) for more info about roles.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `defaultConversationRoleSid` | `string` | Form, Optional | The conversation-level role assigned to users when they are added to a conversation. See [Conversation Role](https://www.twilio.com/docs/conversations/api/role-resource) for more info about roles.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `defaultChatServiceRoleSid` | `string` | Form, Optional | The service-level role assigned to users when they are added to the service. See [Conversation Role](https://www.twilio.com/docs/conversations/api/role-resource) for more info about roles.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `reachabilityEnabled` | `bool?` | Form, Optional | Whether the [Reachability Indicator](https://www.twilio.com/docs/conversations/reachability) is enabled for this Conversations Service. The default is `false`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConfiguration](../../doc/models/service-configuration.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string defaultConversationCreatorRoleSid = "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string defaultConversationRoleSid = "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string defaultChatServiceRoleSid = "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
bool? reachabilityEnabled = false;
try
{
    ApiResponse<ServiceConfiguration> result = await conversationsV1ConfigurationApi.UpdateServiceConfigurationAsync(
        chatServiceSid,
        defaultConversationCreatorRoleSid,
        defaultConversationRoleSid,
        defaultChatServiceRoleSid,
        reachabilityEnabled
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
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_creator_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_chat_service_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "reachability_enabled": false,
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
  "links": {
    "notifications": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Notifications",
    "webhooks": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
  }
}
```

