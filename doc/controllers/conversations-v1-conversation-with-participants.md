# Conversations V1 Conversation with Participants

```csharp
ConversationsV1ConversationWithParticipantsApi conversationsV1ConversationWithParticipantsApi = client.ConversationsV1ConversationWithParticipantsApi;
```

## Class Name

`ConversationsV1ConversationWithParticipantsApi`

## Methods

* [Create Conversation with Participants](../../doc/controllers/conversations-v1-conversation-with-participants.md#create-conversation-with-participants)
* [Create Service Conversation with Participants](../../doc/controllers/conversations-v1-conversation-with-participants.md#create-service-conversation-with-participants)


# Create Conversation with Participants

Create a new conversation with the list of participants in your account's default service

```csharp
CreateConversationWithParticipantsAsync(
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string friendlyName = null,
    string uniqueName = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string messagingServiceSid = null,
    string attributes = null,
    Models.ConversationWithParticipantsState? state = null,
    string timersInactive = null,
    string timersClosed = null,
    string bindingsEmailAddress = null,
    string bindingsEmailName = null,
    List<string> participant = null)
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
| `state` | [`ConversationWithParticipantsState?`](../../doc/models/conversation-with-participants-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timersInactive` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timersClosed` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `bindingsEmailAddress` | `string` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindingsEmailName` | `string` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |
| `participant` | `List<string>` | Form, Optional | The participant to be added to the conversation in JSON format. The JSON object attributes are as parameters in [Participant Resource](https://www.twilio.com/docs/conversations/api/conversation-participant-resource). The maximum number of participants that can be added in a single request is 10. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConversationWithParticipants](../../doc/models/conversation-with-participants.md).

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
ConversationWithParticipantsState? state = ConversationWithParticipantsState.Inactive;
string timersInactive = "PT1M";
string timersClosed = "PT10M";
try
{
    ApiResponse<ConversationWithParticipants> result = await conversationsV1ConversationWithParticipantsApi.CreateConversationWithParticipantsAsync(
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


# Create Service Conversation with Participants

Create a new conversation with the list of participants in your account's default service

```csharp
CreateServiceConversationWithParticipantsAsync(
    string chatServiceSid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string friendlyName = null,
    string uniqueName = null,
    DateTime? dateCreated = null,
    DateTime? dateUpdated = null,
    string messagingServiceSid = null,
    string attributes = null,
    Models.ServiceConversationWithParticipantsState? state = null,
    string timersInactive = null,
    string timersClosed = null,
    string bindingsEmailAddress = null,
    string bindingsEmailName = null,
    List<string> participant = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `string` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `uniqueName` | `string` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `dateCreated` | `DateTime?` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `DateTime?` | Form, Optional | The date that this resource was last updated. |
| `messagingServiceSid` | `string` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `attributes` | `string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `state` | [`ServiceConversationWithParticipantsState?`](../../doc/models/service-conversation-with-participants-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timersInactive` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timersClosed` | `string` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `bindingsEmailAddress` | `string` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindingsEmailName` | `string` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |
| `participant` | `List<string>` | Form, Optional | The participant to be added to the conversation in JSON format. The JSON object attributes are as parameters in [Participant Resource](https://www.twilio.com/docs/conversations/api/conversation-participant-resource). The maximum number of participants that can be added in a single request is 10. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceConversationWithParticipants](../../doc/models/service-conversation-with-participants.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
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
ServiceConversationWithParticipantsState? state = ServiceConversationWithParticipantsState.Inactive;
string timersInactive = "PT1M";
string timersClosed = "PT10M";
List<string> participant = new List<string>
{
    "{ \"identity\": \"user1\" }",
    "{ \"identity\": \"user2\" }",
};

try
{
    ApiResponse<ServiceConversationWithParticipants> result = await conversationsV1ConversationWithParticipantsApi.CreateServiceConversationWithParticipantsAsync(
        chatServiceSid,
        null,
        friendlyName,
        uniqueName,
        dateCreated,
        dateUpdated,
        messagingServiceSid,
        attributes,
        state,
        timersInactive,
        timersClosed,
        null,
        null,
        participant
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

