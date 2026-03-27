# Conversations V1 User

```csharp
ConversationsV1UserApi conversationsV1UserApi = client.ConversationsV1UserApi;
```

## Class Name

`ConversationsV1UserApi`

## Methods

* [Create Service User](../../doc/controllers/conversations-v1-user.md#create-service-user)
* [List Service User](../../doc/controllers/conversations-v1-user.md#list-service-user)
* [Update Service User](../../doc/controllers/conversations-v1-user.md#update-service-user)
* [Delete Service User](../../doc/controllers/conversations-v1-user.md#delete-service-user)
* [Fetch Service User](../../doc/controllers/conversations-v1-user.md#fetch-service-user)
* [Create User](../../doc/controllers/conversations-v1-user.md#create-user)
* [List User](../../doc/controllers/conversations-v1-user.md#list-user)
* [Update User](../../doc/controllers/conversations-v1-user.md#update-user)
* [Delete User](../../doc/controllers/conversations-v1-user.md#delete-user)
* [Fetch User](../../doc/controllers/conversations-v1-user.md#fetch-user)


# Create Service User

Add a new conversation user to your service

```csharp
CreateServiceUserAsync(
    string chatServiceSid,
    string identity,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string friendlyName = null,
    string attributes = null,
    string roleSid = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the User resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `identity` | `string` | Form, Required | The application-defined string that uniquely identifies the resource's User within the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource). This value is often a username or an email address, and is case-sensitive. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `string` | Form, Optional | The string that you assigned to describe the resource. |
| `attributes` | `string` | Form, Optional | The JSON Object string that stores application-specific data. If attributes have not been set, `{}` is returned. |
| `roleSid` | `string` | Form, Optional | The SID of a service-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the user.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceUser](../../doc/models/service-user.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string identity = "admin";
string friendlyName = "name";
string attributes = "{ \"duty\": \"tech\" }";
string roleSid = "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
try
{
    ApiResponse<ServiceUser> result = await conversationsV1UserApi.CreateServiceUserAsync(
        chatServiceSid,
        identity,
        null,
        friendlyName,
        attributes,
        roleSid
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
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "name",
  "attributes": "{ \"duty\": \"tech\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```


# List Service User

Retrieve a list of all conversation users in your service

```csharp
ListServiceUserAsync(
    string chatServiceSid,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to read the User resources from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListServiceUserResponse](../../doc/models/list-service-user-response.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
try
{
    ApiResponse<ListServiceUserResponse> result = await conversationsV1UserApi.ListServiceUserAsync(chatServiceSid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "users"
  },
  "users": [
    {
      "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "identity": "admin",
      "friendly_name": "name",
      "attributes": "{ \"duty\": \"tech\" }",
      "is_online": true,
      "is_notifiable": null,
      "date_created": "2019-12-16T22:18:37Z",
      "date_updated": "2019-12-16T22:18:38Z",
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "user_conversations": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
      }
    },
    {
      "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "identity": "agent0034",
      "friendly_name": "John from customs",
      "attributes": "{ \"duty\": \"agent\" }",
      "is_online": false,
      "is_notifiable": null,
      "date_created": "2020-03-24T20:38:21Z",
      "date_updated": "2020-03-24T20:38:21Z",
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "user_conversations": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
      }
    }
  ]
}
```


# Update Service User

Update an existing conversation user in your service

```csharp
UpdateServiceUserAsync(
    string chatServiceSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string friendlyName = null,
    string attributes = null,
    string roleSid = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the User resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the User resource to update. This value can be either the `sid` or the `identity` of the User resource to update. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `string` | Form, Optional | The string that you assigned to describe the resource. |
| `attributes` | `string` | Form, Optional | The JSON Object string that stores application-specific data. If attributes have not been set, `{}` is returned. |
| `roleSid` | `string` | Form, Optional | The SID of a service-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the user.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceUser](../../doc/models/service-user.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string sid = "Sid8";
string friendlyName = "new name";
string attributes = "{ \"duty\": \"tech\", \"team\": \"internals\" }";
string roleSid = "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
try
{
    ApiResponse<ServiceUser> result = await conversationsV1UserApi.UpdateServiceUserAsync(
        chatServiceSid,
        sid,
        null,
        friendlyName,
        attributes,
        roleSid
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
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "new name",
  "attributes": "{ \"duty\": \"tech\", \"team\": \"internals\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```


# Delete Service User

Remove a conversation user from your service

```csharp
DeleteServiceUserAsync(
    string chatServiceSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to delete the User resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the User resource to delete. This value can be either the `sid` or the `identity` of the User resource to delete. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

`Task`

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string sid = "Sid8";
try
{
    await conversationsV1UserApi.DeleteServiceUserAsync(
        chatServiceSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Service User

Fetch a conversation user from your service

```csharp
FetchServiceUserAsync(
    string chatServiceSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to fetch the User resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the User resource to fetch. This value can be either the `sid` or the `identity` of the User resource to fetch. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceUser](../../doc/models/service-user.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string sid = "Sid8";
try
{
    ApiResponse<ServiceUser> result = await conversationsV1UserApi.FetchServiceUserAsync(
        chatServiceSid,
        sid
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
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "name",
  "attributes": "{ \"duty\": \"tech\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```


# Create User

Add a new conversation user to your account's default service

```csharp
CreateUserAsync(
    string identity,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string friendlyName = null,
    string attributes = null,
    string roleSid = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `identity` | `string` | Form, Required | The application-defined string that uniquely identifies the resource's User within the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource). This value is often a username or an email address, and is case-sensitive. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `string` | Form, Optional | The string that you assigned to describe the resource. |
| `attributes` | `string` | Form, Optional | The JSON Object string that stores application-specific data. If attributes have not been set, `{}` is returned. |
| `roleSid` | `string` | Form, Optional | The SID of a service-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the user.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.User](../../doc/models/user.md).

## Example Usage

```csharp
string identity = "admin";
string friendlyName = "name";
string attributes = "{ \"duty\": \"tech\" }";
string roleSid = "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
try
{
    ApiResponse<User> result = await conversationsV1UserApi.CreateUserAsync(
        identity,
        null,
        friendlyName,
        attributes,
        roleSid
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
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "name",
  "attributes": "{ \"duty\": \"tech\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```


# List User

Retrieve a list of all conversation users in your account's default service

```csharp
ListUserAsync(
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListUserResponse](../../doc/models/list-user-response.md).

## Example Usage

```csharp
try
{
    ApiResponse<ListUserResponse> result = await conversationsV1UserApi.ListUserAsync();
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Users?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Users?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "users"
  },
  "users": [
    {
      "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "identity": "admin",
      "friendly_name": "name",
      "attributes": "{ \"duty\": \"tech\" }",
      "is_online": true,
      "is_notifiable": null,
      "date_created": "2019-12-16T22:18:37Z",
      "date_updated": "2019-12-16T22:18:38Z",
      "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "user_conversations": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
      }
    },
    {
      "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "identity": "agent0034",
      "friendly_name": "John from customs",
      "attributes": "{ \"duty\": \"agent\" }",
      "is_online": false,
      "is_notifiable": null,
      "date_created": "2020-03-24T20:38:21Z",
      "date_updated": "2020-03-24T20:38:21Z",
      "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "user_conversations": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
      }
    }
  ]
}
```


# Update User

Update an existing conversation user in your account's default service

```csharp
UpdateUserAsync(
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    string friendlyName = null,
    string attributes = null,
    string roleSid = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the User resource to update. This value can be either the `sid` or the `identity` of the User resource to update. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `string` | Form, Optional | The string that you assigned to describe the resource. |
| `attributes` | `string` | Form, Optional | The JSON Object string that stores application-specific data. If attributes have not been set, `{}` is returned. |
| `roleSid` | `string` | Form, Optional | The SID of a service-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the user.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.User](../../doc/models/user.md).

## Example Usage

```csharp
string sid = "Sid8";
string friendlyName = "new name";
string attributes = "{ \"duty\": \"tech\", \"team\": \"internals\" }";
string roleSid = "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
try
{
    ApiResponse<User> result = await conversationsV1UserApi.UpdateUserAsync(
        sid,
        null,
        friendlyName,
        attributes,
        roleSid
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
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "new name",
  "attributes": "{ \"duty\": \"tech\", \"team\": \"internals\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```


# Delete User

Remove a conversation user from your account's default service

```csharp
DeleteUserAsync(
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the User resource to delete. This value can be either the `sid` or the `identity` of the User resource to delete. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

`Task`

## Example Usage

```csharp
string sid = "Sid8";
try
{
    await conversationsV1UserApi.DeleteUserAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch User

Fetch a conversation user from your account's default service

```csharp
FetchUserAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the User resource to fetch. This value can be either the `sid` or the `identity` of the User resource to fetch. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.User](../../doc/models/user.md).

## Example Usage

```csharp
string sid = "Sid8";
try
{
    ApiResponse<User> result = await conversationsV1UserApi.FetchUserAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "name",
  "attributes": "{ \"duty\": \"tech\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```

