# Conversations V1 Notification

```csharp
ConversationsV1NotificationApi conversationsV1NotificationApi = client.ConversationsV1NotificationApi;
```

## Class Name

`ConversationsV1NotificationApi`

## Methods

* [Update Service Notification](../../doc/controllers/conversations-v1-notification.md#update-service-notification)
* [Fetch Service Notification](../../doc/controllers/conversations-v1-notification.md#fetch-service-notification)


# Update Service Notification

Update push notification service settings

```csharp
UpdateServiceNotificationAsync(
    string chatServiceSid,
    bool? logEnabled = null,
    bool? newMessageEnabled = null,
    string newMessageTemplate = null,
    string newMessageSound = null,
    bool? newMessageBadgeCountEnabled = null,
    bool? addedToConversationEnabled = null,
    string addedToConversationTemplate = null,
    string addedToConversationSound = null,
    bool? removedFromConversationEnabled = null,
    string removedFromConversationTemplate = null,
    string removedFromConversationSound = null,
    bool? newMessageWithMediaEnabled = null,
    string newMessageWithMediaTemplate = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Configuration applies to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `logEnabled` | `bool?` | Form, Optional | Weather the notification logging is enabled. |
| `newMessageEnabled` | `bool?` | Form, Optional | Whether to send a notification when a new message is added to a conversation. The default is `false`. |
| `newMessageTemplate` | `string` | Form, Optional | The template to use to create the notification text displayed when a new message is added to a conversation and `new_message.enabled` is `true`. |
| `newMessageSound` | `string` | Form, Optional | The name of the sound to play when a new message is added to a conversation and `new_message.enabled` is `true`. |
| `newMessageBadgeCountEnabled` | `bool?` | Form, Optional | Whether the new message badge is enabled. The default is `false`. |
| `addedToConversationEnabled` | `bool?` | Form, Optional | Whether to send a notification when a participant is added to a conversation. The default is `false`. |
| `addedToConversationTemplate` | `string` | Form, Optional | The template to use to create the notification text displayed when a participant is added to a conversation and `added_to_conversation.enabled` is `true`. |
| `addedToConversationSound` | `string` | Form, Optional | The name of the sound to play when a participant is added to a conversation and `added_to_conversation.enabled` is `true`. |
| `removedFromConversationEnabled` | `bool?` | Form, Optional | Whether to send a notification to a user when they are removed from a conversation. The default is `false`. |
| `removedFromConversationTemplate` | `string` | Form, Optional | The template to use to create the notification text displayed to a user when they are removed from a conversation and `removed_from_conversation.enabled` is `true`. |
| `removedFromConversationSound` | `string` | Form, Optional | The name of the sound to play to a user when they are removed from a conversation and `removed_from_conversation.enabled` is `true`. |
| `newMessageWithMediaEnabled` | `bool?` | Form, Optional | Whether to send a notification when a new message with media/file attachments is added to a conversation. The default is `false`. |
| `newMessageWithMediaTemplate` | `string` | Form, Optional | The template to use to create the notification text displayed when a new message with media/file attachments is added to a conversation and `new_message.attachments.enabled` is `true`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceNotification](../../doc/models/service-notification.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
bool? logEnabled = true;
bool? newMessageEnabled = false;
string newMessageTemplate = "You have a new message in ${CONVERSATION} from ${PARTICIPANT}: ${MESSAGE}";
string newMessageSound = "ring";
bool? newMessageBadgeCountEnabled = true;
bool? addedToConversationEnabled = false;
string addedToConversationTemplate = "You have been added to a Conversation: ${CONVERSATION}";
string addedToConversationSound = "ring";
bool? removedFromConversationEnabled = false;
string removedFromConversationTemplate = "You have been removed from a Conversation: ${CONVERSATION}";
string removedFromConversationSound = "ring";
bool? newMessageWithMediaEnabled = false;
string newMessageWithMediaTemplate = "You have a new message in ${CONVERSATION} with ${MEDIA_COUNT} media files: ${MEDIA}";
try
{
    ApiResponse<ServiceNotification> result = await conversationsV1NotificationApi.UpdateServiceNotificationAsync(
        chatServiceSid,
        logEnabled,
        newMessageEnabled,
        newMessageTemplate,
        newMessageSound,
        newMessageBadgeCountEnabled,
        addedToConversationEnabled,
        addedToConversationTemplate,
        addedToConversationSound,
        removedFromConversationEnabled,
        removedFromConversationTemplate,
        removedFromConversationSound,
        newMessageWithMediaEnabled,
        newMessageWithMediaTemplate
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Service Notification

Fetch push notification service settings

```csharp
FetchServiceNotificationAsync(
    string chatServiceSid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Configuration applies to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceNotification](../../doc/models/service-notification.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
try
{
    ApiResponse<ServiceNotification> result = await conversationsV1NotificationApi.FetchServiceNotificationAsync(chatServiceSid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

