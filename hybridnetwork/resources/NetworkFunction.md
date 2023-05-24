Network function resource response.
API Version: 2021-05-01.
Previous API Version: 2020-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create network function resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkFunction = new AzureNative.HybridNetwork.NetworkFunction("networkFunction", new()
    {
        Device = new AzureNative.HybridNetwork.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourcegroups/rg/providers/Microsoft.HybridNetwork/devices/testDevice",
        },
        Location = "eastus",
        ManagedApplicationParameters = null,
        NetworkFunctionName = "testNf",
        NetworkFunctionUserConfigurations = new[]
        {
            new AzureNative.HybridNetwork.Inputs.NetworkFunctionUserConfigurationArgs
            {
                NetworkInterfaces = new[]
                {
                    new AzureNative.HybridNetwork.Inputs.NetworkInterfaceArgs
                    {
                        IpConfigurations = new[]
                        {
                            new AzureNative.HybridNetwork.Inputs.NetworkInterfaceIPConfigurationArgs
                            {
                                Gateway = "",
                                IpAddress = "",
                                IpAllocationMethod = "Dynamic",
                                IpVersion = "IPv4",
                                Subnet = "",
                            },
                        },
                        MacAddress = "",
                        NetworkInterfaceName = "nic1",
                        VmSwitchType = "Management",
                    },
                    new AzureNative.HybridNetwork.Inputs.NetworkInterfaceArgs
                    {
                        IpConfigurations = new[]
                        {
                            new AzureNative.HybridNetwork.Inputs.NetworkInterfaceIPConfigurationArgs
                            {
                                Gateway = "",
                                IpAddress = "",
                                IpAllocationMethod = "Dynamic",
                                IpVersion = "IPv4",
                                Subnet = "",
                            },
                        },
                        MacAddress = "DC-97-F8-79-16-7D",
                        NetworkInterfaceName = "nic2",
                        VmSwitchType = "Wan",
                    },
                },
                RoleName = "testRole",
                UserDataParameters = null,
            },
        },
        ResourceGroupName = "rg",
        SkuName = "testSku",
        VendorName = "testVendor",
    });

});


```

```go
package main

import (
	hybridnetwork "github.com/pulumi/pulumi-azure-native-sdk/hybridnetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridnetwork.NewNetworkFunction(ctx, "networkFunction", &hybridnetwork.NetworkFunctionArgs{
			Device: &hybridnetwork.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourcegroups/rg/providers/Microsoft.HybridNetwork/devices/testDevice"),
			},
			Location:                     pulumi.String("eastus"),
			ManagedApplicationParameters: nil,
			NetworkFunctionName:          pulumi.String("testNf"),
			NetworkFunctionUserConfigurations: []hybridnetwork.NetworkFunctionUserConfigurationArgs{
				{
					NetworkInterfaces: hybridnetwork.NetworkInterfaceArray{
						{
							IpConfigurations: hybridnetwork.NetworkInterfaceIPConfigurationArray{
								{
									Gateway:            pulumi.String(""),
									IpAddress:          pulumi.String(""),
									IpAllocationMethod: pulumi.String("Dynamic"),
									IpVersion:          pulumi.String("IPv4"),
									Subnet:             pulumi.String(""),
								},
							},
							MacAddress:           pulumi.String(""),
							NetworkInterfaceName: pulumi.String("nic1"),
							VmSwitchType:         pulumi.String("Management"),
						},
						{
							IpConfigurations: hybridnetwork.NetworkInterfaceIPConfigurationArray{
								{
									Gateway:            pulumi.String(""),
									IpAddress:          pulumi.String(""),
									IpAllocationMethod: pulumi.String("Dynamic"),
									IpVersion:          pulumi.String("IPv4"),
									Subnet:             pulumi.String(""),
								},
							},
							MacAddress:           pulumi.String("DC-97-F8-79-16-7D"),
							NetworkInterfaceName: pulumi.String("nic2"),
							VmSwitchType:         pulumi.String("Wan"),
						},
					},
					RoleName:           pulumi.String("testRole"),
					UserDataParameters: nil,
				},
			},
			ResourceGroupName: pulumi.String("rg"),
			SkuName:           pulumi.String("testSku"),
			VendorName:        pulumi.String("testVendor"),
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
import com.pulumi.azurenative.hybridnetwork.NetworkFunction;
import com.pulumi.azurenative.hybridnetwork.NetworkFunctionArgs;
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
        var networkFunction = new NetworkFunction("networkFunction", NetworkFunctionArgs.builder()        
            .device(Map.of("id", "/subscriptions/subid/resourcegroups/rg/providers/Microsoft.HybridNetwork/devices/testDevice"))
            .location("eastus")
            .managedApplicationParameters()
            .networkFunctionName("testNf")
            .networkFunctionUserConfigurations(Map.ofEntries(
                Map.entry("networkInterfaces",                 
                    Map.ofEntries(
                        Map.entry("ipConfigurations", Map.ofEntries(
                            Map.entry("gateway", ""),
                            Map.entry("ipAddress", ""),
                            Map.entry("ipAllocationMethod", "Dynamic"),
                            Map.entry("ipVersion", "IPv4"),
                            Map.entry("subnet", "")
                        )),
                        Map.entry("macAddress", ""),
                        Map.entry("networkInterfaceName", "nic1"),
                        Map.entry("vmSwitchType", "Management")
                    ),
                    Map.ofEntries(
                        Map.entry("ipConfigurations", Map.ofEntries(
                            Map.entry("gateway", ""),
                            Map.entry("ipAddress", ""),
                            Map.entry("ipAllocationMethod", "Dynamic"),
                            Map.entry("ipVersion", "IPv4"),
                            Map.entry("subnet", "")
                        )),
                        Map.entry("macAddress", "DC-97-F8-79-16-7D"),
                        Map.entry("networkInterfaceName", "nic2"),
                        Map.entry("vmSwitchType", "Wan")
                    )),
                Map.entry("roleName", "testRole"),
                Map.entry("userDataParameters", )
            ))
            .resourceGroupName("rg")
            .skuName("testSku")
            .vendorName("testVendor")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkFunction = new azure_native.hybridnetwork.NetworkFunction("networkFunction", {
    device: {
        id: "/subscriptions/subid/resourcegroups/rg/providers/Microsoft.HybridNetwork/devices/testDevice",
    },
    location: "eastus",
    managedApplicationParameters: {},
    networkFunctionName: "testNf",
    networkFunctionUserConfigurations: [{
        networkInterfaces: [
            {
                ipConfigurations: [{
                    gateway: "",
                    ipAddress: "",
                    ipAllocationMethod: "Dynamic",
                    ipVersion: "IPv4",
                    subnet: "",
                }],
                macAddress: "",
                networkInterfaceName: "nic1",
                vmSwitchType: "Management",
            },
            {
                ipConfigurations: [{
                    gateway: "",
                    ipAddress: "",
                    ipAllocationMethod: "Dynamic",
                    ipVersion: "IPv4",
                    subnet: "",
                }],
                macAddress: "DC-97-F8-79-16-7D",
                networkInterfaceName: "nic2",
                vmSwitchType: "Wan",
            },
        ],
        roleName: "testRole",
        userDataParameters: {},
    }],
    resourceGroupName: "rg",
    skuName: "testSku",
    vendorName: "testVendor",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_function = azure_native.hybridnetwork.NetworkFunction("networkFunction",
    device=azure_native.hybridnetwork.SubResourceArgs(
        id="/subscriptions/subid/resourcegroups/rg/providers/Microsoft.HybridNetwork/devices/testDevice",
    ),
    location="eastus",
    managed_application_parameters={},
    network_function_name="testNf",
    network_function_user_configurations=[{
        "networkInterfaces": [
            {
                "ipConfigurations": [azure_native.hybridnetwork.NetworkInterfaceIPConfigurationArgs(
                    gateway="",
                    ip_address="",
                    ip_allocation_method="Dynamic",
                    ip_version="IPv4",
                    subnet="",
                )],
                "macAddress": "",
                "networkInterfaceName": "nic1",
                "vmSwitchType": "Management",
            },
            {
                "ipConfigurations": [azure_native.hybridnetwork.NetworkInterfaceIPConfigurationArgs(
                    gateway="",
                    ip_address="",
                    ip_allocation_method="Dynamic",
                    ip_version="IPv4",
                    subnet="",
                )],
                "macAddress": "DC-97-F8-79-16-7D",
                "networkInterfaceName": "nic2",
                "vmSwitchType": "Wan",
            },
        ],
        "roleName": "testRole",
        "userDataParameters": {},
    }],
    resource_group_name="rg",
    sku_name="testSku",
    vendor_name="testVendor")

```

```yaml
resources:
  networkFunction:
    type: azure-native:hybridnetwork:NetworkFunction
    properties:
      device:
        id: /subscriptions/subid/resourcegroups/rg/providers/Microsoft.HybridNetwork/devices/testDevice
      location: eastus
      managedApplicationParameters: {}
      networkFunctionName: testNf
      networkFunctionUserConfigurations:
        - networkInterfaces:
            - ipConfigurations:
                - gateway:
                  ipAddress:
                  ipAllocationMethod: Dynamic
                  ipVersion: IPv4
                  subnet:
              macAddress:
              networkInterfaceName: nic1
              vmSwitchType: Management
            - ipConfigurations:
                - gateway:
                  ipAddress:
                  ipAllocationMethod: Dynamic
                  ipVersion: IPv4
                  subnet:
              macAddress: DC-97-F8-79-16-7D
              networkInterfaceName: nic2
              vmSwitchType: Wan
          roleName: testRole
          userDataParameters: {}
      resourceGroupName: rg
      skuName: testSku
      vendorName: testVendor

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridnetwork:NetworkFunction testNf /subscriptions/subid/resourcegroups/rg/providers/Microsoft.HybridNetwork/networkFunctions/testNf 
```
