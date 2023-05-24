A virtual machine.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VirtualMachines_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.DevTestLab.VirtualMachine("virtualMachine", new()
    {
        AllowClaim = true,
        DisallowPublicIpAddress = true,
        GalleryImageReference = new AzureNative.DevTestLab.Inputs.GalleryImageReferenceArgs
        {
            Offer = "UbuntuServer",
            OsType = "Linux",
            Publisher = "Canonical",
            Sku = "16.04-LTS",
            Version = "Latest",
        },
        LabName = "{labName}",
        LabSubnetName = "{virtualNetworkName}Subnet",
        LabVirtualNetworkId = "/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualnetworks/{virtualNetworkName}",
        Location = "{location}",
        Name = "{vmName}",
        Password = "{userPassword}",
        ResourceGroupName = "resourceGroupName",
        Size = "Standard_A2_v2",
        StorageType = "Standard",
        Tags = 
        {
            { "tagName1", "tagValue1" },
        },
        UserName = "{userName}",
    });

});


```

```go
package main

import (
	devtestlab "github.com/pulumi/pulumi-azure-native-sdk/devtestlab"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devtestlab.NewVirtualMachine(ctx, "virtualMachine", &devtestlab.VirtualMachineArgs{
			AllowClaim:              pulumi.Bool(true),
			DisallowPublicIpAddress: pulumi.Bool(true),
			GalleryImageReference: &devtestlab.GalleryImageReferenceArgs{
				Offer:     pulumi.String("UbuntuServer"),
				OsType:    pulumi.String("Linux"),
				Publisher: pulumi.String("Canonical"),
				Sku:       pulumi.String("16.04-LTS"),
				Version:   pulumi.String("Latest"),
			},
			LabName:             pulumi.String("{labName}"),
			LabSubnetName:       pulumi.String("{virtualNetworkName}Subnet"),
			LabVirtualNetworkId: pulumi.String("/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualnetworks/{virtualNetworkName}"),
			Location:            pulumi.String("{location}"),
			Name:                pulumi.String("{vmName}"),
			Password:            pulumi.String("{userPassword}"),
			ResourceGroupName:   pulumi.String("resourceGroupName"),
			Size:                pulumi.String("Standard_A2_v2"),
			StorageType:         pulumi.String("Standard"),
			Tags: pulumi.StringMap{
				"tagName1": pulumi.String("tagValue1"),
			},
			UserName: pulumi.String("{userName}"),
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
import com.pulumi.azurenative.devtestlab.VirtualMachine;
import com.pulumi.azurenative.devtestlab.VirtualMachineArgs;
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
            .allowClaim(true)
            .disallowPublicIpAddress(true)
            .galleryImageReference(Map.ofEntries(
                Map.entry("offer", "UbuntuServer"),
                Map.entry("osType", "Linux"),
                Map.entry("publisher", "Canonical"),
                Map.entry("sku", "16.04-LTS"),
                Map.entry("version", "Latest")
            ))
            .labName("{labName}")
            .labSubnetName("{virtualNetworkName}Subnet")
            .labVirtualNetworkId("/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualnetworks/{virtualNetworkName}")
            .location("{location}")
            .name("{vmName}")
            .password("{userPassword}")
            .resourceGroupName("resourceGroupName")
            .size("Standard_A2_v2")
            .storageType("Standard")
            .tags(Map.of("tagName1", "tagValue1"))
            .userName("{userName}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.devtestlab.VirtualMachine("virtualMachine", {
    allowClaim: true,
    disallowPublicIpAddress: true,
    galleryImageReference: {
        offer: "UbuntuServer",
        osType: "Linux",
        publisher: "Canonical",
        sku: "16.04-LTS",
        version: "Latest",
    },
    labName: "{labName}",
    labSubnetName: "{virtualNetworkName}Subnet",
    labVirtualNetworkId: "/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualnetworks/{virtualNetworkName}",
    location: "{location}",
    name: "{vmName}",
    password: "{userPassword}",
    resourceGroupName: "resourceGroupName",
    size: "Standard_A2_v2",
    storageType: "Standard",
    tags: {
        tagName1: "tagValue1",
    },
    userName: "{userName}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.devtestlab.VirtualMachine("virtualMachine",
    allow_claim=True,
    disallow_public_ip_address=True,
    gallery_image_reference=azure_native.devtestlab.GalleryImageReferenceArgs(
        offer="UbuntuServer",
        os_type="Linux",
        publisher="Canonical",
        sku="16.04-LTS",
        version="Latest",
    ),
    lab_name="{labName}",
    lab_subnet_name="{virtualNetworkName}Subnet",
    lab_virtual_network_id="/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualnetworks/{virtualNetworkName}",
    location="{location}",
    name="{vmName}",
    password="{userPassword}",
    resource_group_name="resourceGroupName",
    size="Standard_A2_v2",
    storage_type="Standard",
    tags={
        "tagName1": "tagValue1",
    },
    user_name="{userName}")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:devtestlab:VirtualMachine
    properties:
      allowClaim: true
      disallowPublicIpAddress: true
      galleryImageReference:
        offer: UbuntuServer
        osType: Linux
        publisher: Canonical
        sku: 16.04-LTS
        version: Latest
      labName: '{labName}'
      labSubnetName: '{virtualNetworkName}Subnet'
      labVirtualNetworkId: /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualnetworks/{virtualNetworkName}
      location: '{location}'
      name: '{vmName}'
      password: '{userPassword}'
      resourceGroupName: resourceGroupName
      size: Standard_A2_v2
      storageType: Standard
      tags:
        tagName1: tagValue1
      userName: '{userName}'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:VirtualMachine {vmName} /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/{vmName} 
```
