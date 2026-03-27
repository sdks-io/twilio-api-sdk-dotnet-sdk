# Taskrouter V1 Workers Statistics

```csharp
TaskrouterV1WorkersStatisticsApi taskrouterV1WorkersStatisticsApi = client.TaskrouterV1WorkersStatisticsApi;
```

## Class Name

`TaskrouterV1WorkersStatisticsApi`


# Fetch Worker Statistics

```csharp
FetchWorkerStatisticsAsync(
    string workspaceSid,
    int? minutes = null,
    DateTime? startDate = null,
    DateTime? endDate = null,
    string taskQueueSid = null,
    string taskQueueName = null,
    string friendlyName = null,
    string taskChannel = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Worker to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `minutes` | `int?` | Query, Optional | Only calculate statistics since this many minutes in the past. The default 15 minutes. This is helpful for displaying statistics for the last 15 minutes, 240 minutes (4 hours), and 480 minutes (8 hours) to see trends. |
| `startDate` | `DateTime?` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `endDate` | `DateTime?` | Query, Optional | Only calculate statistics from this date and time and earlier, specified in GMT as an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date-time. |
| `taskQueueSid` | `string` | Query, Optional | The SID of the TaskQueue for which to fetch Worker statistics.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `taskQueueName` | `string` | Query, Optional | The `friendly_name` of the TaskQueue for which to fetch Worker statistics. |
| `friendlyName` | `string` | Query, Optional | Only include Workers with `friendly_name` values that match this parameter. |
| `taskChannel` | `string` | Query, Optional | Only calculate statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.WorkerStatistics](../../doc/models/worker-statistics.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
int? minutes = 1;
DateTime? startDate = DateTime.ParseExact("01/02/2008 00:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
DateTime? endDate = DateTime.ParseExact("01/02/2008 00:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
try
{
    ApiResponse<WorkerStatistics> result = await taskrouterV1WorkersStatisticsApi.FetchWorkerStatisticsAsync(
        workspaceSid,
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

