# Chat V3 Channel

```csharp
ChatV3ChannelApi chatV3ChannelApi = client.ChatV3ChannelApi;
```

## Class Name

`ChatV3ChannelApi`


# Update Channel

Update a specific Channel.

```csharp
UpdateChannelAsync(
    string serviceSid,
    string sid,
    Models.ChannelWebhookEnabledType? xTwilioWebhookEnabled = null,
    Models.ChannelChannelType? type = null,
    string messagingServiceSid = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `serviceSid` | `string` | Template, Required | The unique SID identifier of the Service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this Channel. |
| `xTwilioWebhookEnabled` | [`ChannelWebhookEnabledType?`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `type` | [`ChannelChannelType?`](../../doc/models/channel-channel-type.md) | Form, Optional | The visibility of the channel. Can be: `public` or `private`. |
| `messagingServiceSid` | `string` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this channel belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Channel](../../doc/models/channel.md).

## Example Usage

```csharp
string serviceSid = "ServiceSid8";
string sid = "Sid8";
ChannelChannelType? type = ChannelChannelType.Private;
string messagingServiceSid = "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
try
{
    ApiResponse<Channel> result = await chatV3ChannelApi.UpdateChannelAsync(
        serviceSid,
        sid,
        null,
        type,
        messagingServiceSid
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
  "sid": "CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "friendly_name",
  "unique_name": "unique_name",
  "attributes": "{ \"foo\": \"bar\" }",
  "type": "public",
  "date_created": "2015-12-16T22:18:37Z",
  "date_updated": "2015-12-16T22:18:38Z",
  "created_by": "username",
  "members_count": 0,
  "messages_count": 0,
  "url": "https://chat.twilio.com/v3/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Channels/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

