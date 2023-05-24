A class represent a resource.
API Version: 2023-02-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SignalR_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var signalR = new AzureNative.SignalRService.SignalR("signalR", new()
    {
        Cors = new AzureNative.SignalRService.Inputs.SignalRCorsSettingsArgs
        {
            AllowedOrigins = new[]
            {
                "https://foo.com",
                "https://bar.com",
            },
        },
        DisableAadAuth = false,
        DisableLocalAuth = false,
        Features = new[]
        {
            new AzureNative.SignalRService.Inputs.SignalRFeatureArgs
            {
                Flag = "ServiceMode",
                Properties = null,
                Value = "Serverless",
            },
            new AzureNative.SignalRService.Inputs.SignalRFeatureArgs
            {
                Flag = "EnableConnectivityLogs",
                Properties = null,
                Value = "True",
            },
            new AzureNative.SignalRService.Inputs.SignalRFeatureArgs
            {
                Flag = "EnableMessagingLogs",
                Properties = null,
                Value = "False",
            },
            new AzureNative.SignalRService.Inputs.SignalRFeatureArgs
            {
                Flag = "EnableLiveTrace",
                Properties = null,
                Value = "False",
            },
        },
        Identity = new AzureNative.SignalRService.Inputs.ManagedIdentityArgs
        {
            Type = "SystemAssigned",
        },
        Kind = "SignalR",
        LiveTraceConfiguration = new AzureNative.SignalRService.Inputs.LiveTraceConfigurationArgs
        {
            Categories = new[]
            {
                new AzureNative.SignalRService.Inputs.LiveTraceCategoryArgs
                {
                    Enabled = "true",
                    Name = "ConnectivityLogs",
                },
            },
            Enabled = "false",
        },
        Location = "eastus",
        NetworkACLs = new AzureNative.SignalRService.Inputs.SignalRNetworkACLsArgs
        {
            DefaultAction = "Deny",
            PrivateEndpoints = new[]
            {
                new AzureNative.SignalRService.Inputs.PrivateEndpointACLArgs
                {
                    Allow = new[]
                    {
                        "ServerConnection",
                    },
                    Name = "mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
                },
            },
            PublicNetwork = new AzureNative.SignalRService.Inputs.NetworkACLArgs
            {
                Allow = new[]
                {
                    "ClientConnection",
                },
            },
        },
        PublicNetworkAccess = "Enabled",
        ResourceGroupName = "myResourceGroup",
        ResourceName = "mySignalRService",
        Serverless = new AzureNative.SignalRService.Inputs.ServerlessSettingsArgs
        {
            ConnectionTimeoutInSeconds = 5,
        },
        Sku = new AzureNative.SignalRService.Inputs.ResourceSkuArgs
        {
            Capacity = 1,
            Name = "Premium_P1",
            Tier = "Premium",
        },
        Tags = 
        {
            { "key1", "value1" },
        },
        Tls = new AzureNative.SignalRService.Inputs.SignalRTlsSettingsArgs
        {
            ClientCertEnabled = false,
        },
        Upstream = new AzureNative.SignalRService.Inputs.ServerlessUpstreamSettingsArgs
        {
            Templates = new[]
            {
                new AzureNative.SignalRService.Inputs.UpstreamTemplateArgs
                {
                    Auth = new AzureNative.SignalRService.Inputs.UpstreamAuthSettingsArgs
                    {
                        ManagedIdentity = new AzureNative.SignalRService.Inputs.ManagedIdentitySettingsArgs
                        {
                            Resource = "api://example",
                        },
                        Type = "ManagedIdentity",
                    },
                    CategoryPattern = "*",
                    EventPattern = "connect,disconnect",
                    HubPattern = "*",
                    UrlTemplate = "https://example.com/chat/api/connect",
                },
            },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.signalrservice.SignalR;
import com.pulumi.azurenative.signalrservice.SignalRArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var signalR = new SignalR("signalR", SignalRArgs.builder()        
            .cors(Map.of("allowedOrigins",             
                "https://foo.com",
                "https://bar.com"))
            .disableAadAuth(false)
            .disableLocalAuth(false)
            .features(            
                Map.ofEntries(
                    Map.entry("flag", "ServiceMode"),
                    Map.entry("properties", ),
                    Map.entry("value", "Serverless")
                ),
                Map.ofEntries(
                    Map.entry("flag", "EnableConnectivityLogs"),
                    Map.entry("properties", ),
                    Map.entry("value", "True")
                ),
                Map.ofEntries(
                    Map.entry("flag", "EnableMessagingLogs"),
                    Map.entry("properties", ),
                    Map.entry("value", "False")
                ),
                Map.ofEntries(
                    Map.entry("flag", "EnableLiveTrace"),
                    Map.entry("properties", ),
                    Map.entry("value", "False")
                ))
            .identity(Map.of("type", "SystemAssigned"))
            .kind("SignalR")
            .liveTraceConfiguration(Map.ofEntries(
                Map.entry("categories", Map.ofEntries(
                    Map.entry("enabled", "true"),
                    Map.entry("name", "ConnectivityLogs")
                )),
                Map.entry("enabled", "false")
            ))
            .location("eastus")
            .networkACLs(Map.ofEntries(
                Map.entry("defaultAction", "Deny"),
                Map.entry("privateEndpoints", Map.ofEntries(
                    Map.entry("allow", "ServerConnection"),
                    Map.entry("name", "mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e")
                )),
                Map.entry("publicNetwork", Map.of("allow", "ClientConnection"))
            ))
            .publicNetworkAccess("Enabled")
            .resourceGroupName("myResourceGroup")
            .resourceName("mySignalRService")
            .serverless(Map.of("connectionTimeoutInSeconds", 5))
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "Premium_P1"),
                Map.entry("tier", "Premium")
            ))
            .tags(Map.of("key1", "value1"))
            .tls(Map.of("clientCertEnabled", false))
            .upstream(Map.of("templates", Map.ofEntries(
                Map.entry("auth", Map.ofEntries(
                    Map.entry("managedIdentity", Map.of("resource", "api://example")),
                    Map.entry("type", "ManagedIdentity")
                )),
                Map.entry("categoryPattern", "*"),
                Map.entry("eventPattern", "connect,disconnect"),
                Map.entry("hubPattern", "*"),
                Map.entry("urlTemplate", "https://example.com/chat/api/connect")
            )))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const signalR = new azure_native.signalrservice.SignalR("signalR", {
    cors: {
        allowedOrigins: [
            "https://foo.com",
            "https://bar.com",
        ],
    },
    disableAadAuth: false,
    disableLocalAuth: false,
    features: [
        {
            flag: "ServiceMode",
            properties: {},
            value: "Serverless",
        },
        {
            flag: "EnableConnectivityLogs",
            properties: {},
            value: "True",
        },
        {
            flag: "EnableMessagingLogs",
            properties: {},
            value: "False",
        },
        {
            flag: "EnableLiveTrace",
            properties: {},
            value: "False",
        },
    ],
    identity: {
        type: "SystemAssigned",
    },
    kind: "SignalR",
    liveTraceConfiguration: {
        categories: [{
            enabled: "true",
            name: "ConnectivityLogs",
        }],
        enabled: "false",
    },
    location: "eastus",
    networkACLs: {
        defaultAction: "Deny",
        privateEndpoints: [{
            allow: ["ServerConnection"],
            name: "mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
        }],
        publicNetwork: {
            allow: ["ClientConnection"],
        },
    },
    publicNetworkAccess: "Enabled",
    resourceGroupName: "myResourceGroup",
    resourceName: "mySignalRService",
    serverless: {
        connectionTimeoutInSeconds: 5,
    },
    sku: {
        capacity: 1,
        name: "Premium_P1",
        tier: "Premium",
    },
    tags: {
        key1: "value1",
    },
    tls: {
        clientCertEnabled: false,
    },
    upstream: {
        templates: [{
            auth: {
                managedIdentity: {
                    resource: "api://example",
                },
                type: "ManagedIdentity",
            },
            categoryPattern: "*",
            eventPattern: "connect,disconnect",
            hubPattern: "*",
            urlTemplate: "https://example.com/chat/api/connect",
        }],
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

signal_r = azure_native.signalrservice.SignalR("signalR",
    cors=azure_native.signalrservice.SignalRCorsSettingsArgs(
        allowed_origins=[
            "https://foo.com",
            "https://bar.com",
        ],
    ),
    disable_aad_auth=False,
    disable_local_auth=False,
    features=[
        azure_native.signalrservice.SignalRFeatureArgs(
            flag="ServiceMode",
            properties={},
            value="Serverless",
        ),
        azure_native.signalrservice.SignalRFeatureArgs(
            flag="EnableConnectivityLogs",
            properties={},
            value="True",
        ),
        azure_native.signalrservice.SignalRFeatureArgs(
            flag="EnableMessagingLogs",
            properties={},
            value="False",
        ),
        azure_native.signalrservice.SignalRFeatureArgs(
            flag="EnableLiveTrace",
            properties={},
            value="False",
        ),
    ],
    identity=azure_native.signalrservice.ManagedIdentityArgs(
        type="SystemAssigned",
    ),
    kind="SignalR",
    live_trace_configuration=azure_native.signalrservice.LiveTraceConfigurationResponseArgs(
        categories=[azure_native.signalrservice.LiveTraceCategoryArgs(
            enabled="true",
            name="ConnectivityLogs",
        )],
        enabled="false",
    ),
    location="eastus",
    network_acls=azure_native.signalrservice.SignalRNetworkACLsResponseArgs(
        default_action="Deny",
        private_endpoints=[azure_native.signalrservice.PrivateEndpointACLArgs(
            allow=["ServerConnection"],
            name="mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
        )],
        public_network=azure_native.signalrservice.NetworkACLArgs(
            allow=["ClientConnection"],
        ),
    ),
    public_network_access="Enabled",
    resource_group_name="myResourceGroup",
    resource_name_="mySignalRService",
    serverless=azure_native.signalrservice.ServerlessSettingsArgs(
        connection_timeout_in_seconds=5,
    ),
    sku=azure_native.signalrservice.ResourceSkuArgs(
        capacity=1,
        name="Premium_P1",
        tier="Premium",
    ),
    tags={
        "key1": "value1",
    },
    tls=azure_native.signalrservice.SignalRTlsSettingsArgs(
        client_cert_enabled=False,
    ),
    upstream=azure_native.signalrservice.ServerlessUpstreamSettingsResponseArgs(
        templates=[{
            "auth": {
                "managedIdentity": azure_native.signalrservice.ManagedIdentitySettingsArgs(
                    resource="api://example",
                ),
                "type": "ManagedIdentity",
            },
            "categoryPattern": "*",
            "eventPattern": "connect,disconnect",
            "hubPattern": "*",
            "urlTemplate": "https://example.com/chat/api/connect",
        }],
    ))

```

```yaml
resources:
  signalR:
    type: azure-native:signalrservice:SignalR
    properties:
      cors:
        allowedOrigins:
          - https://foo.com
          - https://bar.com
      disableAadAuth: false
      disableLocalAuth: false
      features:
        - flag: ServiceMode
          properties: {}
          value: Serverless
        - flag: EnableConnectivityLogs
          properties: {}
          value: True
        - flag: EnableMessagingLogs
          properties: {}
          value: False
        - flag: EnableLiveTrace
          properties: {}
          value: False
      identity:
        type: SystemAssigned
      kind: SignalR
      liveTraceConfiguration:
        categories:
          - enabled: 'true'
            name: ConnectivityLogs
        enabled: 'false'
      location: eastus
      networkACLs:
        defaultAction: Deny
        privateEndpoints:
          - allow:
              - ServerConnection
            name: mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e
        publicNetwork:
          allow:
            - ClientConnection
      publicNetworkAccess: Enabled
      resourceGroupName: myResourceGroup
      resourceName: mySignalRService
      serverless:
        connectionTimeoutInSeconds: 5
      sku:
        capacity: 1
        name: Premium_P1
        tier: Premium
      tags:
        key1: value1
      tls:
        clientCertEnabled: false
      upstream:
        templates:
          - auth:
              managedIdentity:
                resource: api://example
              type: ManagedIdentity
            categoryPattern: '*'
            eventPattern: connect,disconnect
            hubPattern: '*'
            urlTemplate: https://example.com/chat/api/connect

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:signalrservice:SignalR mySignalRService /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/SignalR/mySignalRService 
```
