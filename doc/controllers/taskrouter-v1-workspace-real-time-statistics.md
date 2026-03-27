# Taskrouter V1 Workspace Real Time Statistics

```csharp
TaskrouterV1WorkspaceRealTimeStatisticsApi taskrouterV1WorkspaceRealTimeStatisticsApi = client.TaskrouterV1WorkspaceRealTimeStatisticsApi;
```

## Class Name

`TaskrouterV1WorkspaceRealTimeStatisticsApi`


# Fetch Workspace Real Time Statistics

```csharp
FetchWorkspaceRealTimeStatisticsAsync(
    string workspaceSid,
    string taskChannel = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `taskChannel` | `string` | Query, Optional | Only calculate real-time statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.WorkspaceRealTimeStatistics](../../doc/models/workspace-real-time-statistics.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
string taskChannel = "voice";
try
{
    ApiResponse<WorkspaceRealTimeStatistics> result = await taskrouterV1WorkspaceRealTimeStatisticsApi.FetchWorkspaceRealTimeStatisticsAsync(
        workspaceSid,
        taskChannel
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

