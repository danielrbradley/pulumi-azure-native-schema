The NetworkFabric resource definition.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NetworkFabrics_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkFabric = new AzureNative.ManagedNetworkFabric.NetworkFabric("networkFabric", new()
    {
        FabricASN = 29249,
        Ipv4Prefix = "10.18.0.0/19",
        Ipv6Prefix = "3FFE:FFFF:0:CD40::/59",
        Location = "eastus",
        ManagementNetworkConfiguration = new AzureNative.ManagedNetworkFabric.Inputs.NetworkFabricPropertiesManagementNetworkConfigurationArgs
        {
            InfrastructureVpnConfiguration = new AzureNative.ManagedNetworkFabric.Inputs.NetworkFabricPropertiesInfrastructureVpnConfigurationArgs
            {
                OptionBProperties = new AzureNative.ManagedNetworkFabric.Inputs.FabricOptionBPropertiesArgs
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
            },
            WorkloadVpnConfiguration = new AzureNative.ManagedNetworkFabric.Inputs.NetworkFabricPropertiesWorkloadVpnConfigurationArgs
            {
                OptionBProperties = new AzureNative.ManagedNetworkFabric.Inputs.FabricOptionBPropertiesArgs
                {
                    ExportRouteTargets = new[]
                    {
                        "65046:10050",
                    },
                    ImportRouteTargets = new[]
                    {
                        "65046:10050",
                    },
                },
                PeeringOption = "OptionA",
            },
        },
        NetworkFabricControllerId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/fabricControllerName",
        NetworkFabricName = "FabricName",
        NetworkFabricSku = "M4-A400-A100-C16-aa",
        RackCount = 4,
        ResourceGroupName = "resourceGroupName",
        ServerCountPerRack = 8,
        TerminalServerConfiguration = new AzureNative.ManagedNetworkFabric.Inputs.NetworkFabricPropertiesTerminalServerConfigurationArgs
        {
            Password = "xxxx",
            PrimaryIpv4Prefix = "20.0.0.12/30",
            PrimaryIpv6Prefix = "3FFE:FFFF:0:CD30::a8/126",
            SecondaryIpv4Prefix = "20.0.0.13/30",
            SecondaryIpv6Prefix = "3FFE:FFFF:0:CD30::ac/126",
            SerialNumber = "123456",
            Username = "username",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.managednetworkfabric.NetworkFabric;
import com.pulumi.azurenative.managednetworkfabric.NetworkFabricArgs;
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
        var networkFabric = new NetworkFabric("networkFabric", NetworkFabricArgs.builder()        
            .fabricASN(29249)
            .ipv4Prefix("10.18.0.0/19")
            .ipv6Prefix("3FFE:FFFF:0:CD40::/59")
            .location("eastus")
            .managementNetworkConfiguration(Map.ofEntries(
                Map.entry("infrastructureVpnConfiguration", Map.ofEntries(
                    Map.entry("optionBProperties", Map.ofEntries(
                        Map.entry("exportRouteTargets", "65046:10039"),
                        Map.entry("importRouteTargets", "65046:10039")
                    )),
                    Map.entry("peeringOption", "OptionA")
                )),
                Map.entry("workloadVpnConfiguration", Map.ofEntries(
                    Map.entry("optionBProperties", Map.ofEntries(
                        Map.entry("exportRouteTargets", "65046:10050"),
                        Map.entry("importRouteTargets", "65046:10050")
                    )),
                    Map.entry("peeringOption", "OptionA")
                ))
            ))
            .networkFabricControllerId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/fabricControllerName")
            .networkFabricName("FabricName")
            .networkFabricSku("M4-A400-A100-C16-aa")
            .rackCount(4)
            .resourceGroupName("resourceGroupName")
            .serverCountPerRack(8)
            .terminalServerConfiguration(Map.ofEntries(
                Map.entry("password", "xxxx"),
                Map.entry("primaryIpv4Prefix", "20.0.0.12/30"),
                Map.entry("primaryIpv6Prefix", "3FFE:FFFF:0:CD30::a8/126"),
                Map.entry("secondaryIpv4Prefix", "20.0.0.13/30"),
                Map.entry("secondaryIpv6Prefix", "3FFE:FFFF:0:CD30::ac/126"),
                Map.entry("serialNumber", "123456"),
                Map.entry("username", "username")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkFabric = new azure_native.managednetworkfabric.NetworkFabric("networkFabric", {
    fabricASN: 29249,
    ipv4Prefix: "10.18.0.0/19",
    ipv6Prefix: "3FFE:FFFF:0:CD40::/59",
    location: "eastus",
    managementNetworkConfiguration: {
        infrastructureVpnConfiguration: {
            optionBProperties: {
                exportRouteTargets: ["65046:10039"],
                importRouteTargets: ["65046:10039"],
            },
            peeringOption: "OptionA",
        },
        workloadVpnConfiguration: {
            optionBProperties: {
                exportRouteTargets: ["65046:10050"],
                importRouteTargets: ["65046:10050"],
            },
            peeringOption: "OptionA",
        },
    },
    networkFabricControllerId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/fabricControllerName",
    networkFabricName: "FabricName",
    networkFabricSku: "M4-A400-A100-C16-aa",
    rackCount: 4,
    resourceGroupName: "resourceGroupName",
    serverCountPerRack: 8,
    terminalServerConfiguration: {
        password: "xxxx",
        primaryIpv4Prefix: "20.0.0.12/30",
        primaryIpv6Prefix: "3FFE:FFFF:0:CD30::a8/126",
        secondaryIpv4Prefix: "20.0.0.13/30",
        secondaryIpv6Prefix: "3FFE:FFFF:0:CD30::ac/126",
        serialNumber: "123456",
        username: "username",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_fabric = azure_native.managednetworkfabric.NetworkFabric("networkFabric",
    fabric_asn=29249,
    ipv4_prefix="10.18.0.0/19",
    ipv6_prefix="3FFE:FFFF:0:CD40::/59",
    location="eastus",
    management_network_configuration=azure_native.managednetworkfabric.NetworkFabricPropertiesResponseManagementNetworkConfigurationArgs(
        infrastructure_vpn_configuration={
            "optionBProperties": azure_native.managednetworkfabric.FabricOptionBPropertiesArgs(
                export_route_targets=["65046:10039"],
                import_route_targets=["65046:10039"],
            ),
            "peeringOption": "OptionA",
        },
        workload_vpn_configuration={
            "optionBProperties": azure_native.managednetworkfabric.FabricOptionBPropertiesArgs(
                export_route_targets=["65046:10050"],
                import_route_targets=["65046:10050"],
            ),
            "peeringOption": "OptionA",
        },
    ),
    network_fabric_controller_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/fabricControllerName",
    network_fabric_name="FabricName",
    network_fabric_sku="M4-A400-A100-C16-aa",
    rack_count=4,
    resource_group_name="resourceGroupName",
    server_count_per_rack=8,
    terminal_server_configuration=azure_native.managednetworkfabric.NetworkFabricPropertiesTerminalServerConfigurationArgs(
        password="xxxx",
        primary_ipv4_prefix="20.0.0.12/30",
        primary_ipv6_prefix="3FFE:FFFF:0:CD30::a8/126",
        secondary_ipv4_prefix="20.0.0.13/30",
        secondary_ipv6_prefix="3FFE:FFFF:0:CD30::ac/126",
        serial_number="123456",
        username="username",
    ))

```

```yaml
resources:
  networkFabric:
    type: azure-native:managednetworkfabric:NetworkFabric
    properties:
      fabricASN: 29249
      ipv4Prefix: 10.18.0.0/19
      ipv6Prefix: 3FFE:FFFF:0:CD40::/59
      location: eastus
      managementNetworkConfiguration:
        infrastructureVpnConfiguration:
          optionBProperties:
            exportRouteTargets:
              - 65046:10039
            importRouteTargets:
              - 65046:10039
          peeringOption: OptionA
        workloadVpnConfiguration:
          optionBProperties:
            exportRouteTargets:
              - 65046:10050
            importRouteTargets:
              - 65046:10050
          peeringOption: OptionA
      networkFabricControllerId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/fabricControllerName
      networkFabricName: FabricName
      networkFabricSku: M4-A400-A100-C16-aa
      rackCount: 4
      resourceGroupName: resourceGroupName
      serverCountPerRack: 8
      terminalServerConfiguration:
        password: xxxx
        primaryIpv4Prefix: 20.0.0.12/30
        primaryIpv6Prefix: 3FFE:FFFF:0:CD30::a8/126
        secondaryIpv4Prefix: 20.0.0.13/30
        secondaryIpv6Prefix: 3FFE:FFFF:0:CD30::ac/126
        serialNumber: '123456'
        username: username

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:NetworkFabric FabricName /subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName 
```
