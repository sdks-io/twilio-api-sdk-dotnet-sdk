# Conversations V1 Webhook

```csharp
ConversationsV1WebhookApi conversationsV1WebhookApi = client.ConversationsV1WebhookApi;
```

## Class Name

`ConversationsV1WebhookApi`

## Methods

* [Fetch Configuration Webhook](../../doc/controllers/conversations-v1-webhook.md#fetch-configuration-webhook)
* [Update Configuration Webhook](../../doc/controllers/conversations-v1-webhook.md#update-configuration-webhook)
* [List Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#list-conversation-scoped-webhook)
* [Create Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#create-conversation-scoped-webhook)
* [Fetch Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#fetch-conversation-scoped-webhook)
* [Update Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#update-conversation-scoped-webhook)
* [Delete Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#delete-conversation-scoped-webhook)
* [Create Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#create-service-conversation-scoped-webhook)
* [List Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#list-service-conversation-scoped-webhook)
* [Update Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#update-service-conversation-scoped-webhook)
* [Delete Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#delete-service-conversation-scoped-webhook)
* [Fetch Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#fetch-service-conversation-scoped-webhook)
* [Update Service Webhook Configuration](../../doc/controllers/conversations-v1-webhook.md#update-service-webhook-configuration)
* [Fetch Service Webhook Configuration](../../doc/controllers/conversations-v1-webhook.md#fetch-service-webhook-configuration)


# Fetch Configuration Webhook

A Webhook resource manages a service-level set of callback URLs and their configuration for receiving all conversation events.

```csharp
FetchConfigurationWebhookAsync()
```

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConfigurationWebhook](../../doc/models/configuration-webhook.md).

## Example Usage

```csharp
try
{
    ApiResponse<ConfigurationWebhook> result = await conversationsV1WebhookApi.FetchConfigurationWebhookAsync();
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
  "pre_webhook_url": "https://example.com/pre",
  "post_webhook_url": "https://example.com/post",
  "method": "GET",
  "filters": [
    "onMessageSend",
    "onConversationUpdated"
  ],
  "target": "webhook",
  "url": "https://conversations.twilio.com/v1/Configuration/Webhooks"
}
```


# Update Configuration Webhook

A Webhook resource manages a service-level set of callback URLs and their configuration for receiving all conversation events.

```csharp
UpdateConfigurationWebhookAsync(
    string method = null,
    List<string> filters = null,
    string preWebhookUrl = null,
    string postWebhookUrl = null,
    Models.ConfigurationWebhookTarget? target = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `method` | `string` | Form, Optional | The HTTP method to be used when sending a webhook request. |
| `filters` | `List<string>` | Form, Optional | The list of webhook event triggers that are enabled for this Service: `onMessageAdded`, `onMessageUpdated`, `onMessageRemoved`, `onMessageAdd`, `onMessageUpdate`, `onMessageRemove`, `onConversationUpdated`, `onConversationRemoved`, `onConversationAdd`, `onConversationAdded`, `onConversationRemove`, `onConversationUpdate`, `onConversationStateUpdated`, `onParticipantAdded`, `onParticipantUpdated`, `onParticipantRemoved`, `onParticipantAdd`, `onParticipantRemove`, `onParticipantUpdate`, `onDeliveryUpdated`, `onUserAdded`, `onUserUpdate`, `onUserUpdated` |
| `preWebhookUrl` | `string` | Form, Optional | The absolute url the pre-event webhook request should be sent to. |
| `postWebhookUrl` | `string` | Form, Optional | The absolute url the post-event webhook request should be sent to. |
| `target` | [`ConfigurationWebhookTarget?`](../../doc/models/configuration-webhook-target.md) | Form, Optional | The routing target of the webhook. Can be ordinary or route internally to Flex |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConfigurationWebhook](../../doc/models/configuration-webhook.md).

## Example Usage

```csharp
string method = "GET";
List<string> filters = new List<string>
{
    "onConversationUpdated",
};

string preWebhookUrl = "https://example.com/pre";
string postWebhookUrl = "https://example.com/post";
ConfigurationWebhookTarget? target = ConfigurationWebhookTarget.Webhook;
try
{
    ApiResponse<ConfigurationWebhook> result = await conversationsV1WebhookApi.UpdateConfigurationWebhookAsync(
        method,
        filters,
        preWebhookUrl,
        postWebhookUrl,
        target
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
  "pre_webhook_url": "https://example.com/pre",
  "post_webhook_url": "http://example.com/post",
  "method": "GET",
  "filters": [
    "onConversationUpdated"
  ],
  "target": "webhook",
  "url": "https://conversations.twilio.com/v1/Configuration/Webhooks"
}
```


# List Conversation Scoped Webhook

Retrieve a list of all webhooks scoped to the conversation

```csharp
ListConversationScopedWebhookAsync(
    string conversationSid,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 5, and the maximum is 5.<br><br>**Constraints**: `>= 1`, `<= 5` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListConversationScopedWebhookResponse](../../doc/models/list-conversation-scoped-webhook-response.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
try
{
    ApiResponse<ListConversationScopedWebhookResponse> result = await conversationsV1WebhookApi.ListConversationScopedWebhookAsync(conversationSid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Create Conversation Scoped Webhook

Create a new webhook scoped to the conversation

```csharp
CreateConversationScopedWebhookAsync(
    string conversationSid,
    Models.ConversationScopedWebhookTarget target,
    string configurationUrl = null,
    Models.ConversationScopedWebhookMethod? configurationMethod = null,
    List<string> configurationFilters = null,
    List<string> configurationTriggers = null,
    string configurationFlowSid = null,
    int? configurationReplayAfter = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `target` | [`ConversationScopedWebhookTarget`](../../doc/models/conversation-scoped-webhook-target.md) | Form, Required | The target of this webhook: `webhook`, `studio`, `trigger` |
| `configurationUrl` | `string` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configurationMethod` | [`ConversationScopedWebhookMethod?`](../../doc/models/conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configurationFilters` | `List<string>` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configurationTriggers` | `List<string>` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configurationFlowSid` | `string` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |
| `configurationReplayAfter` | `int?` | Form, Optional | The message index for which and it's successors the webhook will be replayed. Not set by default |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConversationScopedWebhook](../../doc/models/conversation-scoped-webhook.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
ConversationScopedWebhookTarget target = ConversationScopedWebhookTarget.Webhook;
string configurationUrl = "https://example.com";
ConversationScopedWebhookMethod? configurationMethod = ConversationScopedWebhookMethod.Get;
List<string> configurationFilters = new List<string>
{
    "onMessageSent",
    "onConversationDestroyed",
};

int? configurationReplayAfter = 7;
try
{
    ApiResponse<ConversationScopedWebhook> result = await conversationsV1WebhookApi.CreateConversationScopedWebhookAsync(
        conversationSid,
        target,
        configurationUrl,
        configurationMethod,
        configurationFilters,
        null,
        null,
        configurationReplayAfter
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Conversation Scoped Webhook

Fetch the configuration of a conversation-scoped webhook

```csharp
FetchConversationScopedWebhookAsync(
    string conversationSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConversationScopedWebhook](../../doc/models/conversation-scoped-webhook.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
string sid = "Sid8";
try
{
    ApiResponse<ConversationScopedWebhook> result = await conversationsV1WebhookApi.FetchConversationScopedWebhookAsync(
        conversationSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Update Conversation Scoped Webhook

Update an existing conversation-scoped webhook

```csharp
UpdateConversationScopedWebhookAsync(
    string conversationSid,
    string sid,
    string configurationUrl = null,
    Models.ConversationScopedWebhookMethod? configurationMethod = null,
    List<string> configurationFilters = null,
    List<string> configurationTriggers = null,
    string configurationFlowSid = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |
| `configurationUrl` | `string` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configurationMethod` | [`ConversationScopedWebhookMethod?`](../../doc/models/conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configurationFilters` | `List<string>` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configurationTriggers` | `List<string>` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configurationFlowSid` | `string` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConversationScopedWebhook](../../doc/models/conversation-scoped-webhook.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
string sid = "Sid8";
string configurationUrl = "https://example.com";
ConversationScopedWebhookMethod? configurationMethod = ConversationScopedWebhookMethod.Post;
List<string> configurationTriggers = new List<string>
{
    "keyword1",
    "keyword2",
};

try
{
    ApiResponse<ConversationScopedWebhook> result = await conversationsV1WebhookApi.UpdateConversationScopedWebhookAsync(
        conversationSid,
        sid,
        configurationUrl,
        configurationMethod,
        null,
        configurationTriggers
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Delete Conversation Scoped Webhook

Remove an existing webhook scoped to the conversation

```csharp
DeleteConversationScopedWebhookAsync(
    string conversationSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Response Type

`Task`

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
string sid = "Sid8";
try
{
    await conversationsV1WebhookApi.DeleteConversationScopedWebhookAsync(
        conversationSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Create Service Conversation Scoped Webhook

Create a new webhook scoped to the conversation in a specific service

```csharp
CreateServiceConversationScopedWebhookAsync(
    string chatServiceSid,
    string conversationSid,
    Models.ServiceConversationScopedWebhookTarget target,
    string configurationUrl = null,
    Models.ServiceConversationScopedWebhookMethod? configurationMethod = null,
    List<string> configurationFilters = null,
    List<string> configurationTriggers = null,
    string configurationFlowSid = null,
    int? configurationReplayAfter = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `target` | [`ServiceConversationScopedWebhookTarget`](../../doc/models/service-conversation-scoped-webhook-target.md) | Form, Required | The target of this webhook: `webhook`, `studio`, `trigger` |
| `configurationUrl` | `string` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configurationMethod` | [`ServiceConversationScopedWebhookMethod?`](../../doc/models/service-conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configurationFilters` | `List<string>` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configurationTriggers` | `List<string>` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configurationFlowSid` | `string` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |
| `configurationReplayAfter` | `int?` | Form, Optional | The message index for which and it's successors the webhook will be replayed. Not set by default |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversationScopedWebhook](../../doc/models/service-conversation-scoped-webhook.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
ServiceConversationScopedWebhookTarget target = ServiceConversationScopedWebhookTarget.Webhook;
string configurationUrl = "https://example.com";
ServiceConversationScopedWebhookMethod? configurationMethod = ServiceConversationScopedWebhookMethod.Get;
List<string> configurationFilters = new List<string>
{
    "onMessageSent",
    "onConversationDestroyed",
};

int? configurationReplayAfter = 7;
try
{
    ApiResponse<ServiceConversationScopedWebhook> result = await conversationsV1WebhookApi.CreateServiceConversationScopedWebhookAsync(
        chatServiceSid,
        conversationSid,
        target,
        configurationUrl,
        configurationMethod,
        configurationFilters,
        null,
        null,
        configurationReplayAfter
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# List Service Conversation Scoped Webhook

Retrieve a list of all webhooks scoped to the conversation

```csharp
ListServiceConversationScopedWebhookAsync(
    string chatServiceSid,
    string conversationSid,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 5, and the maximum is 5.<br><br>**Constraints**: `>= 1`, `<= 5` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListServiceConversationScopedWebhookResponse](../../doc/models/list-service-conversation-scoped-webhook-response.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
try
{
    ApiResponse<ListServiceConversationScopedWebhookResponse> result = await conversationsV1WebhookApi.ListServiceConversationScopedWebhookAsync(
        chatServiceSid,
        conversationSid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Update Service Conversation Scoped Webhook

Update an existing conversation-scoped webhook

```csharp
UpdateServiceConversationScopedWebhookAsync(
    string chatServiceSid,
    string conversationSid,
    string sid,
    string configurationUrl = null,
    Models.ServiceConversationScopedWebhookMethod? configurationMethod = null,
    List<string> configurationFilters = null,
    List<string> configurationTriggers = null,
    string configurationFlowSid = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |
| `configurationUrl` | `string` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configurationMethod` | [`ServiceConversationScopedWebhookMethod?`](../../doc/models/service-conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configurationFilters` | `List<string>` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configurationTriggers` | `List<string>` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configurationFlowSid` | `string` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversationScopedWebhook](../../doc/models/service-conversation-scoped-webhook.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
string sid = "Sid8";
string configurationUrl = "https://example.com";
ServiceConversationScopedWebhookMethod? configurationMethod = ServiceConversationScopedWebhookMethod.Post;
List<string> configurationTriggers = new List<string>
{
    "keyword1",
    "keyword2",
};

try
{
    ApiResponse<ServiceConversationScopedWebhook> result = await conversationsV1WebhookApi.UpdateServiceConversationScopedWebhookAsync(
        chatServiceSid,
        conversationSid,
        sid,
        configurationUrl,
        configurationMethod,
        null,
        configurationTriggers
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Delete Service Conversation Scoped Webhook

Remove an existing webhook scoped to the conversation

```csharp
DeleteServiceConversationScopedWebhookAsync(
    string chatServiceSid,
    string conversationSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Response Type

`Task`

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
string sid = "Sid8";
try
{
    await conversationsV1WebhookApi.DeleteServiceConversationScopedWebhookAsync(
        chatServiceSid,
        conversationSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Service Conversation Scoped Webhook

Fetch the configuration of a conversation-scoped webhook

```csharp
FetchServiceConversationScopedWebhookAsync(
    string chatServiceSid,
    string conversationSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversationScopedWebhook](../../doc/models/service-conversation-scoped-webhook.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
string sid = "Sid8";
try
{
    ApiResponse<ServiceConversationScopedWebhook> result = await conversationsV1WebhookApi.FetchServiceConversationScopedWebhookAsync(
        chatServiceSid,
        conversationSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Update Service Webhook Configuration

Update a specific Webhook.

```csharp
UpdateServiceWebhookConfigurationAsync(
    string chatServiceSid,
    string preWebhookUrl = null,
    string postWebhookUrl = null,
    List<string> filters = null,
    string method = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The unique ID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `preWebhookUrl` | `string` | Form, Optional | The absolute url the pre-event webhook request should be sent to. |
| `postWebhookUrl` | `string` | Form, Optional | The absolute url the post-event webhook request should be sent to. |
| `filters` | `List<string>` | Form, Optional | The list of events that your configured webhook targets will receive. Events not configured here will not fire. Possible values are `onParticipantAdd`, `onParticipantAdded`, `onDeliveryUpdated`, `onConversationUpdated`, `onConversationRemove`, `onParticipantRemove`, `onConversationUpdate`, `onMessageAdd`, `onMessageRemoved`, `onParticipantUpdated`, `onConversationAdded`, `onMessageAdded`, `onConversationAdd`, `onConversationRemoved`, `onParticipantUpdate`, `onMessageRemove`, `onMessageUpdated`, `onParticipantRemoved`, `onMessageUpdate` or `onConversationStateUpdated`. |
| `method` | `string` | Form, Optional | The HTTP method to be used when sending a webhook request. One of `GET` or `POST`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceWebhookConfiguration](../../doc/models/service-webhook-configuration.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string preWebhookUrl = "https://www.example.com/pre";
string postWebhookUrl = "https://www.example.com/post";
List<string> filters = new List<string>
{
    "onMessageRemoved",
    "onParticipantAdded",
};

string method = "GET";
try
{
    ApiResponse<ServiceWebhookConfiguration> result = await conversationsV1WebhookApi.UpdateServiceWebhookConfigurationAsync(
        chatServiceSid,
        preWebhookUrl,
        postWebhookUrl,
        filters,
        method
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
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "pre_webhook_url": "https://www.example.com/pre",
  "post_webhook_url": "https://www.example.com/post",
  "filters": [
    "onMessageRemoved",
    "onParticipantAdded"
  ],
  "method": "GET",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
}
```


# Fetch Service Webhook Configuration

Fetch a specific service webhook configuration.

```csharp
FetchServiceWebhookConfigurationAsync(
    string chatServiceSid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The unique ID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceWebhookConfiguration](../../doc/models/service-webhook-configuration.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
try
{
    ApiResponse<ServiceWebhookConfiguration> result = await conversationsV1WebhookApi.FetchServiceWebhookConfigurationAsync(chatServiceSid);
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
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "pre_webhook_url": "https://www.example.com/pre",
  "post_webhook_url": "https://www.example.com/post",
  "filters": [
    "onMessageRemove",
    "onParticipantAdd"
  ],
  "method": "POST",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
}
```

