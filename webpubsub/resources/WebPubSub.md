A class represent a resource.
API Version: 2023-02-01.
Previous API Version: 2021-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WebPubSub_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webPubSub = new AzureNative.WebPubSub.WebPubSub("webPubSub", new()
    {
        DisableAadAuth = false,
        DisableLocalAuth = false,
        Identity = new AzureNative.WebPubSub.Inputs.ManagedIdentityArgs
        {
            Type = "SystemAssigned",
        },
        LiveTraceConfiguration = new AzureNative.WebPubSub.Inputs.LiveTraceConfigurationArgs
        {
            Categories = new[]
            {
                new AzureNative.WebPubSub.Inputs.LiveTraceCategoryArgs
                {
                    Enabled = "true",
                    Name = "ConnectivityLogs",
                },
            },
            Enabled = "false",
        },
        Location = "eastus",
        NetworkACLs = new AzureNative.WebPubSub.Inputs.WebPubSubNetworkACLsArgs
        {
            DefaultAction = "Deny",
            PrivateEndpoints = new[]
            {
                new AzureNative.WebPubSub.Inputs.PrivateEndpointACLArgs
                {
                    Allow = new[]
                    {
                        "ServerConnection",
                    },
                    Name = "mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
                },
            },
            PublicNetwork = new AzureNative.WebPubSub.Inputs.NetworkACLArgs
            {
                Allow = new[]
                {
                    "ClientConnection",
                },
            },
        },
        PublicNetworkAccess = "Enabled",
        ResourceGroupName = "myResourceGroup",
        ResourceName = "myWebPubSubService",
        Sku = new AzureNative.WebPubSub.Inputs.ResourceSkuArgs
        {
            Capacity = 1,
            Name = "Premium_P1",
            Tier = "Premium",
        },
        Tags = 
        {
            { "key1", "value1" },
        },
        Tls = new AzureNative.WebPubSub.Inputs.WebPubSubTlsSettingsArgs
        {
            ClientCertEnabled = false,
        },
    });

});


```

```go
package main

import (
	webpubsub "github.com/pulumi/pulumi-azure-native-sdk/webpubsub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := webpubsub.NewWebPubSub(ctx, "webPubSub", &webpubsub.WebPubSubArgs{
			DisableAadAuth:   pulumi.Bool(false),
			DisableLocalAuth: pulumi.Bool(false),
			Identity: &webpubsub.ManagedIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			LiveTraceConfiguration: webpubsub.LiveTraceConfigurationResponse{
				Categories: webpubsub.LiveTraceCategoryArray{
					&webpubsub.LiveTraceCategoryArgs{
						Enabled: pulumi.String("true"),
						Name:    pulumi.String("ConnectivityLogs"),
					},
				},
				Enabled: pulumi.String("false"),
			},
			Location: pulumi.String("eastus"),
			NetworkACLs: webpubsub.WebPubSubNetworkACLsResponse{
				DefaultAction: pulumi.String("Deny"),
				PrivateEndpoints: webpubsub.PrivateEndpointACLArray{
					&webpubsub.PrivateEndpointACLArgs{
						Allow: pulumi.StringArray{
							pulumi.String("ServerConnection"),
						},
						Name: pulumi.String("mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e"),
					},
				},
				PublicNetwork: &webpubsub.NetworkACLArgs{
					Allow: pulumi.StringArray{
						pulumi.String("ClientConnection"),
					},
				},
			},
			PublicNetworkAccess: pulumi.String("Enabled"),
			ResourceGroupName:   pulumi.String("myResourceGroup"),
			ResourceName:        pulumi.String("myWebPubSubService"),
			Sku: &webpubsub.ResourceSkuArgs{
				Capacity: pulumi.Int(1),
				Name:     pulumi.String("Premium_P1"),
				Tier:     pulumi.String("Premium"),
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			Tls: &webpubsub.WebPubSubTlsSettingsArgs{
				ClientCertEnabled: pulumi.Bool(false),
			},
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.webpubsub.WebPubSub;
import com.pulumi.azurenative.webpubsub.WebPubSubArgs;
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
        var webPubSub = new WebPubSub("webPubSub", WebPubSubArgs.builder()        
            .disableAadAuth(false)
            .disableLocalAuth(false)
            .identity(Map.of("type", "SystemAssigned"))
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
                    Map.entry("name", "mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e")
                )),
                Map.entry("publicNetwork", Map.of("allow", "ClientConnection"))
            ))
            .publicNetworkAccess("Enabled")
            .resourceGroupName("myResourceGroup")
            .resourceName("myWebPubSubService")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "Premium_P1"),
                Map.entry("tier", "Premium")
            ))
            .tags(Map.of("key1", "value1"))
            .tls(Map.of("clientCertEnabled", false))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webPubSub = new azure_native.webpubsub.WebPubSub("webPubSub", {
    disableAadAuth: false,
    disableLocalAuth: false,
    identity: {
        type: "SystemAssigned",
    },
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
            name: "mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
        }],
        publicNetwork: {
            allow: ["ClientConnection"],
        },
    },
    publicNetworkAccess: "Enabled",
    resourceGroupName: "myResourceGroup",
    resourceName: "myWebPubSubService",
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
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_pub_sub = azure_native.webpubsub.WebPubSub("webPubSub",
    disable_aad_auth=False,
    disable_local_auth=False,
    identity=azure_native.webpubsub.ManagedIdentityArgs(
        type="SystemAssigned",
    ),
    live_trace_configuration=azure_native.webpubsub.LiveTraceConfigurationResponseArgs(
        categories=[azure_native.webpubsub.LiveTraceCategoryArgs(
            enabled="true",
            name="ConnectivityLogs",
        )],
        enabled="false",
    ),
    location="eastus",
    network_acls=azure_native.webpubsub.WebPubSubNetworkACLsResponseArgs(
        default_action="Deny",
        private_endpoints=[azure_native.webpubsub.PrivateEndpointACLArgs(
            allow=["ServerConnection"],
            name="mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
        )],
        public_network=azure_native.webpubsub.NetworkACLArgs(
            allow=["ClientConnection"],
        ),
    ),
    public_network_access="Enabled",
    resource_group_name="myResourceGroup",
    resource_name_="myWebPubSubService",
    sku=azure_native.webpubsub.ResourceSkuArgs(
        capacity=1,
        name="Premium_P1",
        tier="Premium",
    ),
    tags={
        "key1": "value1",
    },
    tls=azure_native.webpubsub.WebPubSubTlsSettingsArgs(
        client_cert_enabled=False,
    ))

```

```yaml
resources:
  webPubSub:
    type: azure-native:webpubsub:WebPubSub
    properties:
      disableAadAuth: false
      disableLocalAuth: false
      identity:
        type: SystemAssigned
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
            name: mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e
        publicNetwork:
          allow:
            - ClientConnection
      publicNetworkAccess: Enabled
      resourceGroupName: myResourceGroup
      resourceName: myWebPubSubService
      sku:
        capacity: 1
        name: Premium_P1
        tier: Premium
      tags:
        key1: value1
      tls:
        clientCertEnabled: false

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:webpubsub:WebPubSub myWebPubSubService /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService 
```
