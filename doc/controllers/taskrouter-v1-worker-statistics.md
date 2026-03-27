# Taskrouter V1 Worker Statistics

```csharp
TaskrouterV1WorkerStatisticsApi taskrouterV1WorkerStatisticsApi = client.TaskrouterV1WorkerStatisticsApi;
```

## Class Name

`TaskrouterV1WorkerStatisticsApi`


# Fetch Worker Instance Statistics

```csharp
FetchWorkerInstanceStatisticsAsync(
    string workspaceSid,
    string workerSid,
    int? minutes = null,
    DateTime? startDate = null,
    DateTime? endDate = null,
    string taskChannel = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the WorkerChannel to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `workerSid` | `string` | Template, Required | The SID of the Worker with the WorkerChannel to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` |
| `minutes` | `int?` | Query, Optional | Only calculate statistics since this many minutes in the past. The default 15 minutes. This is helpful for displaying statistics for the last 15 minutes, 240 minutes (4 hours), and 480 minutes (8 hours) to see trends. |
| `startDate` | `DateTime?` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `endDate` | `DateTime?` | Query, Optional | Only include usage that occurred on or before this date, specified in GMT as an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date-time. |
| `taskChannel` | `string` | Query, Optional | Only calculate statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.WorkerInstanceStatistics](../../doc/models/worker-instance-statistics.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
string workerSid = "WorkerSid0";
int? minutes = 1;
DateTime? startDate = DateTime.ParseExact("01/02/2008 00:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? endDate = DateTime.ParseExact("01/02/2008 00:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
try
{
    ApiResponse<WorkerInstanceStatistics> result = await taskrouterV1WorkerStatisticsApi.FetchWorkerInstanceStatisticsAsync(
        workspaceSid,
        workerSid,
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

