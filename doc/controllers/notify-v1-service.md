# Notify V1 Service

```csharp
NotifyV1ServiceApi notifyV1ServiceApi = client.NotifyV1ServiceApi;
```

## Class Name

`NotifyV1ServiceApi`

## Methods

* [Create Service](../../doc/controllers/notify-v1-service.md#create-service)
* [List Service](../../doc/controllers/notify-v1-service.md#list-service)
* [Delete Service](../../doc/controllers/notify-v1-service.md#delete-service)
* [Fetch Service](../../doc/controllers/notify-v1-service.md#fetch-service)
* [Update Service](../../doc/controllers/notify-v1-service.md#update-service)


# Create Service

```csharp
CreateServiceAsync(
    string friendlyName = null,
    string apnCredentialSid = null,
    string gcmCredentialSid = null,
    string messagingServiceSid = null,
    string facebookMessengerPageId = null,
    string defaultApnNotificationProtocolVersion = null,
    string defaultGcmNotificationProtocolVersion = null,
    string fcmCredentialSid = null,
    string defaultFcmNotificationProtocolVersion = null,
    bool? logEnabled = null,
    string alexaSkillId = null,
    string defaultAlexaNotificationProtocolVersion = null,
    string deliveryCallbackUrl = null,
    bool? deliveryCallbackEnabled = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `friendlyName` | `string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |
| `apnCredentialSid` | `string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for APN Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `gcmCredentialSid` | `string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for GCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `messagingServiceSid` | `string` | Form, Optional | The SID of the [Messaging Service](https://www.twilio.com/docs/sms/quickstart#messaging-services) to use for SMS Bindings. This parameter must be set in order to send SMS notifications.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `facebookMessengerPageId` | `string` | Form, Optional | Deprecated. |
| `defaultApnNotificationProtocolVersion` | `string` | Form, Optional | The protocol version to use for sending APNS notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `defaultGcmNotificationProtocolVersion` | `string` | Form, Optional | The protocol version to use for sending GCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `fcmCredentialSid` | `string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for FCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `defaultFcmNotificationProtocolVersion` | `string` | Form, Optional | The protocol version to use for sending FCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `logEnabled` | `bool?` | Form, Optional | Whether to log notifications. Can be: `true` or `false` and the default is `true`. |
| `alexaSkillId` | `string` | Form, Optional | Deprecated. |
| `defaultAlexaNotificationProtocolVersion` | `string` | Form, Optional | Deprecated. |
| `deliveryCallbackUrl` | `string` | Form, Optional | URL to send delivery status callback. |
| `deliveryCallbackEnabled` | `bool?` | Form, Optional | Callback configuration that enables delivery callbacks, default false |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Service1](../../doc/models/service-1.md).

## Example Usage

```csharp
string friendlyName = "friendly_name";
string apnCredentialSid = "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string messagingServiceSid = "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string facebookMessengerPageId = "4";
string defaultApnNotificationProtocolVersion = "3";
string defaultGcmNotificationProtocolVersion = "3";
string defaultFcmNotificationProtocolVersion = "3";
bool? logEnabled = true;
string deliveryCallbackUrl = "Hello";
bool? deliveryCallbackEnabled = true;
try
{
    ApiResponse<Service1> result = await notifyV1ServiceApi.CreateServiceAsync(
        friendlyName,
        apnCredentialSid,
        null,
        messagingServiceSid,
        facebookMessengerPageId,
        defaultApnNotificationProtocolVersion,
        defaultGcmNotificationProtocolVersion,
        null,
        defaultFcmNotificationProtocolVersion,
        logEnabled,
        null,
        null,
        deliveryCallbackUrl,
        deliveryCallbackEnabled
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
  "sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "733c7f0f-6541-42ec-84ce-e2ae1cac588c",
  "date_created": "2016-03-09T20:22:31Z",
  "date_updated": "2016-03-09T20:22:31Z",
  "apn_credential_sid": null,
  "gcm_credential_sid": null,
  "fcm_credential_sid": null,
  "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "facebook_messenger_page_id": "4",
  "alexa_skill_id": null,
  "default_apn_notification_protocol_version": "3",
  "default_gcm_notification_protocol_version": "3",
  "default_fcm_notification_protocol_version": "3",
  "default_alexa_notification_protocol_version": "3",
  "log_enabled": true,
  "delivery_callback_url": "Hello",
  "delivery_callback_enabled": true,
  "url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "bindings": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings",
    "notifications": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Notifications",
    "segments": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Segments",
    "users": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users"
  }
}
```


# List Service

```csharp
ListServiceAsync(
    string friendlyName = null,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `friendlyName` | `string` | Query, Optional | The string that identifies the Service resources to read. |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListServiceResponse](../../doc/models/list-service-response.md).

## Example Usage

```csharp
try
{
    ApiResponse<ListServiceResponse> result = await notifyV1ServiceApi.ListServiceAsync();
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://notify.twilio.com/v1/Services?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://notify.twilio.com/v1/Services?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "services"
  },
  "services": [
    {
      "sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "733c7f0f-6541-42ec-84ce-e2ae1cac588c",
      "date_created": "2016-03-09T20:22:31Z",
      "date_updated": "2016-03-09T20:22:31Z",
      "apn_credential_sid": null,
      "gcm_credential_sid": null,
      "fcm_credential_sid": null,
      "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "facebook_messenger_page_id": "4",
      "alexa_skill_id": null,
      "default_apn_notification_protocol_version": "3",
      "default_gcm_notification_protocol_version": "3",
      "default_fcm_notification_protocol_version": "3",
      "default_alexa_notification_protocol_version": "3",
      "log_enabled": true,
      "delivery_callback_url": "Hello",
      "delivery_callback_enabled": true,
      "url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "bindings": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings",
        "notifications": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Notifications",
        "segments": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Segments",
        "users": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users"
      }
    }
  ]
}
```


# Delete Service

```csharp
DeleteServiceAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the Service resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Response Type

`Task`

## Example Usage

```csharp
string sid = "Sid8";
try
{
    await notifyV1ServiceApi.DeleteServiceAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Service

```csharp
FetchServiceAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the Service resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Service1](../../doc/models/service-1.md).

## Example Usage

```csharp
string sid = "Sid8";
try
{
    ApiResponse<Service1> result = await notifyV1ServiceApi.FetchServiceAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "733c7f0f-6541-42ec-84ce-e2ae1cac588c",
  "date_created": "2016-03-09T20:22:31Z",
  "date_updated": "2016-03-09T20:22:31Z",
  "apn_credential_sid": null,
  "gcm_credential_sid": null,
  "fcm_credential_sid": null,
  "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "facebook_messenger_page_id": "4",
  "alexa_skill_id": null,
  "default_apn_notification_protocol_version": "3",
  "default_gcm_notification_protocol_version": "3",
  "default_fcm_notification_protocol_version": "3",
  "default_alexa_notification_protocol_version": "3",
  "log_enabled": true,
  "delivery_callback_url": "Hello",
  "delivery_callback_enabled": true,
  "url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "bindings": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings",
    "notifications": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Notifications",
    "segments": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Segments",
    "users": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users"
  }
}
```


# Update Service

```csharp
UpdateServiceAsync(
    string sid,
    string friendlyName = null,
    string apnCredentialSid = null,
    string gcmCredentialSid = null,
    string messagingServiceSid = null,
    string facebookMessengerPageId = null,
    string defaultApnNotificationProtocolVersion = null,
    string defaultGcmNotificationProtocolVersion = null,
    string fcmCredentialSid = null,
    string defaultFcmNotificationProtocolVersion = null,
    bool? logEnabled = null,
    string alexaSkillId = null,
    string defaultAlexaNotificationProtocolVersion = null,
    string deliveryCallbackUrl = null,
    bool? deliveryCallbackEnabled = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the Service resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `friendlyName` | `string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |
| `apnCredentialSid` | `string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for APN Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `gcmCredentialSid` | `string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for GCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `messagingServiceSid` | `string` | Form, Optional | The SID of the [Messaging Service](https://www.twilio.com/docs/sms/quickstart#messaging-services) to use for SMS Bindings. This parameter must be set in order to send SMS notifications.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `facebookMessengerPageId` | `string` | Form, Optional | Deprecated. |
| `defaultApnNotificationProtocolVersion` | `string` | Form, Optional | The protocol version to use for sending APNS notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `defaultGcmNotificationProtocolVersion` | `string` | Form, Optional | The protocol version to use for sending GCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `fcmCredentialSid` | `string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for FCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `defaultFcmNotificationProtocolVersion` | `string` | Form, Optional | The protocol version to use for sending FCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `logEnabled` | `bool?` | Form, Optional | Whether to log notifications. Can be: `true` or `false` and the default is `true`. |
| `alexaSkillId` | `string` | Form, Optional | Deprecated. |
| `defaultAlexaNotificationProtocolVersion` | `string` | Form, Optional | Deprecated. |
| `deliveryCallbackUrl` | `string` | Form, Optional | URL to send delivery status callback. |
| `deliveryCallbackEnabled` | `bool?` | Form, Optional | Callback configuration that enables delivery callbacks, default false |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Service1](../../doc/models/service-1.md).

## Example Usage

```csharp
string sid = "Sid8";
string friendlyName = "friendly_name";
string apnCredentialSid = "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string messagingServiceSid = "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string facebookMessengerPageId = "4";
string defaultApnNotificationProtocolVersion = "3";
string defaultGcmNotificationProtocolVersion = "3";
string defaultFcmNotificationProtocolVersion = "3";
bool? logEnabled = true;
string deliveryCallbackUrl = "Hello";
bool? deliveryCallbackEnabled = true;
try
{
    ApiResponse<Service1> result = await notifyV1ServiceApi.UpdateServiceAsync(
        sid,
        friendlyName,
        apnCredentialSid,
        null,
        messagingServiceSid,
        facebookMessengerPageId,
        defaultApnNotificationProtocolVersion,
        defaultGcmNotificationProtocolVersion,
        null,
        defaultFcmNotificationProtocolVersion,
        logEnabled,
        null,
        null,
        deliveryCallbackUrl,
        deliveryCallbackEnabled
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
  "sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "733c7f0f-6541-42ec-84ce-e2ae1cac588c",
  "date_created": "2016-03-09T20:22:31Z",
  "date_updated": "2016-03-09T20:22:31Z",
  "apn_credential_sid": null,
  "gcm_credential_sid": null,
  "fcm_credential_sid": null,
  "default_apn_notification_protocol_version": "3",
  "default_gcm_notification_protocol_version": "3",
  "default_fcm_notification_protocol_version": "3",
  "default_alexa_notification_protocol_version": "3",
  "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "alexa_skill_id": null,
  "facebook_messenger_page_id": "4",
  "log_enabled": true,
  "delivery_callback_url": "Hello",
  "delivery_callback_enabled": true,
  "url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "bindings": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings",
    "notifications": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Notifications",
    "segments": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Segments",
    "users": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users"
  }
}
```

