Private endpoint connection proxy details.
API Version: 2022-10-01.
Previous API Version: 2020-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnectionProxyCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnectionProxy = new AzureNative.DeviceUpdate.PrivateEndpointConnectionProxy("privateEndpointConnectionProxy", new()
    {
        AccountName = "contoso",
        PrivateEndpointConnectionProxyId = "peexample01",
        RemotePrivateEndpoint = new AzureNative.DeviceUpdate.Inputs.RemotePrivateEndpointArgs
        {
            Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{peName}",
            ImmutableResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{peName}",
            ImmutableSubscriptionId = "00000000-0000-0000-0000-000000000000",
            Location = "westus2",
            ManualPrivateLinkServiceConnections = new[]
            {
                new AzureNative.DeviceUpdate.Inputs.PrivateLinkServiceConnectionArgs
                {
                    GroupIds = new[]
                    {
                        "DeviceUpdate",
                    },
                    Name = "{privateEndpointConnectionProxyId}",
                    RequestMessage = "Please approve my connection, thanks.",
                },
            },
            PrivateLinkServiceProxies = new[]
            {
                new AzureNative.DeviceUpdate.Inputs.PrivateLinkServiceProxyArgs
                {
                    GroupConnectivityInformation = new[] {},
                    Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{privateEndpointConnectionProxyId}/privateLinkServiceProxies/{privateEndpointConnectionProxyId}",
                },
            },
        },
        ResourceGroupName = "test-rg",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.deviceupdate.PrivateEndpointConnectionProxy;
import com.pulumi.azurenative.deviceupdate.PrivateEndpointConnectionProxyArgs;
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
        var privateEndpointConnectionProxy = new PrivateEndpointConnectionProxy("privateEndpointConnectionProxy", PrivateEndpointConnectionProxyArgs.builder()        
            .accountName("contoso")
            .privateEndpointConnectionProxyId("peexample01")
            .remotePrivateEndpoint(Map.ofEntries(
                Map.entry("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{peName}"),
                Map.entry("immutableResourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{peName}"),
                Map.entry("immutableSubscriptionId", "00000000-0000-0000-0000-000000000000"),
                Map.entry("location", "westus2"),
                Map.entry("manualPrivateLinkServiceConnections", Map.ofEntries(
                    Map.entry("groupIds", "DeviceUpdate"),
                    Map.entry("name", "{privateEndpointConnectionProxyId}"),
                    Map.entry("requestMessage", "Please approve my connection, thanks.")
                )),
                Map.entry("privateLinkServiceProxies", Map.ofEntries(
                    Map.entry("groupConnectivityInformation", ),
                    Map.entry("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{privateEndpointConnectionProxyId}/privateLinkServiceProxies/{privateEndpointConnectionProxyId}")
                ))
            ))
            .resourceGroupName("test-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnectionProxy = new azure_native.deviceupdate.PrivateEndpointConnectionProxy("privateEndpointConnectionProxy", {
    accountName: "contoso",
    privateEndpointConnectionProxyId: "peexample01",
    remotePrivateEndpoint: {
        id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{peName}",
        immutableResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{peName}",
        immutableSubscriptionId: "00000000-0000-0000-0000-000000000000",
        location: "westus2",
        manualPrivateLinkServiceConnections: [{
            groupIds: ["DeviceUpdate"],
            name: "{privateEndpointConnectionProxyId}",
            requestMessage: "Please approve my connection, thanks.",
        }],
        privateLinkServiceProxies: [{
            groupConnectivityInformation: [],
            id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{privateEndpointConnectionProxyId}/privateLinkServiceProxies/{privateEndpointConnectionProxyId}",
        }],
    },
    resourceGroupName: "test-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection_proxy = azure_native.deviceupdate.PrivateEndpointConnectionProxy("privateEndpointConnectionProxy",
    account_name="contoso",
    private_endpoint_connection_proxy_id="peexample01",
    remote_private_endpoint=azure_native.deviceupdate.RemotePrivateEndpointResponseArgs(
        id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{peName}",
        immutable_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{peName}",
        immutable_subscription_id="00000000-0000-0000-0000-000000000000",
        location="westus2",
        manual_private_link_service_connections=[azure_native.deviceupdate.PrivateLinkServiceConnectionArgs(
            group_ids=["DeviceUpdate"],
            name="{privateEndpointConnectionProxyId}",
            request_message="Please approve my connection, thanks.",
        )],
        private_link_service_proxies=[{
            "groupConnectivityInformation": [],
            "id": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{privateEndpointConnectionProxyId}/privateLinkServiceProxies/{privateEndpointConnectionProxyId}",
        }],
    ),
    resource_group_name="test-rg")

```

```yaml
resources:
  privateEndpointConnectionProxy:
    type: azure-native:deviceupdate:PrivateEndpointConnectionProxy
    properties:
      accountName: contoso
      privateEndpointConnectionProxyId: peexample01
      remotePrivateEndpoint:
        id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{peName}
        immutableResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{peName}
        immutableSubscriptionId: 00000000-0000-0000-0000-000000000000
        location: westus2
        manualPrivateLinkServiceConnections:
          - groupIds:
              - DeviceUpdate
            name: '{privateEndpointConnectionProxyId}'
            requestMessage: Please approve my connection, thanks.
        privateLinkServiceProxies:
          - groupConnectivityInformation: []
            id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Network/privateEndpoints/{privateEndpointConnectionProxyId}/privateLinkServiceProxies/{privateEndpointConnectionProxyId}
      resourceGroupName: test-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:deviceupdate:PrivateEndpointConnectionProxy peexample01 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DeviceUpdate/accounts/contoso/privateEndpointConnectionProxies/peexample01 
```
