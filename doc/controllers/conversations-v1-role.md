# Conversations V1 Role

```csharp
ConversationsV1RoleApi conversationsV1RoleApi = client.ConversationsV1RoleApi;
```

## Class Name

`ConversationsV1RoleApi`

## Methods

* [Create Role](../../doc/controllers/conversations-v1-role.md#create-role)
* [List Role](../../doc/controllers/conversations-v1-role.md#list-role)
* [Update Role](../../doc/controllers/conversations-v1-role.md#update-role)
* [Delete Role](../../doc/controllers/conversations-v1-role.md#delete-role)
* [Fetch Role](../../doc/controllers/conversations-v1-role.md#fetch-role)
* [Create Service Role](../../doc/controllers/conversations-v1-role.md#create-service-role)
* [List Service Role](../../doc/controllers/conversations-v1-role.md#list-service-role)
* [Update Service Role](../../doc/controllers/conversations-v1-role.md#update-service-role)
* [Delete Service Role](../../doc/controllers/conversations-v1-role.md#delete-service-role)
* [Fetch Service Role](../../doc/controllers/conversations-v1-role.md#fetch-service-role)


# Create Role

Create a new user role in your account's default service

```csharp
CreateRoleAsync(
    string friendlyName,
    Models.RoleRoleType type,
    List<string> permission)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `friendlyName` | `string` | Form, Required | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `type` | [`RoleRoleType`](../../doc/models/role-role-type.md) | Form, Required | The type of role. Can be: `conversation` for [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) roles or `service` for [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) roles. |
| `permission` | `List<string>` | Form, Required | A permission that you grant to the new role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. The values for this parameter depend on the role's `type`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Role](../../doc/models/role.md).

## Example Usage

```csharp
string friendlyName = "Conversation Role";
RoleRoleType type = RoleRoleType.Conversation;
List<string> permission = new List<string>
{
    "Permission5",
};

try
{
    ApiResponse<Role> result = await conversationsV1RoleApi.CreateRoleAsync(
        friendlyName,
        type,
        permission
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
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Role

Retrieve a list of all user roles in your account's default service

```csharp
ListRoleAsync(
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

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListRoleResponse](../../doc/models/list-role-response.md).

## Example Usage

```csharp
try
{
    ApiResponse<ListRoleResponse> result = await conversationsV1RoleApi.ListRoleAsync();
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
    "first_page_url": "https://conversations.twilio.com/v1/Roles?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Roles?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "roles"
  },
  "roles": [
    {
      "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Conversation Role",
      "type": "conversation",
      "permissions": [
        "sendMessage",
        "leaveConversation",
        "editOwnMessage",
        "deleteOwnMessage"
      ],
      "date_created": "2016-03-03T19:47:15Z",
      "date_updated": "2016-03-03T19:47:15Z",
      "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Update Role

Update an existing user role in your account's default service

```csharp
UpdateRoleAsync(
    string sid,
    List<string> permission)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Role resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `permission` | `List<string>` | Form, Required | A permission that you grant to the role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. Note that the update action replaces all previously assigned permissions with those defined in the update action. To remove a permission, do not include it in the subsequent update action. The values for this parameter depend on the role's `type`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Role](../../doc/models/role.md).

## Example Usage

```csharp
string sid = "Sid8";
List<string> permission = new List<string>
{
    "Permission5",
};

try
{
    ApiResponse<Role> result = await conversationsV1RoleApi.UpdateRoleAsync(
        sid,
        permission
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
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Role

Remove a user role from your account's default service

```csharp
DeleteRoleAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Role resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

`Task`

## Example Usage

```csharp
string sid = "Sid8";
try
{
    await conversationsV1RoleApi.DeleteRoleAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Role

Fetch a user role from your account's default service

```csharp
FetchRoleAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Role resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Role](../../doc/models/role.md).

## Example Usage

```csharp
string sid = "Sid8";
try
{
    ApiResponse<Role> result = await conversationsV1RoleApi.FetchRoleAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Create Service Role

Create a new user role in your service

```csharp
CreateServiceRoleAsync(
    string chatServiceSid,
    string friendlyName,
    Models.ServiceRoleRoleType type,
    List<string> permission)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to create the Role resource under.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `friendlyName` | `string` | Form, Required | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `type` | [`ServiceRoleRoleType`](../../doc/models/service-role-role-type.md) | Form, Required | The type of role. Can be: `conversation` for [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) roles or `service` for [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) roles. |
| `permission` | `List<string>` | Form, Required | A permission that you grant to the new role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. The values for this parameter depend on the role's `type`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceRole](../../doc/models/service-role.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string friendlyName = "Conversation Role";
ServiceRoleRoleType type = ServiceRoleRoleType.Conversation;
List<string> permission = new List<string>
{
    "Permission5",
};

try
{
    ApiResponse<ServiceRole> result = await conversationsV1RoleApi.CreateServiceRoleAsync(
        chatServiceSid,
        friendlyName,
        type,
        permission
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
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Service Role

Retrieve a list of all user roles in your service

```csharp
ListServiceRoleAsync(
    string chatServiceSid,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to read the Role resources from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListServiceRoleResponse](../../doc/models/list-service-role-response.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
try
{
    ApiResponse<ListServiceRoleResponse> result = await conversationsV1RoleApi.ListServiceRoleAsync(chatServiceSid);
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
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "roles"
  },
  "roles": [
    {
      "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Conversation Role",
      "type": "conversation",
      "permissions": [
        "sendMessage",
        "leaveConversation",
        "editOwnMessage",
        "deleteOwnMessage"
      ],
      "date_created": "2016-03-03T19:47:15Z",
      "date_updated": "2016-03-03T19:47:15Z",
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Update Service Role

Update an existing user role in your service

```csharp
UpdateServiceRoleAsync(
    string chatServiceSid,
    string sid,
    List<string> permission)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to update the Role resource in.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Role resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `permission` | `List<string>` | Form, Required | A permission that you grant to the role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. Note that the update action replaces all previously assigned permissions with those defined in the update action. To remove a permission, do not include it in the subsequent update action. The values for this parameter depend on the role's `type`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceRole](../../doc/models/service-role.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string sid = "Sid8";
List<string> permission = new List<string>
{
    "Permission5",
};

try
{
    ApiResponse<ServiceRole> result = await conversationsV1RoleApi.UpdateServiceRoleAsync(
        chatServiceSid,
        sid,
        permission
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
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Service Role

Remove a user role from your service

```csharp
DeleteServiceRoleAsync(
    string chatServiceSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to delete the Role resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Role resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

`Task`

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string sid = "Sid8";
try
{
    await conversationsV1RoleApi.DeleteServiceRoleAsync(
        chatServiceSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Service Role

Fetch a user role from your service

```csharp
FetchServiceRoleAsync(
    string chatServiceSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to fetch the Role resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Role resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceRole](../../doc/models/service-role.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string sid = "Sid8";
try
{
    ApiResponse<ServiceRole> result = await conversationsV1RoleApi.FetchServiceRoleAsync(
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
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

