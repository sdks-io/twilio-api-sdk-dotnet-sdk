# Conversations V1 User Conversation

```csharp
ConversationsV1UserConversationApi conversationsV1UserConversationApi = client.ConversationsV1UserConversationApi;
```

## Class Name

`ConversationsV1UserConversationApi`

## Methods

* [Update Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#update-service-user-conversation)
* [Delete Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#delete-service-user-conversation)
* [Fetch Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#fetch-service-user-conversation)
* [List Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#list-service-user-conversation)
* [Update User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#update-user-conversation)
* [Delete User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#delete-user-conversation)
* [Fetch User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#fetch-user-conversation)
* [List User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#list-user-conversation)


# Update Service User Conversation

Update a specific User Conversation.

```csharp
UpdateServiceUserConversationAsync(
    string chatServiceSid,
    string userSid,
    string conversationSid,
    Models.ServiceUserConversationNotificationLevel? notificationLevel = null,
    DateTime? lastReadTimestamp = null,
    int? lastReadMessageIndex = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |
| `notificationLevel` | [`ServiceUserConversationNotificationLevel?`](../../doc/models/service-user-conversation-notification-level.md) | Form, Optional | The Notification Level of this User Conversation. One of `default` or `muted`. |
| `lastReadTimestamp` | `DateTime?` | Form, Optional | The date of the last message read in conversation by the user, given in ISO 8601 format. |
| `lastReadMessageIndex` | `int?` | Form, Optional | The index of the last Message in the Conversation that the Participant has read. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceUserConversation](../../doc/models/service-user-conversation.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string userSid = "UserSid6";
string conversationSid = "ConversationSid0";
ServiceUserConversationNotificationLevel? notificationLevel = ServiceUserConversationNotificationLevel.Default;
DateTime? lastReadTimestamp = DateTime.ParseExact("07/30/2015 20:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
int? lastReadMessageIndex = 100;
try
{
    ApiResponse<ServiceUserConversation> result = await conversationsV1UserConversationApi.UpdateServiceUserConversationAsync(
        chatServiceSid,
        userSid,
        conversationSid,
        notificationLevel,
        lastReadTimestamp,
        lastReadMessageIndex
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Delete Service User Conversation

Delete a specific User Conversation.

```csharp
DeleteServiceUserConversationAsync(
    string chatServiceSid,
    string userSid,
    string conversationSid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Response Type

`Task`

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string userSid = "UserSid6";
string conversationSid = "ConversationSid0";
try
{
    await conversationsV1UserConversationApi.DeleteServiceUserConversationAsync(
        chatServiceSid,
        userSid,
        conversationSid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Service User Conversation

Fetch a specific User Conversation.

```csharp
FetchServiceUserConversationAsync(
    string chatServiceSid,
    string userSid,
    string conversationSid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceUserConversation](../../doc/models/service-user-conversation.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string userSid = "UserSid6";
string conversationSid = "ConversationSid0";
try
{
    ApiResponse<ServiceUserConversation> result = await conversationsV1UserConversationApi.FetchServiceUserConversationAsync(
        chatServiceSid,
        userSid,
        conversationSid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# List Service User Conversation

Retrieve a list of all User Conversations for the User.

```csharp
ListServiceUserConversationAsync(
    string chatServiceSid,
    string userSid,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListServiceUserConversationResponse](../../doc/models/list-service-user-conversation-response.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string userSid = "UserSid6";
try
{
    ApiResponse<ListServiceUserConversationResponse> result = await conversationsV1UserConversationApi.ListServiceUserConversationAsync(
        chatServiceSid,
        userSid
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
  "conversations": [],
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "conversations"
  }
}
```


# Update User Conversation

Update a specific User Conversation.

```csharp
UpdateUserConversationAsync(
    string userSid,
    string conversationSid,
    Models.UserConversationNotificationLevel? notificationLevel = null,
    DateTime? lastReadTimestamp = null,
    int? lastReadMessageIndex = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |
| `notificationLevel` | [`UserConversationNotificationLevel?`](../../doc/models/user-conversation-notification-level.md) | Form, Optional | The Notification Level of this User Conversation. One of `default` or `muted`. |
| `lastReadTimestamp` | `DateTime?` | Form, Optional | The date of the last message read in conversation by the user, given in ISO 8601 format. |
| `lastReadMessageIndex` | `int?` | Form, Optional | The index of the last Message in the Conversation that the Participant has read. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.UserConversation](../../doc/models/user-conversation.md).

## Example Usage

```csharp
string userSid = "UserSid6";
string conversationSid = "ConversationSid0";
UserConversationNotificationLevel? notificationLevel = UserConversationNotificationLevel.Default;
DateTime? lastReadTimestamp = DateTime.ParseExact("07/30/2015 20:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
int? lastReadMessageIndex = 100;
try
{
    ApiResponse<UserConversation> result = await conversationsV1UserConversationApi.UpdateUserConversationAsync(
        userSid,
        conversationSid,
        notificationLevel,
        lastReadTimestamp,
        lastReadMessageIndex
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Delete User Conversation

Delete a specific User Conversation.

```csharp
DeleteUserConversationAsync(
    string userSid,
    string conversationSid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Response Type

`Task`

## Example Usage

```csharp
string userSid = "UserSid6";
string conversationSid = "ConversationSid0";
try
{
    await conversationsV1UserConversationApi.DeleteUserConversationAsync(
        userSid,
        conversationSid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch User Conversation

Fetch a specific User Conversation.

```csharp
FetchUserConversationAsync(
    string userSid,
    string conversationSid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.UserConversation](../../doc/models/user-conversation.md).

## Example Usage

```csharp
string userSid = "UserSid6";
string conversationSid = "ConversationSid0";
try
{
    ApiResponse<UserConversation> result = await conversationsV1UserConversationApi.FetchUserConversationAsync(
        userSid,
        conversationSid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# List User Conversation

Retrieve a list of all User Conversations for the User.

```csharp
ListUserConversationAsync(
    string userSid,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListUserConversationResponse](../../doc/models/list-user-conversation-response.md).

## Example Usage

```csharp
string userSid = "UserSid6";
try
{
    ApiResponse<ListUserConversationResponse> result = await conversationsV1UserConversationApi.ListUserConversationAsync(userSid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "conversations": [],
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "conversations"
  }
}
```

