# Conversations V1 Address Configuration

```csharp
ConversationsV1AddressConfigurationApi conversationsV1AddressConfigurationApi = client.ConversationsV1AddressConfigurationApi;
```

## Class Name

`ConversationsV1AddressConfigurationApi`

## Methods

* [List Configuration Address](../../doc/controllers/conversations-v1-address-configuration.md#list-configuration-address)
* [Create Configuration Address](../../doc/controllers/conversations-v1-address-configuration.md#create-configuration-address)
* [Fetch Configuration Address](../../doc/controllers/conversations-v1-address-configuration.md#fetch-configuration-address)
* [Update Configuration Address](../../doc/controllers/conversations-v1-address-configuration.md#update-configuration-address)
* [Delete Configuration Address](../../doc/controllers/conversations-v1-address-configuration.md#delete-configuration-address)


# List Configuration Address

Retrieve a list of address configurations for an account

```csharp
ListConfigurationAddressAsync(
    string type = null,
    long? pageSize = null,
    int? page = null,
    string pageToken = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | `string` | Query, Optional | Filter the address configurations by its type. This value can be one of: `whatsapp`, `sms`. |
| `pageSize` | `long?` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `int?` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ListConfigurationAddressResponse](../../doc/models/list-configuration-address-response.md).

## Example Usage

```csharp
string type = "sms";
try
{
    ApiResponse<ListConfigurationAddressResponse> result = await conversationsV1AddressConfigurationApi.ListConfigurationAddressAsync(type);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Create Configuration Address

Create a new address configuration

```csharp
CreateConfigurationAddressAsync(
    Models.ConfigurationAddressType type,
    string address,
    string friendlyName = null,
    bool? autoCreationEnabled = null,
    Models.ConfigurationAddressAutoCreationType? autoCreationType = null,
    string autoCreationConversationServiceSid = null,
    string autoCreationWebhookUrl = null,
    Models.ConfigurationAddressMethod? autoCreationWebhookMethod = null,
    List<string> autoCreationWebhookFilters = null,
    string autoCreationStudioFlowSid = null,
    int? autoCreationStudioRetryCount = null,
    string addressCountry = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | [`ConfigurationAddressType`](../../doc/models/configuration-address-type.md) | Form, Required | Type of Address, value can be `whatsapp` or `sms`. |
| `address` | `string` | Form, Required | The unique address to be configured. The address can be a whatsapp address or phone number |
| `friendlyName` | `string` | Form, Optional | The human-readable name of this configuration, limited to 256 characters. Optional. |
| `autoCreationEnabled` | `bool?` | Form, Optional | Enable/Disable auto-creating conversations for messages to this address |
| `autoCreationType` | [`ConfigurationAddressAutoCreationType?`](../../doc/models/configuration-address-auto-creation-type.md) | Form, Optional | - |
| `autoCreationConversationServiceSid` | `string` | Form, Optional | Conversation Service for the auto-created conversation. If not set, the conversation is created in the default service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `autoCreationWebhookUrl` | `string` | Form, Optional | For type `webhook`, the url for the webhook request. |
| `autoCreationWebhookMethod` | [`ConfigurationAddressMethod?`](../../doc/models/configuration-address-method.md) | Form, Optional | - |
| `autoCreationWebhookFilters` | `List<string>` | Form, Optional | The list of events, firing webhook event for this Conversation. Values can be any of the following: `onMessageAdded`, `onMessageUpdated`, `onMessageRemoved`, `onConversationUpdated`, `onConversationStateUpdated`, `onConversationRemoved`, `onParticipantAdded`, `onParticipantUpdated`, `onParticipantRemoved`, `onDeliveryUpdated` |
| `autoCreationStudioFlowSid` | `string` | Form, Optional | For type `studio`, the studio flow SID where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |
| `autoCreationStudioRetryCount` | `int?` | Form, Optional | For type `studio`, number of times to retry the webhook request |
| `addressCountry` | `string` | Form, Optional | An ISO 3166-1 alpha-2n country code which the address belongs to. This is currently only applicable to short code addresses. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConfigurationAddress](../../doc/models/configuration-address.md).

## Example Usage

```csharp
ConfigurationAddressType type = ConfigurationAddressType.Sms;
string address = "+37256123457";
string friendlyName = "My Test Configuration";
bool? autoCreationEnabled = true;
ConfigurationAddressAutoCreationType? autoCreationType = ConfigurationAddressAutoCreationType.Webhook;
string autoCreationConversationServiceSid = "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
string autoCreationWebhookUrl = "https://example.com";
ConfigurationAddressMethod? autoCreationWebhookMethod = ConfigurationAddressMethod.Post;
List<string> autoCreationWebhookFilters = new List<string>
{
    "onParticipantAdded",
    "onMessageAdded",
};

string addressCountry = "CA";
try
{
    ApiResponse<ConfigurationAddress> result = await conversationsV1AddressConfigurationApi.CreateConfigurationAddressAsync(
        type,
        address,
        friendlyName,
        autoCreationEnabled,
        autoCreationType,
        autoCreationConversationServiceSid,
        autoCreationWebhookUrl,
        autoCreationWebhookMethod,
        autoCreationWebhookFilters,
        null,
        null,
        addressCountry
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Fetch Configuration Address

Fetch an address configuration

```csharp
FetchConfigurationAddressAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Address Configuration resource. This value can be either the `sid` or the `address` of the configuration |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConfigurationAddress](../../doc/models/configuration-address.md).

## Example Usage

```csharp
string sid = "Sid8";
try
{
    ApiResponse<ConfigurationAddress> result = await conversationsV1AddressConfigurationApi.FetchConfigurationAddressAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Update Configuration Address

Update an existing address configuration

```csharp
UpdateConfigurationAddressAsync(
    string sid,
    string friendlyName = null,
    bool? autoCreationEnabled = null,
    Models.ConfigurationAddressAutoCreationType? autoCreationType = null,
    string autoCreationConversationServiceSid = null,
    string autoCreationWebhookUrl = null,
    Models.ConfigurationAddressMethod? autoCreationWebhookMethod = null,
    List<string> autoCreationWebhookFilters = null,
    string autoCreationStudioFlowSid = null,
    int? autoCreationStudioRetryCount = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Address Configuration resource. This value can be either the `sid` or the `address` of the configuration |
| `friendlyName` | `string` | Form, Optional | The human-readable name of this configuration, limited to 256 characters. Optional. |
| `autoCreationEnabled` | `bool?` | Form, Optional | Enable/Disable auto-creating conversations for messages to this address |
| `autoCreationType` | [`ConfigurationAddressAutoCreationType?`](../../doc/models/configuration-address-auto-creation-type.md) | Form, Optional | - |
| `autoCreationConversationServiceSid` | `string` | Form, Optional | Conversation Service for the auto-created conversation. If not set, the conversation is created in the default service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `autoCreationWebhookUrl` | `string` | Form, Optional | For type `webhook`, the url for the webhook request. |
| `autoCreationWebhookMethod` | [`ConfigurationAddressMethod?`](../../doc/models/configuration-address-method.md) | Form, Optional | - |
| `autoCreationWebhookFilters` | `List<string>` | Form, Optional | The list of events, firing webhook event for this Conversation. Values can be any of the following: `onMessageAdded`, `onMessageUpdated`, `onMessageRemoved`, `onConversationUpdated`, `onConversationStateUpdated`, `onConversationRemoved`, `onParticipantAdded`, `onParticipantUpdated`, `onParticipantRemoved`, `onDeliveryUpdated` |
| `autoCreationStudioFlowSid` | `string` | Form, Optional | For type `studio`, the studio flow SID where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |
| `autoCreationStudioRetryCount` | `int?` | Form, Optional | For type `studio`, number of times to retry the webhook request |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ConfigurationAddress](../../doc/models/configuration-address.md).

## Example Usage

```csharp
string sid = "Sid8";
string friendlyName = "My Test Configuration Updated";
bool? autoCreationEnabled = false;
ConfigurationAddressAutoCreationType? autoCreationType = ConfigurationAddressAutoCreationType.Studio;
string autoCreationStudioFlowSid = "FWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
int? autoCreationStudioRetryCount = 3;
try
{
    ApiResponse<ConfigurationAddress> result = await conversationsV1AddressConfigurationApi.UpdateConfigurationAddressAsync(
        sid,
        friendlyName,
        autoCreationEnabled,
        autoCreationType,
        null,
        null,
        null,
        null,
        autoCreationStudioFlowSid,
        autoCreationStudioRetryCount
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```


# Delete Configuration Address

Remove an existing address configuration

```csharp
DeleteConfigurationAddressAsync(
    string sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Address Configuration resource. This value can be either the `sid` or the `address` of the configuration |

## Response Type

`Task`

## Example Usage

```csharp
string sid = "Sid8";
try
{
    await conversationsV1AddressConfigurationApi.DeleteConfigurationAddressAsync(sid);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

