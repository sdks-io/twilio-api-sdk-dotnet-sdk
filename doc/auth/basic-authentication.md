
# Basic Authentication



Documentation for accessing and setting credentials for accountSid_authToken.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| BasicAuthUserName | `string` | The username to use with basic authentication | `Username` | `BasicAuthUserName` |
| BasicAuthPassword | `string` | The password to use with basic authentication | `Password` | `BasicAuthPassword` |



**Note:** Auth credentials can be set using `BasicAuthCredentials` in the client builder and accessed through `BasicAuthCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```csharp
using TwilioApIs.Standard;
using TwilioApIs.Standard.Authentication;

namespace ConsoleApp;

TwilioApIsClient client = new TwilioApIsClient.Builder()
    .BasicAuthCredentials(
        new BasicAuthModel.Builder(
            "BasicAuthUserName",
            "BasicAuthPassword"
        )
        .Build())
    .Build();
```


