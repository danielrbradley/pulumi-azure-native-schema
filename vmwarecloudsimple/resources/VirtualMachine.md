Virtual machine model
API Version: 2019-04-01.
Previous API Version: 2019-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateVirtualMachine
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.VMwareCloudSimple.VirtualMachine("virtualMachine", new()
    {
        AmountOfRam = 4096,
        Disks = new[]
        {
            new AzureNative.VMwareCloudSimple.Inputs.VirtualDiskArgs
            {
                ControllerId = "1000",
                IndependenceMode = AzureNative.VMwareCloudSimple.DiskIndependenceMode.Persistent,
                TotalSize = 10485760,
                VirtualDiskId = "2000",
            },
        },
        Location = "westus2",
        Nics = new[]
        {
            new AzureNative.VMwareCloudSimple.Inputs.VirtualNicArgs
            {
                Network = new AzureNative.VMwareCloudSimple.Inputs.VirtualNetworkArgs
                {
                    Id = "/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualNetworks/dvportgroup-19",
                },
                NicType = AzureNative.VMwareCloudSimple.NICType.E1000,
                PowerOnBoot = true,
                VirtualNicId = "4000",
            },
        },
        NumberOfCores = 2,
        PrivateCloudId = "/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud",
        ResourceGroupName = "myResourceGroup",
        ResourcePool = new AzureNative.VMwareCloudSimple.Inputs.ResourcePoolArgs
        {
            Id = "/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/resourcePools/resgroup-26",
        },
        TemplateId = "/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualMachineTemplates/vm-34",
        VirtualMachineName = "myVirtualMachine",
    });

});


```

```go
package main

import (
	vmwarecloudsimple "github.com/pulumi/pulumi-azure-native-sdk/vmwarecloudsimple"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := vmwarecloudsimple.NewVirtualMachine(ctx, "virtualMachine", &vmwarecloudsimple.VirtualMachineArgs{
			AmountOfRam: pulumi.Int(4096),
			Disks: []vmwarecloudsimple.VirtualDiskArgs{
				{
					ControllerId:     pulumi.String("1000"),
					IndependenceMode: vmwarecloudsimple.DiskIndependenceModePersistent,
					TotalSize:        pulumi.Int(10485760),
					VirtualDiskId:    pulumi.String("2000"),
				},
			},
			Location: pulumi.String("westus2"),
			Nics: []vmwarecloudsimple.VirtualNicArgs{
				{
					Network: {
						Id: pulumi.String("/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualNetworks/dvportgroup-19"),
					},
					NicType:      vmwarecloudsimple.NICTypeE1000,
					PowerOnBoot:  pulumi.Bool(true),
					VirtualNicId: pulumi.String("4000"),
				},
			},
			NumberOfCores:     pulumi.Int(2),
			PrivateCloudId:    pulumi.String("/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ResourcePool: &vmwarecloudsimple.ResourcePoolArgs{
				Id: pulumi.String("/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/resourcePools/resgroup-26"),
			},
			TemplateId:         pulumi.String("/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualMachineTemplates/vm-34"),
			VirtualMachineName: pulumi.String("myVirtualMachine"),
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
import com.pulumi.azurenative.vmwarecloudsimple.VirtualMachine;
import com.pulumi.azurenative.vmwarecloudsimple.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .amountOfRam(4096)
            .disks(Map.ofEntries(
                Map.entry("controllerId", "1000"),
                Map.entry("independenceMode", "persistent"),
                Map.entry("totalSize", 10485760),
                Map.entry("virtualDiskId", "2000")
            ))
            .location("westus2")
            .nics(Map.ofEntries(
                Map.entry("network", Map.of("id", "/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualNetworks/dvportgroup-19")),
                Map.entry("nicType", "E1000"),
                Map.entry("powerOnBoot", true),
                Map.entry("virtualNicId", "4000")
            ))
            .numberOfCores(2)
            .privateCloudId("/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud")
            .resourceGroupName("myResourceGroup")
            .resourcePool(Map.of("id", "/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/resourcePools/resgroup-26"))
            .templateId("/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualMachineTemplates/vm-34")
            .virtualMachineName("myVirtualMachine")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.vmwarecloudsimple.VirtualMachine("virtualMachine", {
    amountOfRam: 4096,
    disks: [{
        controllerId: "1000",
        independenceMode: azure_native.vmwarecloudsimple.DiskIndependenceMode.Persistent,
        totalSize: 10485760,
        virtualDiskId: "2000",
    }],
    location: "westus2",
    nics: [{
        network: {
            id: "/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualNetworks/dvportgroup-19",
        },
        nicType: azure_native.vmwarecloudsimple.NICType.E1000,
        powerOnBoot: true,
        virtualNicId: "4000",
    }],
    numberOfCores: 2,
    privateCloudId: "/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud",
    resourceGroupName: "myResourceGroup",
    resourcePool: {
        id: "/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/resourcePools/resgroup-26",
    },
    templateId: "/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualMachineTemplates/vm-34",
    virtualMachineName: "myVirtualMachine",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.vmwarecloudsimple.VirtualMachine("virtualMachine",
    amount_of_ram=4096,
    disks=[azure_native.vmwarecloudsimple.VirtualDiskArgs(
        controller_id="1000",
        independence_mode=azure_native.vmwarecloudsimple.DiskIndependenceMode.PERSISTENT,
        total_size=10485760,
        virtual_disk_id="2000",
    )],
    location="westus2",
    nics=[{
        "network": azure_native.vmwarecloudsimple.VirtualNetworkArgs(
            id="/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualNetworks/dvportgroup-19",
        ),
        "nicType": azure_native.vmwarecloudsimple.NICType.E1000,
        "powerOnBoot": True,
        "virtualNicId": "4000",
    }],
    number_of_cores=2,
    private_cloud_id="/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud",
    resource_group_name="myResourceGroup",
    resource_pool=azure_native.vmwarecloudsimple.ResourcePoolArgs(
        id="/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/resourcePools/resgroup-26",
    ),
    template_id="/subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualMachineTemplates/vm-34",
    virtual_machine_name="myVirtualMachine")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:vmwarecloudsimple:VirtualMachine
    properties:
      amountOfRam: 4096
      disks:
        - controllerId: '1000'
          independenceMode: persistent
          totalSize: 1.048576e+07
          virtualDiskId: '2000'
      location: westus2
      nics:
        - network:
            id: /subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualNetworks/dvportgroup-19
          nicType: E1000
          powerOnBoot: true
          virtualNicId: '4000'
      numberOfCores: 2
      privateCloudId: /subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud
      resourceGroupName: myResourceGroup
      resourcePool:
        id: /subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/resourcePools/resgroup-26
      templateId: /subscriptions/{subscription-id}/providers/Microsoft.VMwareCloudSimple/locations/westus2/privateClouds/myPrivateCloud/virtualMachineTemplates/vm-34
      virtualMachineName: myVirtualMachine

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:vmwarecloudsimple:VirtualMachine myVirtualMachine /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.VMwareCloudSimple/virtualMachines/myVirtualMachine 
```
