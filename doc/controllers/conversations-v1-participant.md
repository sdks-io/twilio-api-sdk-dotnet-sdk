# Conversations V1 Participant

```csharp
ConversationsV1ParticipantApi conversationsV1ParticipantApi = client.ConversationsV1ParticipantApi;
```

## Class Name

`ConversationsV1ParticipantApi`

## Methods

* [Create Conversation Participant](../../doc/controllers/conversations-v1-participant.md#create-conversation-participant)
* [List Conversation Participant](../../doc/controllers/conversations-v1-participant.md#list-conversation-participant)
* [Update Conversation Participant](../../doc/controllers/conversations-v1-participant.md#update-conversation-participant)
* [Delete Conversation Participant](../../doc/controllers/conversations-v1-participant.md#delete-conversation-participant)
* [Fetch Conversation Participant](../../doc/controllers/conversations-v1-participant.md#fetch-conversation-participant)
* [Create Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#create-service-conversation-participant)
* [List Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#list-service-conversation-participant)
* [Update Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#update-service-conversation-participant)
* [Delete Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#delete-service-conversation-participant)
* [Fetch Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#fetch-service-conversation-participant)


# Create Conversation Participant

Add a new participant to the conversation

```csharp
CreateConversationParticipantAsync(
    string conversationSid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string identity = null,
    string messagingBindingAddress = null,
    string messagingBindingProxyAddress = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string attributes = null,
    string messagingBindingProjectedAddress = null,
    string roleSid = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `identity` | `string` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. |
| `messagingBindingAddress` | `string` | Form, Optional | The address of the participant's device, e.g. a phone or WhatsApp number. Together with the Proxy address, this determines a participant uniquely. This field (with proxy_address) is only null when the participant is interacting from an SDK endpoint (see the 'identity' field). |
| `messagingBindingProxyAddress` | `string` | Form, Optional | The address of the Twilio phone number (or WhatsApp number) that the participant is in contact with. This field, together with participant address, is only null when the participant is interacting from an SDK endpoint (see the 'identity' field). |
| `dateCreated` | `DateTime?` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messagingBindingProjectedAddress` | `string` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. Communication mask for the Conversation participant with Identity. |
| `roleSid` | `string` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConversationParticipant](../../doc/models/conversation-participant.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
string identity = "IDENTITY";
string messagingBindingAddress = "+15558675310";
string messagingBindingProxyAddress = "+15017122661";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string attributes = "{ \"role\": \"driver\" }";
string messagingBindingProjectedAddress = "+15017122661";
string roleSid = "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
try
{
    ApiResponse<ConversationParticipant> result = await conversationsV1ParticipantApi.CreateConversationParticipantAsync(
        conversationSid,
        null,
        identity,
        messagingBindingAddress,
        messagingBindingProxyAddress,
        dateCreated,
        dateUpdated,
        attributes,
        messagingBindingProjectedAddress,
        roleSid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# List Conversation Participant

Retrieve a list of all participants of the conversation

```csharp
ListConversationParticipantAsync(
    string conversationSid,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for participants. |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListConversationParticipantResponse](../../doc/models/list-conversation-participant-response.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
try
{
    ApiResponse<ListConversationParticipantResponse> result = await conversationsV1ParticipantApi.ListConversationParticipantAsync(conversationSid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Update Conversation Participant

Update an existing participant in the conversation

```csharp
UpdateConversationParticipantAsync(
    string conversationSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string attributes = null,
    string roleSid = null,
    string messagingBindingProxyAddress = null,
    string messagingBindingProjectedAddress = null,
    string identity = null,
    int? lastReadMessageIndex = null,
    string lastReadTimestamp = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `dateCreated` | `DateTime?` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `roleSid` | `string` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `messagingBindingProxyAddress` | `string` | Form, Optional | The address of the Twilio phone number that the participant is in contact with. 'null' value will remove it. |
| `messagingBindingProjectedAddress` | `string` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. 'null' value will remove it. |
| `identity` | `string` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. |
| `lastReadMessageIndex` | `int?` | Form, Optional | Index of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |
| `lastReadTimestamp` | `string` | Form, Optional | Timestamp of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConversationParticipant](../../doc/models/conversation-participant.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
string sid = "Sid8";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string attributes = "{ \"role\": \"driver\" }";
string roleSid = "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string messagingBindingProjectedAddress = "+15017122661";
try
{
    ApiResponse<ConversationParticipant> result = await conversationsV1ParticipantApi.UpdateConversationParticipantAsync(
        conversationSid,
        sid,
        null,
        dateCreated,
        dateUpdated,
        attributes,
        roleSid,
        null,
        messagingBindingProjectedAddress
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Delete Conversation Participant

Remove a participant from the conversation

```csharp
DeleteConversationParticipantAsync(
    string conversationSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

`Task`

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
string sid = "Sid8";
try
{
    await conversationsV1ParticipantApi.DeleteConversationParticipantAsync(
        conversationSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Conversation Participant

Fetch a participant of the conversation

```csharp
FetchConversationParticipantAsync(
    string conversationSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Alternatively, you can pass a Participant's `identity` rather than the SID. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConversationParticipant](../../doc/models/conversation-participant.md).

## Example Usage

```csharp
string conversationSid = "ConversationSid0";
string sid = "Sid8";
try
{
    ApiResponse<ConversationParticipant> result = await conversationsV1ParticipantApi.FetchConversationParticipantAsync(
        conversationSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Create Service Conversation Participant

Add a new participant to the conversation in a specific service

```csharp
CreateServiceConversationParticipantAsync(
    string chatServiceSid,
    string conversationSid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string identity = null,
    string messagingBindingAddress = null,
    string messagingBindingProxyAddress = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string attributes = null,
    string messagingBindingProjectedAddress = null,
    string roleSid = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `identity` | `string` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the [Conversation SDK](https://www.twilio.com/docs/conversations/sdk-overview) to communicate. Limited to 256 characters. |
| `messagingBindingAddress` | `string` | Form, Optional | The address of the participant's device, e.g. a phone or WhatsApp number. Together with the Proxy address, this determines a participant uniquely. This field (with `proxy_address`) is only null when the participant is interacting from an SDK endpoint (see the `identity` field). |
| `messagingBindingProxyAddress` | `string` | Form, Optional | The address of the Twilio phone number (or WhatsApp number) that the participant is in contact with. This field, together with participant address, is only null when the participant is interacting from an SDK endpoint (see the `identity` field). |
| `dateCreated` | `DateTime?` | Form, Optional | The date on which this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date on which this resource was last updated. |
| `attributes` | `string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set `{}` will be returned. |
| `messagingBindingProjectedAddress` | `string` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. |
| `roleSid` | `string` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversationParticipant](../../doc/models/service-conversation-participant.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
string identity = "IDENTITY";
string messagingBindingAddress = "+15558675310";
string messagingBindingProxyAddress = "+15017122661";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string attributes = "{ \"role\": \"driver\" }";
string messagingBindingProjectedAddress = "+15017122661";
string roleSid = "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
try
{
    ApiResponse<ServiceConversationParticipant> result = await conversationsV1ParticipantApi.CreateServiceConversationParticipantAsync(
        chatServiceSid,
        conversationSid,
        null,
        identity,
        messagingBindingAddress,
        messagingBindingProxyAddress,
        dateCreated,
        dateUpdated,
        attributes,
        messagingBindingProjectedAddress,
        roleSid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# List Service Conversation Participant

Retrieve a list of all participants of the conversation

```csharp
ListServiceConversationParticipantAsync(
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
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for participants. |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListServiceConversationParticipantResponse](../../doc/models/list-service-conversation-participant-response.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
try
{
    ApiResponse<ListServiceConversationParticipantResponse> result = await conversationsV1ParticipantApi.ListServiceConversationParticipantAsync(
        chatServiceSid,
        conversationSid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Update Service Conversation Participant

Update an existing participant in the conversation

```csharp
UpdateServiceConversationParticipantAsync(
    string chatServiceSid,
    string conversationSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string identity = null,
    string attributes = null,
    string roleSid = null,
    string messagingBindingProxyAddress = null,
    string messagingBindingProjectedAddress = null,
    int? lastReadMessageIndex = null,
    string lastReadTimestamp = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `dateCreated` | `DateTime?` | Form, Optional | The date on which this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date on which this resource was last updated. |
| `identity` | `string` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the [Conversation SDK](https://www.twilio.com/docs/conversations/sdk-overview) to communicate. Limited to 256 characters. |
| `attributes` | `string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set `{}` will be returned. |
| `roleSid` | `string` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `messagingBindingProxyAddress` | `string` | Form, Optional | The address of the Twilio phone number that the participant is in contact with. 'null' value will remove it. |
| `messagingBindingProjectedAddress` | `string` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. 'null' value will remove it. |
| `lastReadMessageIndex` | `int?` | Form, Optional | Index of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |
| `lastReadTimestamp` | `string` | Form, Optional | Timestamp of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversationParticipant](../../doc/models/service-conversation-participant.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
string sid = "Sid8";
DateTime? dateCreated = DateTime.ParseExact("12/16/2015 22:18:37", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? dateUpdated = DateTime.ParseExact("12/16/2015 22:18:38", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string attributes = "{ \"role\": \"driver\" }";
string roleSid = "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string messagingBindingProjectedAddress = "+15017122661";
try
{
    ApiResponse<ServiceConversationParticipant> result = await conversationsV1ParticipantApi.UpdateServiceConversationParticipantAsync(
        chatServiceSid,
        conversationSid,
        sid,
        null,
        dateCreated,
        dateUpdated,
        null,
        attributes,
        roleSid,
        null,
        messagingBindingProjectedAddress
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Delete Service Conversation Participant

Remove a participant from the conversation

```csharp
DeleteServiceConversationParticipantAsync(
    string chatServiceSid,
    string conversationSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. |
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
    await conversationsV1ParticipantApi.DeleteServiceConversationParticipantAsync(
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


# Fetch Service Conversation Participant

Fetch a participant of the conversation

```csharp
FetchServiceConversationParticipantAsync(
    string chatServiceSid,
    string conversationSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Alternatively, you can pass a Participant's `identity` rather than the SID. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversationParticipant](../../doc/models/service-conversation-participant.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string conversationSid = "ConversationSid0";
string sid = "Sid8";
try
{
    ApiResponse<ServiceConversationParticipant> result = await conversationsV1ParticipantApi.FetchServiceConversationParticipantAsync(
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

