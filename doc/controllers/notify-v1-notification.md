# Notify V1 Notification

```csharp
NotifyV1NotificationApi notifyV1NotificationApi = client.NotifyV1NotificationApi;
```

## Class Name

`NotifyV1NotificationApi`


# Create Notification

```csharp
CreateNotificationAsync(
    string serviceSid,
    string body = null,
    Models.NotifPriority? priority = null,
    int? ttl = null,
    string title = null,
    string sound = null,
    string action = null,
    object data = null,
    object apn = null,
    object gcm = null,
    object sms = null,
    object facebookMessenger = null,
    object fcm = null,
    List<string> segment = null,
    object alexa = null,
    List<string> toBinding = null,
    string deliveryCallbackUrl = null,
    List<string> identity = null,
    List<string> tag = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `serviceSid` | `string` | Template, Required | The SID of the [Service](https://www.twilio.com/docs/notify/api/service-resource) to create the resource under.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `body` | `string` | Form, Optional | The notification text. For FCM and GCM, translates to `data.twi_body`. For APNS, translates to `aps.alert.body`. For SMS, translates to `body`. SMS requires either this `body` value, or `media_urls` attribute defined in the `sms` parameter of the notification. |
| `priority` | [`NotifPriority?`](../../doc/models/notif-priority.md) | Form, Optional | The priority of the notification. Can be: `low` or `high` and the default is `high`. A value of `low` optimizes the client app's battery consumption; however, notifications may be delivered with unspecified delay. For FCM and GCM, `low` priority is the same as `Normal` priority. For APNS `low` priority is the same as `5`. A value of `high` sends the notification immediately, and can wake up a sleeping device. For FCM and GCM, `high` is the same as `High` priority. For APNS, `high` is a priority `10`. SMS does not support this property. |
| `ttl` | `int?` | Form, Optional | How long, in seconds, the notification is valid. Can be an integer between 0 and 2,419,200, which is 4 weeks, the default and the maximum supported time to live (TTL). Delivery should be attempted if the device is offline until the TTL elapses. Zero means that the notification delivery is attempted immediately, only once, and is not stored for future delivery. SMS does not support this property. |
| `title` | `string` | Form, Optional | The notification title. For FCM and GCM, this translates to the `data.twi_title` value. For APNS, this translates to the `aps.alert.title` value. SMS does not support this property. This field is not visible on iOS phones and tablets but appears on Apple Watch and Android devices. |
| `sound` | `string` | Form, Optional | The name of the sound to be played for the notification. For FCM and GCM, this Translates to `data.twi_sound`.  For APNS, this translates to `aps.sound`.  SMS does not support this property. |
| `action` | `string` | Form, Optional | The actions to display for the notification. For APNS, translates to the `aps.category` value. For GCM, translates to the `data.twi_action` value. For SMS, this parameter is not supported and is omitted from deliveries to those channels. |
| `data` | `object` | Form, Optional | The custom key-value pairs of the notification's payload. For FCM and GCM, this value translates to `data` in the FCM and GCM payloads. FCM and GCM [reserve certain keys](https://firebase.google.com/docs/cloud-messaging/http-server-ref) that cannot be used in those channels. For APNS, attributes of `data` are inserted into the APNS payload as custom properties outside of the `aps` dictionary. In all channels, we reserve keys that start with `twi_` for future use. Custom keys that start with `twi_` are not allowed and are rejected as 400 Bad request with no delivery attempted. For SMS, this parameter is not supported and is omitted from deliveries to those channels. |
| `apn` | `object` | Form, Optional | The APNS-specific payload that overrides corresponding attributes in the generic payload for APNS Bindings. This property maps to the APNS `Payload` item, therefore the `aps` key must be used to change standard attributes. Adds custom key-value pairs to the root of the dictionary. See the [APNS documentation](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CommunicatingwithAPNs.html) for more details. We reserve keys that start with `twi_` for future use. Custom keys that start with `twi_` are not allowed. |
| `gcm` | `object` | Form, Optional | The GCM-specific payload that overrides corresponding attributes in the generic payload for GCM Bindings.  This property maps to the root JSON dictionary. See the [GCM documentation](https://firebase.google.com/docs/cloud-messaging/http-server-ref) for more details. Target parameters `to`, `registration_ids`, and `notification_key` are not allowed. We reserve keys that start with `twi_` for future use. Custom keys that start with `twi_` are not allowed. GCM also [reserves certain keys](https://firebase.google.com/docs/cloud-messaging/http-server-ref). |
| `sms` | `object` | Form, Optional | The SMS-specific payload that overrides corresponding attributes in the generic payload for SMS Bindings.  Each attribute in this value maps to the corresponding `form` parameter of the Twilio [Message](https://www.twilio.com/docs/sms/quickstart) resource.  These parameters of the Message resource are supported in snake case format: `body`, `media_urls`, `status_callback`, and `max_price`.  The `status_callback` parameter overrides the corresponding parameter in the messaging service, if configured. The `media_urls` property expects a JSON array. |
| `facebookMessenger` | `object` | Form, Optional | Deprecated. |
| `fcm` | `object` | Form, Optional | The FCM-specific payload that overrides corresponding attributes in the generic payload for FCM Bindings. This property maps to the root JSON dictionary. See the [FCM documentation](https://firebase.google.com/docs/cloud-messaging/http-server-ref#downstream) for more details. Target parameters `to`, `registration_ids`, `condition`, and `notification_key` are not allowed in this parameter. We reserve keys that start with `twi_` for future use. Custom keys that start with `twi_` are not allowed. FCM also [reserves certain keys](https://firebase.google.com/docs/cloud-messaging/http-server-ref), which cannot be used in that channel. |
| `segment` | `List<string>` | Form, Optional | The Segment resource is deprecated. Use the `tag` parameter, instead. |
| `alexa` | `object` | Form, Optional | Deprecated. |
| `toBinding` | `List<string>` | Form, Optional | The destination address specified as a JSON string.  Multiple `to_binding` parameters can be included but the total size of the request entity should not exceed 1MB. This is typically sufficient for 10,000 phone numbers. |
| `deliveryCallbackUrl` | `string` | Form, Optional | URL to send webhooks. |
| `identity` | `List<string>` | Form, Optional | The `identity` value that uniquely identifies the new resource's [User](https://www.twilio.com/docs/chat/rest/user-resource) within the [Service](https://www.twilio.com/docs/notify/api/service-resource). Delivery will be attempted only to Bindings with an Identity in this list. No more than 20 items are allowed in this list. |
| `tag` | `List<string>` | Form, Optional | A tag that selects the Bindings to notify. Repeat this parameter to specify more than one tag, up to a total of 5 tags. The implicit tag `all` is available to notify all Bindings in a Service instance. Similarly, the implicit tags `apn`, `fcm`, `gcm`, `sms` and `facebook-messenger` are available to notify all Bindings in a specific channel. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Notification](../../doc/models/notification.md).

## Example Usage

```csharp
string serviceSid = "ServiceSid8";
string body = "body";
NotifPriority? priority = NotifPriority.High;
string title = "test";
string deliveryCallbackUrl = "hello";
try
{
    ApiResponse<Notification> result = await notifyV1NotificationApi.CreateNotificationAsync(
        serviceSid,
        body,
        priority,
        null,
        title,
        null,
        null,
        null,
        null,
        null,
        null,
        null,
        null,
        null,
        null,
        null,
        deliveryCallbackUrl
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
  "sid": "NTb8021351170b4e1286adaac3fdd6d082",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "service_sid": "IS699b53e02da45a1ba9d13b7d7d2766af",
  "date_created": "2016-03-24T23:42:28Z",
  "identities": [
    "jing"
  ],
  "tags": [],
  "segments": [],
  "priority": "high",
  "ttl": 2419200,
  "title": "test",
  "body": "body",
  "sound": null,
  "action": null,
  "data": null,
  "apn": null,
  "fcm": null,
  "gcm": null,
  "sms": null,
  "facebook_messenger": null,
  "alexa": null
}
```

