The L3IsolationDomain resource definition.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### L3IsolationDomains_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var l3IsolationDomain = new AzureNative.ManagedNetworkFabric.L3IsolationDomain("l3IsolationDomain", new()
    {
        AggregateRouteConfiguration = new AzureNative.ManagedNetworkFabric.Inputs.L3IsolationDomainPatchPropertiesAggregateRouteConfigurationArgs
        {
            Ipv4Routes = new[]
            {
                new AzureNative.ManagedNetworkFabric.Inputs.L3IsolationDomainPatchPropertiesIpv4RoutesArgs
                {
                    Prefix = "10.0.0.0/24",
                },
            },
            Ipv6Routes = new[]
            {
                new AzureNative.ManagedNetworkFabric.Inputs.L3IsolationDomainPatchPropertiesIpv6RoutesArgs
                {
                    Prefix = "10.0.0.1",
                },
            },
        },
        ConnectedSubnetRoutePolicy = new AzureNative.ManagedNetworkFabric.Inputs.L3IsolationDomainPatchPropertiesConnectedSubnetRoutePolicyArgs
        {
            ExportRoutePolicyId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2",
        },
        Description = "creating L3 isolation domain",
        L3IsolationDomainName = "example-l3domain",
        Location = "eastus",
        NetworkFabricId = "/subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName",
        RedistributeConnectedSubnets = "True",
        RedistributeStaticRoutes = "False",
        ResourceGroupName = "resourceGroupName",
    });

});


```

```go
package main

import (
	managednetworkfabric "github.com/pulumi/pulumi-azure-native-sdk/managednetworkfabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managednetworkfabric.NewL3IsolationDomain(ctx, "l3IsolationDomain", &managednetworkfabric.L3IsolationDomainArgs{
			AggregateRouteConfiguration: managednetworkfabric.L3IsolationDomainPatchPropertiesResponseAggregateRouteConfiguration{
				Ipv4Routes: managednetworkfabric.L3IsolationDomainPatchPropertiesIpv4RoutesArray{
					&managednetworkfabric.L3IsolationDomainPatchPropertiesIpv4RoutesArgs{
						Prefix: pulumi.String("10.0.0.0/24"),
					},
				},
				Ipv6Routes: managednetworkfabric.L3IsolationDomainPatchPropertiesIpv6RoutesArray{
					&managednetworkfabric.L3IsolationDomainPatchPropertiesIpv6RoutesArgs{
						Prefix: pulumi.String("10.0.0.1"),
					},
				},
			},
			ConnectedSubnetRoutePolicy: &managednetworkfabric.L3IsolationDomainPatchPropertiesConnectedSubnetRoutePolicyArgs{
				ExportRoutePolicyId: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2"),
			},
			Description:                  pulumi.String("creating L3 isolation domain"),
			L3IsolationDomainName:        pulumi.String("example-l3domain"),
			Location:                     pulumi.String("eastus"),
			NetworkFabricId:              pulumi.String("/subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName"),
			RedistributeConnectedSubnets: pulumi.String("True"),
			RedistributeStaticRoutes:     pulumi.String("False"),
			ResourceGroupName:            pulumi.String("resourceGroupName"),
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
import com.pulumi.azurenative.managednetworkfabric.L3IsolationDomain;
import com.pulumi.azurenative.managednetworkfabric.L3IsolationDomainArgs;
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
        var l3IsolationDomain = new L3IsolationDomain("l3IsolationDomain", L3IsolationDomainArgs.builder()        
            .aggregateRouteConfiguration(Map.ofEntries(
                Map.entry("ipv4Routes", Map.of("prefix", "10.0.0.0/24")),
                Map.entry("ipv6Routes", Map.of("prefix", "10.0.0.1"))
            ))
            .connectedSubnetRoutePolicy(Map.of("exportRoutePolicyId", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2"))
            .description("creating L3 isolation domain")
            .l3IsolationDomainName("example-l3domain")
            .location("eastus")
            .networkFabricId("/subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName")
            .redistributeConnectedSubnets("True")
            .redistributeStaticRoutes("False")
            .resourceGroupName("resourceGroupName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const l3IsolationDomain = new azure_native.managednetworkfabric.L3IsolationDomain("l3IsolationDomain", {
    aggregateRouteConfiguration: {
        ipv4Routes: [{
            prefix: "10.0.0.0/24",
        }],
        ipv6Routes: [{
            prefix: "10.0.0.1",
        }],
    },
    connectedSubnetRoutePolicy: {
        exportRoutePolicyId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2",
    },
    description: "creating L3 isolation domain",
    l3IsolationDomainName: "example-l3domain",
    location: "eastus",
    networkFabricId: "/subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName",
    redistributeConnectedSubnets: "True",
    redistributeStaticRoutes: "False",
    resourceGroupName: "resourceGroupName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

l3_isolation_domain = azure_native.managednetworkfabric.L3IsolationDomain("l3IsolationDomain",
    aggregate_route_configuration=azure_native.managednetworkfabric.L3IsolationDomainPatchPropertiesResponseAggregateRouteConfigurationArgs(
        ipv4_routes=[azure_native.managednetworkfabric.L3IsolationDomainPatchPropertiesIpv4RoutesArgs(
            prefix="10.0.0.0/24",
        )],
        ipv6_routes=[azure_native.managednetworkfabric.L3IsolationDomainPatchPropertiesIpv6RoutesArgs(
            prefix="10.0.0.1",
        )],
    ),
    connected_subnet_route_policy=azure_native.managednetworkfabric.L3IsolationDomainPatchPropertiesConnectedSubnetRoutePolicyArgs(
        export_route_policy_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2",
    ),
    description="creating L3 isolation domain",
    l3_isolation_domain_name="example-l3domain",
    location="eastus",
    network_fabric_id="/subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName",
    redistribute_connected_subnets="True",
    redistribute_static_routes="False",
    resource_group_name="resourceGroupName")

```

```yaml
resources:
  l3IsolationDomain:
    type: azure-native:managednetworkfabric:L3IsolationDomain
    properties:
      aggregateRouteConfiguration:
        ipv4Routes:
          - prefix: 10.0.0.0/24
        ipv6Routes:
          - prefix: 10.0.0.1
      connectedSubnetRoutePolicy:
        exportRoutePolicyId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2
      description: creating L3 isolation domain
      l3IsolationDomainName: example-l3domain
      location: eastus
      networkFabricId: /subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName
      redistributeConnectedSubnets: True
      redistributeStaticRoutes: False
      resourceGroupName: resourceGroupName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:L3IsolationDomain example-l3domain /subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/example-l3domain 
```
