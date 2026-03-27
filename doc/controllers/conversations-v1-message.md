# Conversations V1 Message

```csharp
ConversationsV1MessageApi conversationsV1MessageApi = client.ConversationsV1MessageApi;
```

## Class Name

`ConversationsV1MessageApi`

## Methods

* [Create Conversation Message](../../doc/controllers/conversations-v1-message.md#create-conversation-message)
* [List Conversation Message](../../doc/controllers/conversations-v1-message.md#list-conversation-message)
* [Update Conversation Message](../../doc/controllers/conversations-v1-message.md#update-conversation-message)
* [Delete Conversation Message](../../doc/controllers/conversations-v1-message.md#delete-conversation-message)
* [Fetch Conversation Message](../../doc/controllers/conversations-v1-message.md#fetch-conversation-message)
* [Create Service Conversation Message](../../doc/controllers/conversations-v1-message.md#create-service-conversation-message)
* [List Service Conversation Message](../../doc/controllers/conversations-v1-message.md#list-service-conversation-message)
* [Update Service Conversation Message](../../doc/controllers/conversations-v1-message.md#update-service-conversation-message)
* [Delete Service Conversation Message](../../doc/controllers/conversations-v1-message.md#delete-service-conversation-message)
* [Fetch Service Conversation Message](../../doc/controllers/conversations-v1-message.md#fetch-service-conversation-message)


# Create Conversation Message

Add a new message to the conversation

```csharp
CreateConversationMessageAsync(
    string conversationSid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string author = null,
    string body = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string attributes = null,
    string mediaSid = null,
    string contentSid = null,
    string contentVariables = null,
    string subject = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `string` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `string` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `dateCreated` | `DateTime?` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `string` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `mediaSid` | `string` | Form, Optional | The Media SID to be attached to the new Message.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^ME[0-9a-fA-F]{32}$` |
| `contentSid` | `string` | Form, Optional | The unique ID of the multi-channel [Rich Content](https://www.twilio.com/docs/content) template, required for template-generated messages.  **Note** that if this field is set, `Body` and `MediaSid` parameters are ignored.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HX[0-9a-fA-F]{32}$` |
| `contentVariables` | `string` | Form, Optional | A structurally valid JSON string that contains values to resolve Rich Content template variables. |
| `subject` | `string` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConversationMessage](../../doc/models/conversation-message.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
string author = "message author";
string body = "Hello";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string attributes = "{ \"importance\": \"high\" }";
string mediaSid = "MEaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string contentSid = "HXaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string contentVariables = "{\"name\": \"John\"}";
string subject = "message subject";
try
{
    ApiResponse<ConversationMessage> result = await conversationsV1MessageApi.CreateConversationMessageAsync(
        conversationSid,
        null,
        author,
        body,
        dateCreated,
        dateUpdated,
        attributes,
        mediaSid,
        contentSid,
        contentVariables,
        subject
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# List Conversation Message

Retrieve a list of all messages in the conversation

```csharp
ListConversationMessageAsync(
    string conversationSid,
    Models.ConversationMessageOrderType? order = null,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for messages. |
| `order` | [`ConversationMessageOrderType?`](../../doc/models/conversation-message-order-type.md) | Query, Optional | The sort order of the returned messages. Can be: `asc` (ascending) or `desc` (descending), with `asc` as the default. |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListConversationMessageResponse](../../doc/models/list-conversation-message-response.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
ConversationMessageOrderType? order = ConversationMessageOrderType.Desc;
try
{
    ApiResponse<ListConversationMessageResponse> result = await conversationsV1MessageApi.ListConversationMessageAsync(
        conversationSid,
        order
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Update Conversation Message

Update an existing message in the conversation

```csharp
UpdateConversationMessageAsync(
    string conversationSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string author = null,
    string body = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string attributes = null,
    string subject = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `string` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `string` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `dateCreated` | `DateTime?` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `string` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `subject` | `string` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConversationMessage](../../doc/models/conversation-message.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
string sid = "Sid8";
string author = "message author";
string body = "Hello";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string attributes = "{ \"importance\": \"high\" }";
try
{
    ApiResponse<ConversationMessage> result = await conversationsV1MessageApi.UpdateConversationMessageAsync(
        conversationSid,
        sid,
        null,
        author,
        body,
        dateCreated,
        dateUpdated,
        attributes
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Delete Conversation Message

Remove a message from the conversation

```csharp
DeleteConversationMessageAsync(
    string conversationSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

`Task`

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
string sid = "Sid8";
try
{
    await conversationsV1MessageApi.DeleteConversationMessageAsync(
        conversationSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Conversation Message

Fetch a message from the conversation

```csharp
FetchConversationMessageAsync(
    string conversationSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConversationMessage](../../doc/models/conversation-message.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
string sid = "Sid8";
try
{
    ApiResponse<ConversationMessage> result = await conversationsV1MessageApi.FetchConversationMessageAsync(
        conversationSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Create Service Conversation Message

Add a new message to the conversation in a specific service

```csharp
CreateServiceConversationMessageAsync(
    string chatServiceSid,
    string conversationSid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string author = null,
    string body = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string attributes = null,
    string mediaSid = null,
    string contentSid = null,
    string contentVariables = null,
    string subject = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `string` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `string` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `dateCreated` | `DateTime?` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `string` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `mediaSid` | `string` | Form, Optional | The Media SID to be attached to the new Message.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^ME[0-9a-fA-F]{32}$` |
| `contentSid` | `string` | Form, Optional | The unique ID of the multi-channel [Rich Content](https://www.twilio.com/docs/content) template, required for template-generated messages.  **Note** that if this field is set, `Body` and `MediaSid` parameters are ignored.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HX[0-9a-fA-F]{32}$` |
| `contentVariables` | `string` | Form, Optional | A structurally valid JSON string that contains values to resolve Rich Content template variables. |
| `subject` | `string` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversationMessage](../../doc/models/service-conversation-message.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
string author = "message author";
string body = "Hello";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string attributes = "{ \"importance\": \"high\" }";
string mediaSid = "MEaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string contentSid = "HXaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string contentVariables = "{\"name\": \"John\"}";
string subject = "message subject";
try
{
    ApiResponse<ServiceConversationMessage> result = await conversationsV1MessageApi.CreateServiceConversationMessageAsync(
        chatServiceSid,
        conversationSid,
        null,
        author,
        body,
        dateCreated,
        dateUpdated,
        attributes,
        mediaSid,
        contentSid,
        contentVariables,
        subject
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# List Service Conversation Message

Retrieve a list of all messages in the conversation

```csharp
ListServiceConversationMessageAsync(
    string chatServiceSid,
    string conversationSid,
    Models.ServiceConversationMessageOrderType? order = null,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for messages. |
| `order` | [`ServiceConversationMessageOrderType?`](../../doc/models/service-conversation-message-order-type.md) | Query, Optional | The sort order of the returned messages. Can be: `asc` (ascending) or `desc` (descending), with `asc` as the default. |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListServiceConversationMessageResponse](../../doc/models/list-service-conversation-message-response.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
ServiceConversationMessageOrderType? order = ServiceConversationMessageOrderType.Desc;
try
{
    ApiResponse<ListServiceConversationMessageResponse> result = await conversationsV1MessageApi.ListServiceConversationMessageAsync(
        chatServiceSid,
        conversationSid,
        order
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Update Service Conversation Message

Update an existing message in the conversation

```csharp
UpdateServiceConversationMessageAsync(
    string chatServiceSid,
    string conversationSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string author = null,
    string body = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string attributes = null,
    string subject = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `string` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `string` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `dateCreated` | `DateTime?` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `string` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `subject` | `string` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversationMessage](../../doc/models/service-conversation-message.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
string sid = "Sid8";
string author = "message author";
string body = "Hello";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string attributes = "{ \"importance\": \"high\" }";
try
{
    ApiResponse<ServiceConversationMessage> result = await conversationsV1MessageApi.UpdateServiceConversationMessageAsync(
        chatServiceSid,
        conversationSid,
        sid,
        null,
        author,
        body,
        dateCreated,
        dateUpdated,
        attributes
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Delete Service Conversation Message

Remove a message from the conversation

```csharp
DeleteServiceConversationMessageAsync(
    string chatServiceSid,
    string conversationSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

`Task`

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
string sid = "Sid8";
try
{
    await conversationsV1MessageApi.DeleteServiceConversationMessageAsync(
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


# Fetch Service Conversation Message

Fetch a message from the conversation

```csharp
FetchServiceConversationMessageAsync(
    string chatServiceSid,
    string conversationSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversationMessage](../../doc/models/service-conversation-message.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
string sid = "Sid8";
try
{
    ApiResponse<ServiceConversationMessage> result = await conversationsV1MessageApi.FetchServiceConversationMessageAsync(
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

