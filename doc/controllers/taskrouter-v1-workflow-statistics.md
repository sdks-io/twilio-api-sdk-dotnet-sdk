# Taskrouter V1 Workflow Statistics

```csharp
TaskrouterV1WorkflowStatisticsApi taskrouterV1WorkflowStatisticsApi = client.TaskrouterV1WorkflowStatisticsApi;
```

## Class Name

`TaskrouterV1WorkflowStatisticsApi`


# Fetch Workflow Statistics

```csharp
FetchWorkflowStatisticsAsync(
    string workspaceSid,
    string workflowSid,
    int? minutes = null,
    DateTime? startDate = null,
    DateTime? endDate = null,
    string taskChannel = null,
    string splitByWaitTime = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Workflow to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `workflowSid` | `string` | Template, Required | Returns the list of Tasks that are being controlled by the Workflow with the specified SID value.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `minutes` | `int?` | Query, Optional | Only calculate statistics since this many minutes in the past. The default 15 minutes. This is helpful for displaying statistics for the last 15 minutes, 240 minutes (4 hours), and 480 minutes (8 hours) to see trends. |
| `startDate` | `DateTime?` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `endDate` | `DateTime?` | Query, Optional | Only calculate statistics from this date and time and earlier, specified in GMT as an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date-time. |
| `taskChannel` | `string` | Query, Optional | Only calculate real-time statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |
| `splitByWaitTime` | `string` | Query, Optional | A comma separated list of values that describes the thresholds, in seconds, to calculate statistics on. For each threshold specified, the number of Tasks canceled and reservations accepted above and below the specified thresholds in seconds are computed. For example, `5,30` would show splits of Tasks that were canceled or accepted before and after 5 seconds and before and after 30 seconds. This can be used to show short abandoned Tasks or Tasks that failed to meet an SLA. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.WorkflowStatistics](../../doc/models/workflow-statistics.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
string workflowSid = "WorkflowSid4";
int? minutes = 1;
DateTime? startDate = DateTime.ParseExact("01/02/2008 00:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? endDate = DateTime.ParseExact("01/02/2008 00:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
try
{
    ApiResponse<WorkflowStatistics> result = await taskrouterV1WorkflowStatisticsApi.FetchWorkflowStatisticsAsync(
        workspaceSid,
        workflowSid,
        minutes,
        startDate,
        endDate
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

