# Conversations V1 Binding

```csharp
ConversationsV1BindingApi conversationsV1BindingApi = client.ConversationsV1BindingApi;
```

## Class Name

`ConversationsV1BindingApi`

## Methods

* [Delete Service Binding](../../doc/controllers/conversations-v1-binding.md#delete-service-binding)
* [Fetch Service Binding](../../doc/controllers/conversations-v1-binding.md#fetch-service-binding)
* [List Service Binding](../../doc/controllers/conversations-v1-binding.md#list-service-binding)


# Delete Service Binding

Remove a push notification binding from the conversation service

```csharp
DeleteServiceBindingAsync(
    string chatServiceSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to delete the Binding resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Binding resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^BS[0-9a-fA-F]{32}$` |

## Response Type

`Task`

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string sid = "Sid8";
try
{
    await conversationsV1BindingApi.DeleteServiceBindingAsync(
        chatServiceSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Service Binding

Fetch a push notification binding from the conversation service

```csharp
FetchServiceBindingAsync(
    string chatServiceSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Binding resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^BS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ServiceBinding](../../doc/models/service-binding.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
string sid = "Sid8";
try
{
    ApiResponse<ServiceBinding> result = await conversationsV1BindingApi.FetchServiceBindingAsync(
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
  "sid": "BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2016-10-21T11:37:03Z",
  "date_updated": "2016-10-21T11:37:03Z",
  "endpoint": "TestUser-endpoint",
  "identity": "TestUser",
  "binding_type": "gcm",
  "credential_sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "message_types": [
    "removed_from_conversation",
    "new_message",
    "added_to_conversation"
  ],
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings/BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Service Binding

Retrieve a list of all push notification bindings in the conversation service

```csharp
ListServiceBindingAsync(
    string chatServiceSid,
    List<Models.ServiceBindingBindingType> bindingType = null,
    List<string> identity = null,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Binding resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `bindingType` | [`List<ServiceBindingBindingType>`](../../doc/models/service-binding-binding-type.md) | Query, Optional | The push technology used by the Binding resources to read.  Can be: `apn`, `gcm`, `fcm`, or `twilsock`.  See [push notification configuration](https://www.twilio.com/docs/chat/push-notification-configuration) for more info. |
| `identity` | `List<string>` | Query, Optional | The identity of a [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource) this binding belongs to. See [access tokens](https://www.twilio.com/docs/conversations/create-tokens) for more details. |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListServiceBindingResponse](../../doc/models/list-service-binding-response.md).

## Example Usage

```csharp
string chatServiceSid = "ChatServiceSid4";
try
{
    ApiResponse<ListServiceBindingResponse> result = await conversationsV1BindingApi.ListServiceBindingAsync(chatServiceSid);
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
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "bindings"
  },
  "bindings": [
    {
      "sid": "BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2016-10-21T11:37:03Z",
      "date_updated": "2016-10-21T11:37:03Z",
      "endpoint": "TestUser-endpoint",
      "identity": "TestUser",
      "binding_type": "gcm",
      "credential_sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "message_types": [
        "removed_from_conversation",
        "new_message",
        "added_to_conversation"
      ],
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings/BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```

