# Conversations V1 Conversation

```csharp
ConversationsV1ConversationApi conversationsV1ConversationApi = client.ConversationsV1ConversationApi;
```

## Class Name

`ConversationsV1ConversationApi`

## Methods

* [Create Conversation](../../doc/controllers/conversations-v1-conversation.md#create-conversation)
* [List Conversation](../../doc/controllers/conversations-v1-conversation.md#list-conversation)
* [Update Conversation](../../doc/controllers/conversations-v1-conversation.md#update-conversation)
* [Delete Conversation](../../doc/controllers/conversations-v1-conversation.md#delete-conversation)
* [Fetch Conversation](../../doc/controllers/conversations-v1-conversation.md#fetch-conversation)
* [Create Service Conversation](../../doc/controllers/conversations-v1-conversation.md#create-service-conversation)
* [List Service Conversation](../../doc/controllers/conversations-v1-conversation.md#list-service-conversation)
* [Update Service Conversation](../../doc/controllers/conversations-v1-conversation.md#update-service-conversation)
* [Delete Service Conversation](../../doc/controllers/conversations-v1-conversation.md#delete-service-conversation)
* [Fetch Service Conversation](../../doc/controllers/conversations-v1-conversation.md#fetch-service-conversation)


# Create Conversation

Create a new conversation in your account's default service

```csharp
CreateConversationAsync(
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string friendlyName = null,
    string uniqueName = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string messagingServiceSid = null,
    string attributes = null,
    Models.ConversationState? state = null,
    string timersInactive = null,
    string timersClosed = null,
    string bindingsEmailAddress = null,
    string bindingsEmailName = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `string` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `uniqueName` | `string` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `dateCreated` | `DateTime?` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date that this resource was last updated. |
| `messagingServiceSid` | `string` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `attributes` | `string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `state` | [`ConversationState?`](../../doc/models/conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timersInactive` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timersClosed` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `bindingsEmailAddress` | `string` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindingsEmailName` | `string` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Conversation](../../doc/models/conversation.md).

## Example Usage

```csharp
string friendlyName = "friendly_name";
string uniqueName = "unique_name";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string messagingServiceSid = "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string attributes = "{ \"topic\": \"feedback\" }";
ConversationState? state = ConversationState.Inactive;
string timersInactive = "PT1M";
string timersClosed = "PT10M";
try
{
    ApiResponse<Conversation> result = await conversationsV1ConversationApi.CreateConversationAsync(
        null,
        friendlyName,
        uniqueName,
        dateCreated,
        dateUpdated,
        messagingServiceSid,
        attributes,
        state,
        timersInactive,
        timersClosed
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# List Conversation

Retrieve a list of conversations in your account's default service

```csharp
ListConversationAsync(
    string startDate = null,
    string endDate = null,
    Models.ConversationState? state = null,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `startDate` | `string` | Query, Optional | Specifies the beginning of the date range for filtering Conversations based on their creation date. Conversations that were created on or after this date will be included in the results. The date must be in ISO8601 format, specifically starting at the beginning of the specified date (YYYY-MM-DDT00:00:00Z), for precise filtering. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `endDate` | `string` | Query, Optional | Defines the end of the date range for filtering conversations by their creation date. Only conversations that were created on or before this date will appear in the results.  The date must be in ISO8601 format, specifically capturing up to the end of the specified date (YYYY-MM-DDT23:59:59Z), to ensure that conversations from the entire end day are included. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `state` | [`ConversationState?`](../../doc/models/conversation-state.md) | Query, Optional | State for sorting and filtering list of Conversations. Can be `active`, `inactive` or `closed` |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListConversationResponse](../../doc/models/list-conversation-response.md).

## Example Usage

```csharp
try
{
    ApiResponse<ListConversationResponse> result = await conversationsV1ConversationApi.ListConversationAsync();
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Update Conversation

Update an existing conversation in your account's default service

```csharp
UpdateConversationAsync(
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string friendlyName = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string attributes = null,
    string messagingServiceSid = null,
    Models.ConversationState? state = null,
    string timersInactive = null,
    string timersClosed = null,
    string uniqueName = null,
    string bindingsEmailAddress = null,
    string bindingsEmailName = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `string` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `dateCreated` | `DateTime?` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messagingServiceSid` | `string` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `state` | [`ConversationState?`](../../doc/models/conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timersInactive` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timersClosed` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `uniqueName` | `string` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `bindingsEmailAddress` | `string` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindingsEmailName` | `string` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Conversation](../../doc/models/conversation.md).

## Example Usage

```csharp
string sid = "Sid8";
string friendlyName = "friendly_name";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string attributes = "{ \"topic\": \"feedback\" }";
string messagingServiceSid = "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaab";
ConversationState? state = ConversationState.Inactive;
string timersInactive = "PT1M";
string timersClosed = "PT10M";
string uniqueName = "unique_name";
try
{
    ApiResponse<Conversation> result = await conversationsV1ConversationApi.UpdateConversationAsync(
        sid,
        null,
        friendlyName,
        dateCreated,
        dateUpdated,
        attributes,
        messagingServiceSid,
        state,
        timersInactive,
        timersClosed,
        uniqueName
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Delete Conversation

Remove a conversation from your account's default service

```csharp
DeleteConversationAsync(
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

`Task`

## Example Usage

```csharp
string sid = "Sid8";
try
{
    await conversationsV1ConversationApi.DeleteConversationAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Conversation

Fetch a conversation from your account's default service

```csharp
FetchConversationAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Conversation](../../doc/models/conversation.md).

## Example Usage

```csharp
string sid = "Sid8";
try
{
    ApiResponse<Conversation> result = await conversationsV1ConversationApi.FetchConversationAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Create Service Conversation

Create a new conversation in your service

```csharp
CreateServiceConversationAsync(
    string chatServiceSid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string friendlyName = null,
    string uniqueName = null,
    string attributes = null,
    string messagingServiceSid = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    Models.ServiceConversationState? state = null,
    string timersInactive = null,
    string timersClosed = null,
    string bindingsEmailAddress = null,
    string bindingsEmailName = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `string` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `uniqueName` | `string` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `attributes` | `string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messagingServiceSid` | `string` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `dateCreated` | `DateTime?` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date that this resource was last updated. |
| `state` | [`ServiceConversationState?`](../../doc/models/service-conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timersInactive` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timersClosed` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `bindingsEmailAddress` | `string` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindingsEmailName` | `string` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversation](../../doc/models/service-conversation.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string friendlyName = "friendly_name";
string uniqueName = "unique_name";
string attributes = "{ \"topic\": \"feedback\" }";
string messagingServiceSid = "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
ServiceConversationState? state = ServiceConversationState.Inactive;
string timersInactive = "PT1M";
string timersClosed = "PT10M";
try
{
    ApiResponse<ServiceConversation> result = await conversationsV1ConversationApi.CreateServiceConversationAsync(
        chatServiceSid,
        null,
        friendlyName,
        uniqueName,
        attributes,
        messagingServiceSid,
        dateCreated,
        dateUpdated,
        state,
        timersInactive,
        timersClosed
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# List Service Conversation

Retrieve a list of conversations in your service

```csharp
ListServiceConversationAsync(
    string chatServiceSid,
    string startDate = null,
    string endDate = null,
    Models.ServiceConversationState? state = null,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `startDate` | `string` | Query, Optional | Specifies the beginning of the date range for filtering Conversations based on their creation date. Conversations that were created on or after this date will be included in the results. The date must be in ISO8601 format, specifically starting at the beginning of the specified date (YYYY-MM-DDT00:00:00Z), for precise filtering. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `endDate` | `string` | Query, Optional | Defines the end of the date range for filtering conversations by their creation date. Only conversations that were created on or before this date will appear in the results.  The date must be in ISO8601 format, specifically capturing up to the end of the specified date (YYYY-MM-DDT23:59:59Z), to ensure that conversations from the entire end day are included. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `state` | [`ServiceConversationState?`](../../doc/models/service-conversation-state.md) | Query, Optional | State for sorting and filtering list of Conversations. Can be `active`, `inactive` or `closed` |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListServiceConversationResponse](../../doc/models/list-service-conversation-response.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
try
{
    ApiResponse<ListServiceConversationResponse> result = await conversationsV1ConversationApi.ListServiceConversationAsync(chatServiceSid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Update Service Conversation

Update an existing conversation in your service

```csharp
UpdateServiceConversationAsync(
    string chatServiceSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string friendlyName = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string attributes = null,
    string messagingServiceSid = null,
    Models.ServiceConversationState? state = null,
    string timersInactive = null,
    string timersClosed = null,
    string uniqueName = null,
    string bindingsEmailAddress = null,
    string bindingsEmailName = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `string` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `dateCreated` | `DateTime?` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messagingServiceSid` | `string` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `state` | [`ServiceConversationState?`](../../doc/models/service-conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timersInactive` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timersClosed` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `uniqueName` | `string` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `bindingsEmailAddress` | `string` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindingsEmailName` | `string` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversation](../../doc/models/service-conversation.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string sid = "Sid8";
string friendlyName = "friendly_name";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string attributes = "{ \"topic\": \"feedback\" }";
string messagingServiceSid = "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaab";
ServiceConversationState? state = ServiceConversationState.Inactive;
string timersInactive = "PT1M";
string timersClosed = "PT10M";
string uniqueName = "unique_name";
try
{
    ApiResponse<ServiceConversation> result = await conversationsV1ConversationApi.UpdateServiceConversationAsync(
        chatServiceSid,
        sid,
        null,
        friendlyName,
        dateCreated,
        dateUpdated,
        attributes,
        messagingServiceSid,
        state,
        timersInactive,
        timersClosed,
        uniqueName
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Delete Service Conversation

Remove a conversation from your service

```csharp
DeleteServiceConversationAsync(
    string chatServiceSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

`Task`

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string sid = "Sid8";
try
{
    await conversationsV1ConversationApi.DeleteServiceConversationAsync(
        chatServiceSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Service Conversation

Fetch a conversation from your service

```csharp
FetchServiceConversationAsync(
    string chatServiceSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversation](../../doc/models/service-conversation.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string sid = "Sid8";
try
{
    ApiResponse<ServiceConversation> result = await conversationsV1ConversationApi.FetchServiceConversationAsync(
        chatServiceSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

