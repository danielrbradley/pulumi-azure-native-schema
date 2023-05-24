The NetworkToNetworkInterconnect resource definition.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NetworkToNetworkInterconnects_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkToNetworkInterconnect = new AzureNative.ManagedNetworkFabric.NetworkToNetworkInterconnect("networkToNetworkInterconnect", new()
    {
        IsManagementType = "True",
        Layer2Configuration = new AzureNative.ManagedNetworkFabric.Inputs.NetworkToNetworkInterconnectPropertiesLayer2ConfigurationArgs
        {
            Mtu = 1500,
            PortCount = 10,
        },
        Layer3Configuration = new AzureNative.ManagedNetworkFabric.Inputs.Layer3ConfigurationArgs
        {
            ExportRoutePolicyId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2",
            ImportRoutePolicyId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1",
            PeerASN = 50272,
            PrimaryIpv4Prefix = "172.31.0.0/31",
            PrimaryIpv6Prefix = "3FFE:FFFF:0:CD30::a0/126",
            SecondaryIpv4Prefix = "172.31.0.20/31",
            SecondaryIpv6Prefix = "3FFE:FFFF:0:CD30::a4/126",
            VlanId = 2064,
        },
        NetworkFabricName = "FabricName",
        NetworkToNetworkInterconnectName = "DefaultNNI",
        ResourceGroupName = "resourceGroupName",
        UseOptionB = "False",
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
		_, err := managednetworkfabric.NewNetworkToNetworkInterconnect(ctx, "networkToNetworkInterconnect", &managednetworkfabric.NetworkToNetworkInterconnectArgs{
			IsManagementType: pulumi.String("True"),
			Layer2Configuration: &managednetworkfabric.NetworkToNetworkInterconnectPropertiesLayer2ConfigurationArgs{
				Mtu:       pulumi.Int(1500),
				PortCount: pulumi.Int(10),
			},
			Layer3Configuration: &managednetworkfabric.Layer3ConfigurationArgs{
				ExportRoutePolicyId: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2"),
				ImportRoutePolicyId: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1"),
				PeerASN:             pulumi.Int(50272),
				PrimaryIpv4Prefix:   pulumi.String("172.31.0.0/31"),
				PrimaryIpv6Prefix:   pulumi.String("3FFE:FFFF:0:CD30::a0/126"),
				SecondaryIpv4Prefix: pulumi.String("172.31.0.20/31"),
				SecondaryIpv6Prefix: pulumi.String("3FFE:FFFF:0:CD30::a4/126"),
				VlanId:              pulumi.Int(2064),
			},
			NetworkFabricName:                pulumi.String("FabricName"),
			NetworkToNetworkInterconnectName: pulumi.String("DefaultNNI"),
			ResourceGroupName:                pulumi.String("resourceGroupName"),
			UseOptionB:                       pulumi.String("False"),
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
import com.pulumi.azurenative.managednetworkfabric.NetworkToNetworkInterconnect;
import com.pulumi.azurenative.managednetworkfabric.NetworkToNetworkInterconnectArgs;
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
        var networkToNetworkInterconnect = new NetworkToNetworkInterconnect("networkToNetworkInterconnect", NetworkToNetworkInterconnectArgs.builder()        
            .isManagementType("True")
            .layer2Configuration(Map.ofEntries(
                Map.entry("mtu", 1500),
                Map.entry("portCount", 10)
            ))
            .layer3Configuration(Map.ofEntries(
                Map.entry("exportRoutePolicyId", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2"),
                Map.entry("importRoutePolicyId", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1"),
                Map.entry("peerASN", 50272),
                Map.entry("primaryIpv4Prefix", "172.31.0.0/31"),
                Map.entry("primaryIpv6Prefix", "3FFE:FFFF:0:CD30::a0/126"),
                Map.entry("secondaryIpv4Prefix", "172.31.0.20/31"),
                Map.entry("secondaryIpv6Prefix", "3FFE:FFFF:0:CD30::a4/126"),
                Map.entry("vlanId", 2064)
            ))
            .networkFabricName("FabricName")
            .networkToNetworkInterconnectName("DefaultNNI")
            .resourceGroupName("resourceGroupName")
            .useOptionB("False")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkToNetworkInterconnect = new azure_native.managednetworkfabric.NetworkToNetworkInterconnect("networkToNetworkInterconnect", {
    isManagementType: "True",
    layer2Configuration: {
        mtu: 1500,
        portCount: 10,
    },
    layer3Configuration: {
        exportRoutePolicyId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2",
        importRoutePolicyId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1",
        peerASN: 50272,
        primaryIpv4Prefix: "172.31.0.0/31",
        primaryIpv6Prefix: "3FFE:FFFF:0:CD30::a0/126",
        secondaryIpv4Prefix: "172.31.0.20/31",
        secondaryIpv6Prefix: "3FFE:FFFF:0:CD30::a4/126",
        vlanId: 2064,
    },
    networkFabricName: "FabricName",
    networkToNetworkInterconnectName: "DefaultNNI",
    resourceGroupName: "resourceGroupName",
    useOptionB: "False",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_to_network_interconnect = azure_native.managednetworkfabric.NetworkToNetworkInterconnect("networkToNetworkInterconnect",
    is_management_type="True",
    layer2_configuration=azure_native.managednetworkfabric.NetworkToNetworkInterconnectPropertiesLayer2ConfigurationArgs(
        mtu=1500,
        port_count=10,
    ),
    layer3_configuration=azure_native.managednetworkfabric.Layer3ConfigurationArgs(
        export_route_policy_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2",
        import_route_policy_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1",
        peer_asn=50272,
        primary_ipv4_prefix="172.31.0.0/31",
        primary_ipv6_prefix="3FFE:FFFF:0:CD30::a0/126",
        secondary_ipv4_prefix="172.31.0.20/31",
        secondary_ipv6_prefix="3FFE:FFFF:0:CD30::a4/126",
        vlan_id=2064,
    ),
    network_fabric_name="FabricName",
    network_to_network_interconnect_name="DefaultNNI",
    resource_group_name="resourceGroupName",
    use_option_b="False")

```

```yaml
resources:
  networkToNetworkInterconnect:
    type: azure-native:managednetworkfabric:NetworkToNetworkInterconnect
    properties:
      isManagementType: True
      layer2Configuration:
        mtu: 1500
        portCount: 10
      layer3Configuration:
        exportRoutePolicyId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2
        importRoutePolicyId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1
        peerASN: 50272
        primaryIpv4Prefix: 172.31.0.0/31
        primaryIpv6Prefix: 3FFE:FFFF:0:CD30::a0/126
        secondaryIpv4Prefix: 172.31.0.20/31
        secondaryIpv6Prefix: 3FFE:FFFF:0:CD30::a4/126
        vlanId: 2064
      networkFabricName: FabricName
      networkToNetworkInterconnectName: DefaultNNI
      resourceGroupName: resourceGroupName
      useOptionB: False

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:NetworkToNetworkInterconnect DefaultNNI /subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName/networkToNetworkInterconnect/DefaultNNI 
```
