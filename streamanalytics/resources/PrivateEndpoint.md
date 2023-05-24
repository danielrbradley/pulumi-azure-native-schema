Complete information about the private endpoint.
API Version: 2020-03-01.
Previous API Version: 2020-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a private endpoint
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpoint = new AzureNative.StreamAnalytics.PrivateEndpoint("privateEndpoint", new()
    {
        ClusterName = "testcluster",
        ManualPrivateLinkServiceConnections = new[]
        {
            new AzureNative.StreamAnalytics.Inputs.PrivateLinkServiceConnectionArgs
            {
                GroupIds = new[]
                {
                    "groupIdFromResource",
                },
                PrivateLinkServiceId = "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
            },
        },
        PrivateEndpointName = "testpe",
        ResourceGroupName = "sjrg",
    });

});


```

```go
package main

import (
	streamanalytics "github.com/pulumi/pulumi-azure-native-sdk/streamanalytics"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := streamanalytics.NewPrivateEndpoint(ctx, "privateEndpoint", &streamanalytics.PrivateEndpointArgs{
			ClusterName: pulumi.String("testcluster"),
			ManualPrivateLinkServiceConnections: []streamanalytics.PrivateLinkServiceConnectionArgs{
				{
					GroupIds: pulumi.StringArray{
						pulumi.String("groupIdFromResource"),
					},
					PrivateLinkServiceId: pulumi.String("/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls"),
				},
			},
			PrivateEndpointName: pulumi.String("testpe"),
			ResourceGroupName:   pulumi.String("sjrg"),
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
import com.pulumi.azurenative.streamanalytics.PrivateEndpoint;
import com.pulumi.azurenative.streamanalytics.PrivateEndpointArgs;
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
        var privateEndpoint = new PrivateEndpoint("privateEndpoint", PrivateEndpointArgs.builder()        
            .clusterName("testcluster")
            .manualPrivateLinkServiceConnections(Map.ofEntries(
                Map.entry("groupIds", "groupIdFromResource"),
                Map.entry("privateLinkServiceId", "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls")
            ))
            .privateEndpointName("testpe")
            .resourceGroupName("sjrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpoint = new azure_native.streamanalytics.PrivateEndpoint("privateEndpoint", {
    clusterName: "testcluster",
    manualPrivateLinkServiceConnections: [{
        groupIds: ["groupIdFromResource"],
        privateLinkServiceId: "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
    }],
    privateEndpointName: "testpe",
    resourceGroupName: "sjrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint = azure_native.streamanalytics.PrivateEndpoint("privateEndpoint",
    cluster_name="testcluster",
    manual_private_link_service_connections=[azure_native.streamanalytics.PrivateLinkServiceConnectionArgs(
        group_ids=["groupIdFromResource"],
        private_link_service_id="/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls",
    )],
    private_endpoint_name="testpe",
    resource_group_name="sjrg")

```

```yaml
resources:
  privateEndpoint:
    type: azure-native:streamanalytics:PrivateEndpoint
    properties:
      clusterName: testcluster
      manualPrivateLinkServiceConnections:
        - groupIds:
            - groupIdFromResource
          privateLinkServiceId: /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls
      privateEndpointName: testpe
      resourceGroupName: sjrg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:streamanalytics:PrivateEndpoint An Example Private Endpoint /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/sjrg/providers/Microsoft.StreamAnalytics/clusters/testcluster/privateEndpoints/AnExamplePrivateEndpoint 
```
