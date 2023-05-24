Defines the ExternalNetwork item.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ExternalNetworks_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var externalNetwork = new AzureNative.ManagedNetworkFabric.ExternalNetwork("externalNetwork", new()
    {
        ExportRoutePolicyId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName",
        ExternalNetworkName = "example-externalnetwork",
        ImportRoutePolicyId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName",
        L3IsolationDomainName = "example-l3domain",
        OptionAProperties = new AzureNative.ManagedNetworkFabric.Inputs.ExternalNetworkPropertiesOptionAPropertiesArgs
        {
            Mtu = 1500,
            PeerASN = 65047,
            PrimaryIpv4Prefix = "10.1.1.0/30",
            PrimaryIpv6Prefix = "3FFE:FFFF:0:CD30::a0/126",
            SecondaryIpv4Prefix = "10.1.1.4/30",
            SecondaryIpv6Prefix = "3FFE:FFFF:0:CD30::a4/126",
            VlanId = 1001,
        },
        OptionBProperties = new AzureNative.ManagedNetworkFabric.Inputs.OptionBPropertiesArgs
        {
            ExportRouteTargets = new[]
            {
                "65046:10039",
            },
            ImportRouteTargets = new[]
            {
                "65046:10039",
            },
        },
        PeeringOption = "OptionA",
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
		_, err := managednetworkfabric.NewExternalNetwork(ctx, "externalNetwork", &managednetworkfabric.ExternalNetworkArgs{
			ExportRoutePolicyId:   pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName"),
			ExternalNetworkName:   pulumi.String("example-externalnetwork"),
			ImportRoutePolicyId:   pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName"),
			L3IsolationDomainName: pulumi.String("example-l3domain"),
			OptionAProperties: &managednetworkfabric.ExternalNetworkPropertiesOptionAPropertiesArgs{
				Mtu:                 pulumi.Int(1500),
				PeerASN:             pulumi.Int(65047),
				PrimaryIpv4Prefix:   pulumi.String("10.1.1.0/30"),
				PrimaryIpv6Prefix:   pulumi.String("3FFE:FFFF:0:CD30::a0/126"),
				SecondaryIpv4Prefix: pulumi.String("10.1.1.4/30"),
				SecondaryIpv6Prefix: pulumi.String("3FFE:FFFF:0:CD30::a4/126"),
				VlanId:              pulumi.Int(1001),
			},
			OptionBProperties: &managednetworkfabric.OptionBPropertiesArgs{
				ExportRouteTargets: pulumi.StringArray{
					pulumi.String("65046:10039"),
				},
				ImportRouteTargets: pulumi.StringArray{
					pulumi.String("65046:10039"),
				},
			},
			PeeringOption:     pulumi.String("OptionA"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
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
import com.pulumi.azurenative.managednetworkfabric.ExternalNetwork;
import com.pulumi.azurenative.managednetworkfabric.ExternalNetworkArgs;
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
        var externalNetwork = new ExternalNetwork("externalNetwork", ExternalNetworkArgs.builder()        
            .exportRoutePolicyId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName")
            .externalNetworkName("example-externalnetwork")
            .importRoutePolicyId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName")
            .l3IsolationDomainName("example-l3domain")
            .optionAProperties(Map.ofEntries(
                Map.entry("mtu", 1500),
                Map.entry("peerASN", 65047),
                Map.entry("primaryIpv4Prefix", "10.1.1.0/30"),
                Map.entry("primaryIpv6Prefix", "3FFE:FFFF:0:CD30::a0/126"),
                Map.entry("secondaryIpv4Prefix", "10.1.1.4/30"),
                Map.entry("secondaryIpv6Prefix", "3FFE:FFFF:0:CD30::a4/126"),
                Map.entry("vlanId", 1001)
            ))
            .optionBProperties(Map.ofEntries(
                Map.entry("exportRouteTargets", "65046:10039"),
                Map.entry("importRouteTargets", "65046:10039")
            ))
            .peeringOption("OptionA")
            .resourceGroupName("resourceGroupName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const externalNetwork = new azure_native.managednetworkfabric.ExternalNetwork("externalNetwork", {
    exportRoutePolicyId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName",
    externalNetworkName: "example-externalnetwork",
    importRoutePolicyId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName",
    l3IsolationDomainName: "example-l3domain",
    optionAProperties: {
        mtu: 1500,
        peerASN: 65047,
        primaryIpv4Prefix: "10.1.1.0/30",
        primaryIpv6Prefix: "3FFE:FFFF:0:CD30::a0/126",
        secondaryIpv4Prefix: "10.1.1.4/30",
        secondaryIpv6Prefix: "3FFE:FFFF:0:CD30::a4/126",
        vlanId: 1001,
    },
    optionBProperties: {
        exportRouteTargets: ["65046:10039"],
        importRouteTargets: ["65046:10039"],
    },
    peeringOption: "OptionA",
    resourceGroupName: "resourceGroupName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

external_network = azure_native.managednetworkfabric.ExternalNetwork("externalNetwork",
    export_route_policy_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName",
    external_network_name="example-externalnetwork",
    import_route_policy_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName",
    l3_isolation_domain_name="example-l3domain",
    option_a_properties=azure_native.managednetworkfabric.ExternalNetworkPropertiesOptionAPropertiesArgs(
        mtu=1500,
        peer_asn=65047,
        primary_ipv4_prefix="10.1.1.0/30",
        primary_ipv6_prefix="3FFE:FFFF:0:CD30::a0/126",
        secondary_ipv4_prefix="10.1.1.4/30",
        secondary_ipv6_prefix="3FFE:FFFF:0:CD30::a4/126",
        vlan_id=1001,
    ),
    option_b_properties=azure_native.managednetworkfabric.OptionBPropertiesArgs(
        export_route_targets=["65046:10039"],
        import_route_targets=["65046:10039"],
    ),
    peering_option="OptionA",
    resource_group_name="resourceGroupName")

```

```yaml
resources:
  externalNetwork:
    type: azure-native:managednetworkfabric:ExternalNetwork
    properties:
      exportRoutePolicyId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName
      externalNetworkName: example-externalnetwork
      importRoutePolicyId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName
      l3IsolationDomainName: example-l3domain
      optionAProperties:
        mtu: 1500
        peerASN: 65047
        primaryIpv4Prefix: 10.1.1.0/30
        primaryIpv6Prefix: 3FFE:FFFF:0:CD30::a0/126
        secondaryIpv4Prefix: 10.1.1.4/30
        secondaryIpv6Prefix: 3FFE:FFFF:0:CD30::a4/126
        vlanId: 1001
      optionBProperties:
        exportRouteTargets:
          - 65046:10039
        importRouteTargets:
          - 65046:10039
      peeringOption: OptionA
      resourceGroupName: resourceGroupName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:ExternalNetwork example-externalnetwork /subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/example-l3domain/externalNetworks/example-externalnetwork 
```
