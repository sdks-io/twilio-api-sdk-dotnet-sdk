# Taskrouter V1 Workspace Cumulative Statistics

```csharp
TaskrouterV1WorkspaceCumulativeStatisticsApi taskrouterV1WorkspaceCumulativeStatisticsApi = client.TaskrouterV1WorkspaceCumulativeStatisticsApi;
```

## Class Name

`TaskrouterV1WorkspaceCumulativeStatisticsApi`


# Fetch Workspace Cumulative Statistics

```csharp
FetchWorkspaceCumulativeStatisticsAsync(
    string workspaceSid,
    DateTime? endDate = null,
    int? minutes = null,
    DateTime? startDate = null,
    string taskChannel = null,
    string splitByWaitTime = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `endDate` | `DateTime?` | Query, Optional | Only include usage that occurred on or before this date, specified in GMT as an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date-time. |
| `minutes` | `int?` | Query, Optional | Only calculate statistics since this many minutes in the past. The default 15 minutes. This is helpful for displaying statistics for the last 15 minutes, 240 minutes (4 hours), and 480 minutes (8 hours) to see trends. |
| `startDate` | `DateTime?` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `taskChannel` | `string` | Query, Optional | Only calculate cumulative statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |
| `splitByWaitTime` | `string` | Query, Optional | A comma separated list of values that describes the thresholds, in seconds, to calculate statistics on. For each threshold specified, the number of Tasks canceled and reservations accepted above and below the specified thresholds in seconds are computed. For example, `5,30` would show splits of Tasks that were canceled or accepted before and after 5 seconds and before and after 30 seconds. This can be used to show short abandoned Tasks or Tasks that failed to meet an SLA. TaskRouter will calculate statistics on up to 10,000 Tasks for any given threshold. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.WorkspaceCumulativeStatistics](../../doc/models/workspace-cumulative-statistics.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
DateTime? endDate = DateTime.ParseExact("07/30/2015 20:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? startDate = DateTime.ParseExact("07/30/2015 20:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
try
{
    ApiResponse<WorkspaceCumulativeStatistics> result = await taskrouterV1WorkspaceCumulativeStatisticsApi.FetchWorkspaceCumulativeStatisticsAsync(
        workspaceSid,
        endDate,
        null,
        startDate
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

