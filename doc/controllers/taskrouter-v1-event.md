# Taskrouter V1 Event

```csharp
TaskrouterV1EventApi taskrouterV1EventApi = client.TaskrouterV1EventApi;
```

## Class Name

`TaskrouterV1EventApi`

## Methods

* [Fetch Event](../../doc/controllers/taskrouter-v1-event.md#fetch-event)
* [List Event](../../doc/controllers/taskrouter-v1-event.md#list-event)


# Fetch Event

```csharp
FetchEventAsync(
    string workspaceSid,
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Event to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Event resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^EV[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Event](../../doc/models/event.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
string sid = "Sid8";
try
{
    ApiResponse<Event> result = await taskrouterV1EventApi.FetchEventAsync(
        workspaceSid,
        sid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# List Event

```csharp
ListEventAsync(
    string workspaceSid,
    DateTime? endDate = null,
    string eventType = null,
    int? minutes = null,
    string reservationSid = null,
    DateTime? startDate = null,
    string taskQueueSid = null,
    string taskSid = null,
    string workerSid = null,
    string workflowSid = null,
    string taskChannel = null,
    string sid = null,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Events to read. Returns only the Events that pertain to the specified Workspace.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `endDate` | `DateTime?` | Query, Optional | Only include Events that occurred on or before this date, specified in GMT as an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date-time. |
| `eventType` | `string` | Query, Optional | The type of Events to read. Returns only Events of the type specified. |
| `minutes` | `int?` | Query, Optional | The period of events to read in minutes. Returns only Events that occurred since this many minutes in the past. The default is `15` minutes. Task Attributes for Events occuring more 43,200 minutes ago will be redacted. |
| `reservationSid` | `string` | Query, Optional | The SID of the Reservation with the Events to read. Returns only Events that pertain to the specified Reservation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WR[0-9a-fA-F]{32}$` |
| `startDate` | `DateTime?` | Query, Optional | Only include Events from on or after this date and time, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. Task Attributes for Events older than 30 days will be redacted. |
| `taskQueueSid` | `string` | Query, Optional | The SID of the TaskQueue with the Events to read. Returns only the Events that pertain to the specified TaskQueue.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `taskSid` | `string` | Query, Optional | The SID of the Task with the Events to read. Returns only the Events that pertain to the specified Task.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `workerSid` | `string` | Query, Optional | The SID of the Worker with the Events to read. Returns only the Events that pertain to the specified Worker.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` |
| `workflowSid` | `string` | Query, Optional | The SID of the Workflow with the Events to read. Returns only the Events that pertain to the specified Workflow.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `taskChannel` | `string` | Query, Optional | The TaskChannel with the Events to read. Returns only the Events that pertain to the specified TaskChannel. |
| `sid` | `string` | Query, Optional | The SID of the Event resource to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^EV[0-9a-fA-F]{32}$` |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListEventResponse](../../doc/models/list-event-response.md).

## Example Usage

```csharp
string workspaceSid = "WorkspaceSid0";
DateTime? endDate = DateTime.ParseExact("01/03/2008 00:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string eventType = "reservation.created";
string reservationSid = "WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
DateTime? startDate = DateTime.ParseExact("01/02/2008 00:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind);
string taskQueueSid = "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string taskSid = "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string workerSid = "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string workflowSid = "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
try
{
    ApiResponse<ListEventResponse> result = await taskrouterV1EventApi.ListEventAsync(
        workspaceSid,
        endDate,
        eventType,
        null,
        reservationSid,
        startDate,
        taskQueueSid,
        taskSid,
        workerSid,
        workflowSid
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

