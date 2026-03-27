# Taskrouter V1 Task Channel

```csharp
TaskrouterV1TaskChannelApi taskrouterV1TaskChannelApi = client.TaskrouterV1TaskChannelApi;
```

## Class Name

`TaskrouterV1TaskChannelApi`

## Methods

* [Fetch Task Channel](../../doc/controllers/taskrouter-v1-task-channel.md#fetch-task-channel)
* [Update Task Channel](../../doc/controllers/taskrouter-v1-task-channel.md#update-task-channel)
* [Delete Task Channel](../../doc/controllers/taskrouter-v1-task-channel.md#delete-task-channel)
* [List Task Channel](../../doc/controllers/taskrouter-v1-task-channel.md#list-task-channel)
* [Create Task Channel](../../doc/controllers/taskrouter-v1-task-channel.md#create-task-channel)


# Fetch Task Channel

Types of tasks

```csharp
FetchTaskChannelAsync(
    string workspaceSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Task Channel to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Task Channel resource to fetch. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.TaskChannel](../../doc/models/task-channel.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
string sid = "Sid8";
try
{
    ApiResponse<TaskChannel> result = await taskrouterV1TaskChannelApi.FetchTaskChannelAsync(
        workspaceSid,
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
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2016-04-14T17:35:54Z",
  "date_updated": "2016-04-14T17:35:54Z",
  "friendly_name": "Default",
  "sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "unique_name": "default",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskChannels/TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "channel_optimized_routing": true,
  "links": {
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
  }
}
```


# Update Task Channel

Types of tasks

```csharp
UpdateTaskChannelAsync(
    string workspaceSid,
    string sid,
    string friendlyName = null,
    bool? channelOptimizedRouting = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Task Channel to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Task Channel resource to update. |
| `friendlyName` | `string` | Form, Optional | A descriptive string that you create to describe the Task Channel. It can be up to 64 characters long. |
| `channelOptimizedRouting` | `bool?` | Form, Optional | Whether the TaskChannel should prioritize Workers that have been idle. If `true`, Workers that have been idle the longest are prioritized. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.TaskChannel](../../doc/models/task-channel.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
string sid = "Sid8";
string friendlyName = "Outbound Voice";
bool? channelOptimizedRouting = true;
try
{
    ApiResponse<TaskChannel> result = await taskrouterV1TaskChannelApi.UpdateTaskChannelAsync(
        workspaceSid,
        sid,
        friendlyName,
        channelOptimizedRouting
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
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Default",
  "unique_name": "default",
  "date_created": "2016-04-14T17:35:54Z",
  "date_updated": "2016-04-14T17:35:54Z",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskChannels/TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "channel_optimized_routing": true,
  "links": {
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
  }
}
```


# Delete Task Channel

Types of tasks

```csharp
DeleteTaskChannelAsync(
    string workspaceSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Task Channel to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Task Channel resource to delete. |

## Response Type

`Task`

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
string sid = "Sid8";
try
{
    await taskrouterV1TaskChannelApi.DeleteTaskChannelAsync(
        workspaceSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# List Task Channel

Types of tasks

```csharp
ListTaskChannelAsync(
    string workspaceSid,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Task Channel to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListTaskChannelResponse](../../doc/models/list-task-channel-response.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
try
{
    ApiResponse<ListTaskChannelResponse> result = await taskrouterV1TaskChannelApi.ListTaskChannelAsync(workspaceSid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "channels": [
    {
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2016-04-14T17:35:54Z",
      "date_updated": "2016-04-14T17:35:54Z",
      "friendly_name": "Default",
      "sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "unique_name": "default",
      "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskChannels/TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "channel_optimized_routing": true,
      "links": {
        "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
      }
    }
  ],
  "meta": {
    "first_page_url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskChannels?PageSize=50&Page=0",
    "key": "channels",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskChannels?PageSize=50&Page=0"
  }
}
```


# Create Task Channel

Types of tasks

```csharp
CreateTaskChannelAsync(
    string workspaceSid,
    string friendlyName,
    string uniqueName,
    bool? channelOptimizedRouting = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace that the new Task Channel belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `friendlyName` | `string` | Form, Required | A descriptive string that you create to describe the Task Channel. It can be up to 64 characters long. |
| `uniqueName` | `string` | Form, Required | An application-defined string that uniquely identifies the Task Channel, such as `voice` or `sms`. |
| `channelOptimizedRouting` | `bool?` | Form, Optional | Whether the Task Channel should prioritize Workers that have been idle. If `true`, Workers that have been idle the longest are prioritized. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.TaskChannel](../../doc/models/task-channel.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
string friendlyName = "Outbound Voice";
string uniqueName = "ovoice";
try
{
    ApiResponse<TaskChannel> result = await taskrouterV1TaskChannelApi.CreateTaskChannelAsync(
        workspaceSid,
        friendlyName,
        uniqueName
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
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Outbound Voice",
  "unique_name": "ovoice",
  "date_created": "2016-04-14T17:35:54Z",
  "date_updated": "2016-04-14T17:35:54Z",
  "channel_optimized_routing": true,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskChannels/TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
  }
}
```

