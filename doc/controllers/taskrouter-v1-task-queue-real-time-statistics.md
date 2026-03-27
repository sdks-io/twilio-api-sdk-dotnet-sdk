# Taskrouter V1 Task Queue Real Time Statistics

```csharp
TaskrouterV1TaskQueueRealTimeStatisticsApi taskrouterV1TaskQueueRealTimeStatisticsApi = client.TaskrouterV1TaskQueueRealTimeStatisticsApi;
```

## Class Name

`TaskrouterV1TaskQueueRealTimeStatisticsApi`


# Fetch Task Queue Real Time Statistics

```csharp
FetchTaskQueueRealTimeStatisticsAsync(
    string workspaceSid,
    string taskQueueSid,
    string taskChannel = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the TaskQueue to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `taskQueueSid` | `string` | Template, Required | The SID of the TaskQueue for which to fetch statistics.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `taskChannel` | `string` | Query, Optional | The TaskChannel for which to fetch statistics. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.TaskQueueRealTimeStatistics](../../doc/models/task-queue-real-time-statistics.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
string taskQueueSid = "TaskQueueSid8";
string taskChannel = "voice";
try
{
    ApiResponse<TaskQueueRealTimeStatistics> result = await taskrouterV1TaskQueueRealTimeStatisticsApi.FetchTaskQueueRealTimeStatisticsAsync(
        workspaceSid,
        taskQueueSid,
        taskChannel
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

