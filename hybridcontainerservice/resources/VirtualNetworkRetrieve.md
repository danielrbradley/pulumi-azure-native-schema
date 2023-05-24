The virtualNetworks resource definition.
API Version: 2022-09-01-preview.
Previous API Version: 2022-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutVirtualNetwork
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetworkRetrieve = new AzureNative.HybridContainerService.VirtualNetworkRetrieve("virtualNetworkRetrieve", new()
    {
        ExtendedLocation = new AzureNative.HybridContainerService.Inputs.VirtualNetworksExtendedLocationArgs
        {
            Name = "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation",
            Type = "CustomLocation",
        },
        Location = "westus",
        Properties = new AzureNative.HybridContainerService.Inputs.VirtualNetworksPropertiesArgs
        {
            InfraVnetProfile = new AzureNative.HybridContainerService.Inputs.VirtualNetworksPropertiesInfraVnetProfileArgs
            {
                Hci = new AzureNative.HybridContainerService.Inputs.VirtualNetworksPropertiesHciArgs
                {
                    MocGroup = "target-group",
                    MocLocation = "MocLocation",
                    MocVnetName = "test-vnet",
                },
            },
            VipPool = new[]
            {
                new AzureNative.HybridContainerService.Inputs.VirtualNetworksPropertiesVipPoolArgs
                {
                    EndIP = "192.168.0.50",
                    StartIP = "192.168.0.10",
                },
            },
            VmipPool = new[]
            {
                new AzureNative.HybridContainerService.Inputs.VirtualNetworksPropertiesVmipPoolArgs
                {
                    EndIP = "192.168.0.130",
                    StartIP = "192.168.0.110",
                },
            },
        },
        ResourceGroupName = "test-arcappliance-resgrp",
        VirtualNetworksName = "test-vnet-static",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hybridcontainerservice.VirtualNetworkRetrieve;
import com.pulumi.azurenative.hybridcontainerservice.VirtualNetworkRetrieveArgs;
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
        var virtualNetworkRetrieve = new VirtualNetworkRetrieve("virtualNetworkRetrieve", VirtualNetworkRetrieveArgs.builder()        
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation"),
                Map.entry("type", "CustomLocation")
            ))
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("infraVnetProfile", Map.of("hci", Map.ofEntries(
                    Map.entry("mocGroup", "target-group"),
                    Map.entry("mocLocation", "MocLocation"),
                    Map.entry("mocVnetName", "test-vnet")
                ))),
                Map.entry("vipPool", Map.ofEntries(
                    Map.entry("endIP", "192.168.0.50"),
                    Map.entry("startIP", "192.168.0.10")
                )),
                Map.entry("vmipPool", Map.ofEntries(
                    Map.entry("endIP", "192.168.0.130"),
                    Map.entry("startIP", "192.168.0.110")
                ))
            ))
            .resourceGroupName("test-arcappliance-resgrp")
            .virtualNetworksName("test-vnet-static")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetworkRetrieve = new azure_native.hybridcontainerservice.VirtualNetworkRetrieve("virtualNetworkRetrieve", {
    extendedLocation: {
        name: "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation",
        type: "CustomLocation",
    },
    location: "westus",
    properties: {
        infraVnetProfile: {
            hci: {
                mocGroup: "target-group",
                mocLocation: "MocLocation",
                mocVnetName: "test-vnet",
            },
        },
        vipPool: [{
            endIP: "192.168.0.50",
            startIP: "192.168.0.10",
        }],
        vmipPool: [{
            endIP: "192.168.0.130",
            startIP: "192.168.0.110",
        }],
    },
    resourceGroupName: "test-arcappliance-resgrp",
    virtualNetworksName: "test-vnet-static",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network_retrieve = azure_native.hybridcontainerservice.VirtualNetworkRetrieve("virtualNetworkRetrieve",
    extended_location=azure_native.hybridcontainerservice.VirtualNetworksExtendedLocationArgs(
        name="/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation",
        type="CustomLocation",
    ),
    location="westus",
    properties=azure_native.hybridcontainerservice.VirtualNetworksPropertiesResponseArgs(
        infra_vnet_profile={
            "hci": azure_native.hybridcontainerservice.VirtualNetworksPropertiesHciArgs(
                moc_group="target-group",
                moc_location="MocLocation",
                moc_vnet_name="test-vnet",
            ),
        },
        vip_pool=[azure_native.hybridcontainerservice.VirtualNetworksPropertiesVipPoolArgs(
            end_ip="192.168.0.50",
            start_ip="192.168.0.10",
        )],
        vmip_pool=[azure_native.hybridcontainerservice.VirtualNetworksPropertiesVmipPoolArgs(
            end_ip="192.168.0.130",
            start_ip="192.168.0.110",
        )],
    ),
    resource_group_name="test-arcappliance-resgrp",
    virtual_networks_name="test-vnet-static")

```

```yaml
resources:
  virtualNetworkRetrieve:
    type: azure-native:hybridcontainerservice:VirtualNetworkRetrieve
    properties:
      extendedLocation:
        name: /subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation
        type: CustomLocation
      location: westus
      properties:
        infraVnetProfile:
          hci:
            mocGroup: target-group
            mocLocation: MocLocation
            mocVnetName: test-vnet
        vipPool:
          - endIP: 192.168.0.50
            startIP: 192.168.0.10
        vmipPool:
          - endIP: 192.168.0.130
            startIP: 192.168.0.110
      resourceGroupName: test-arcappliance-resgrp
      virtualNetworksName: test-vnet-static

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridcontainerservice:VirtualNetworkRetrieve test-vnet-static /subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/virtualNetworks/test-vnet-static 
```
