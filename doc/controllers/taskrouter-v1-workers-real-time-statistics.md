# Taskrouter V1 Workers Real Time Statistics

```csharp
TaskrouterV1WorkersRealTimeStatisticsApi taskrouterV1WorkersRealTimeStatisticsApi = client.TaskrouterV1WorkersRealTimeStatisticsApi;
```

## Class Name

`TaskrouterV1WorkersRealTimeStatisticsApi`


# Fetch Workers Real Time Statistics

```csharp
FetchWorkersRealTimeStatisticsAsync(
    string workspaceSid,
    string taskChannel = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `taskChannel` | `string` | Query, Optional | Only calculate real-time statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.WorkersRealTimeStatistics](../../doc/models/workers-real-time-statistics.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
string taskChannel = "voice";
try
{
    ApiResponse<WorkersRealTimeStatistics> result = await taskrouterV1WorkersRealTimeStatisticsApi.FetchWorkersRealTimeStatisticsAsync(
        workspaceSid,
        taskChannel
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
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/RealTimeStatistics",
  "total_workers": 15,
  "activity_statistics": [
    {
      "friendly_name": "Idle",
      "workers": 0,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    },
    {
      "friendly_name": "Busy",
      "workers": 9,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    },
    {
      "friendly_name": "Offline",
      "workers": 6,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    },
    {
      "friendly_name": "Reserved",
      "workers": 0,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```

