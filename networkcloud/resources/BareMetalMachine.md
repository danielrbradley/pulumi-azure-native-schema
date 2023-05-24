
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update bare metal machine
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var bareMetalMachine = new AzureNative.NetworkCloud.BareMetalMachine("bareMetalMachine", new()
    {
        BareMetalMachineName = "bareMetalMachineName",
        BmcConnectionString = "bmcconnectionstring",
        BmcCredentials = new AzureNative.NetworkCloud.Inputs.AdministrativeCredentialsArgs
        {
            Password = "{password}",
            Username = "bmcuser",
        },
        BmcMacAddress = "00:00:4f:00:57:00",
        BootMacAddress = "00:00:4e:00:58:af",
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
            Type = "CustomLocation",
        },
        Location = "location",
        MachineDetails = "User-provided machine details.",
        MachineName = "r01c001",
        MachineSkuId = "684E-3B16-399E",
        RackId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName",
        RackSlot = 1,
        ResourceGroupName = "resourceGroupName",
        SerialNumber = "BM1219XXX",
        Tags = 
        {
            { "key1", "myvalue1" },
            { "key2", "myvalue2" },
        },
    });

});


```

```go
package main

import (
	networkcloud "github.com/pulumi/pulumi-azure-native-sdk/networkcloud"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := networkcloud.NewBareMetalMachine(ctx, "bareMetalMachine", &networkcloud.BareMetalMachineArgs{
			BareMetalMachineName: pulumi.String("bareMetalMachineName"),
			BmcConnectionString:  pulumi.String("bmcconnectionstring"),
			BmcCredentials: &networkcloud.AdministrativeCredentialsArgs{
				Password: pulumi.String("{password}"),
				Username: pulumi.String("bmcuser"),
			},
			BmcMacAddress:  pulumi.String("00:00:4f:00:57:00"),
			BootMacAddress: pulumi.String("00:00:4e:00:58:af"),
			ExtendedLocation: &networkcloud.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
				Type: pulumi.String("CustomLocation"),
			},
			Location:          pulumi.String("location"),
			MachineDetails:    pulumi.String("User-provided machine details."),
			MachineName:       pulumi.String("r01c001"),
			MachineSkuId:      pulumi.String("684E-3B16-399E"),
			RackId:            pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName"),
			RackSlot:          pulumi.Float64(1),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			SerialNumber:      pulumi.String("BM1219XXX"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("myvalue1"),
				"key2": pulumi.String("myvalue2"),
			},
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
import com.pulumi.azurenative.networkcloud.BareMetalMachine;
import com.pulumi.azurenative.networkcloud.BareMetalMachineArgs;
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
        var bareMetalMachine = new BareMetalMachine("bareMetalMachine", BareMetalMachineArgs.builder()        
            .bareMetalMachineName("bareMetalMachineName")
            .bmcConnectionString("bmcconnectionstring")
            .bmcCredentials(Map.ofEntries(
                Map.entry("password", "{password}"),
                Map.entry("username", "bmcuser")
            ))
            .bmcMacAddress("00:00:4f:00:57:00")
            .bootMacAddress("00:00:4e:00:58:af")
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .location("location")
            .machineDetails("User-provided machine details.")
            .machineName("r01c001")
            .machineSkuId("684E-3B16-399E")
            .rackId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName")
            .rackSlot(1)
            .resourceGroupName("resourceGroupName")
            .serialNumber("BM1219XXX")
            .tags(Map.ofEntries(
                Map.entry("key1", "myvalue1"),
                Map.entry("key2", "myvalue2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const bareMetalMachine = new azure_native.networkcloud.BareMetalMachine("bareMetalMachine", {
    bareMetalMachineName: "bareMetalMachineName",
    bmcConnectionString: "bmcconnectionstring",
    bmcCredentials: {
        password: "{password}",
        username: "bmcuser",
    },
    bmcMacAddress: "00:00:4f:00:57:00",
    bootMacAddress: "00:00:4e:00:58:af",
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type: "CustomLocation",
    },
    location: "location",
    machineDetails: "User-provided machine details.",
    machineName: "r01c001",
    machineSkuId: "684E-3B16-399E",
    rackId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName",
    rackSlot: 1,
    resourceGroupName: "resourceGroupName",
    serialNumber: "BM1219XXX",
    tags: {
        key1: "myvalue1",
        key2: "myvalue2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

bare_metal_machine = azure_native.networkcloud.BareMetalMachine("bareMetalMachine",
    bare_metal_machine_name="bareMetalMachineName",
    bmc_connection_string="bmcconnectionstring",
    bmc_credentials=azure_native.networkcloud.AdministrativeCredentialsArgs(
        password="{password}",
        username="bmcuser",
    ),
    bmc_mac_address="00:00:4f:00:57:00",
    boot_mac_address="00:00:4e:00:58:af",
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type="CustomLocation",
    ),
    location="location",
    machine_details="User-provided machine details.",
    machine_name="r01c001",
    machine_sku_id="684E-3B16-399E",
    rack_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName",
    rack_slot=1,
    resource_group_name="resourceGroupName",
    serial_number="BM1219XXX",
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    })

```

```yaml
resources:
  bareMetalMachine:
    type: azure-native:networkcloud:BareMetalMachine
    properties:
      bareMetalMachineName: bareMetalMachineName
      bmcConnectionString: bmcconnectionstring
      bmcCredentials:
        password: '{password}'
        username: bmcuser
      bmcMacAddress: 00:00:4f:00:57:00
      bootMacAddress: 00:00:4e:00:58:af
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName
        type: CustomLocation
      location: location
      machineDetails: User-provided machine details.
      machineName: r01c001
      machineSkuId: 684E-3B16-399E
      rackId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName
      rackSlot: 1
      resourceGroupName: resourceGroupName
      serialNumber: BM1219XXX
      tags:
        key1: myvalue1
        key2: myvalue2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkcloud:BareMetalMachine bareMetalMachineName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/bareMetalMachines/bareMetalMachineName 
```
