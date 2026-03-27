# Taskrouter V1 Workflow Real Time Statistics

```csharp
TaskrouterV1WorkflowRealTimeStatisticsApi taskrouterV1WorkflowRealTimeStatisticsApi = client.TaskrouterV1WorkflowRealTimeStatisticsApi;
```

## Class Name

`TaskrouterV1WorkflowRealTimeStatisticsApi`


# Fetch Workflow Real Time Statistics

```csharp
FetchWorkflowRealTimeStatisticsAsync(
    string workspaceSid,
    string workflowSid,
    string taskChannel = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Workflow to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `workflowSid` | `string` | Template, Required | Returns the list of Tasks that are being controlled by the Workflow with the specified SID value.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `taskChannel` | `string` | Query, Optional | Only calculate real-time statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.WorkflowRealTimeStatistics](../../doc/models/workflow-real-time-statistics.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
string workflowSid = "WorkflowSid4";
string taskChannel = "voice";
try
{
    ApiResponse<WorkflowRealTimeStatistics> result = await taskrouterV1WorkflowRealTimeStatisticsApi.FetchWorkflowRealTimeStatisticsAsync(
        workspaceSid,
        workflowSid,
        taskChannel
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

