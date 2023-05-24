
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update storage appliance
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageAppliance = new AzureNative.NetworkCloud.StorageAppliance("storageAppliance", new()
    {
        AdministratorCredentials = new AzureNative.NetworkCloud.Inputs.AdministrativeCredentialsArgs
        {
            Password = "{password}",
            Username = "adminUser",
        },
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
            Type = "CustomLocation",
        },
        Location = "location",
        RackId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName",
        RackSlot = 1,
        ResourceGroupName = "resourceGroupName",
        SerialNumber = "BM1219XXX",
        StorageApplianceName = "storageApplianceName",
        StorageApplianceSkuId = "684E-3B16-399E",
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
		_, err := networkcloud.NewStorageAppliance(ctx, "storageAppliance", &networkcloud.StorageApplianceArgs{
			AdministratorCredentials: &networkcloud.AdministrativeCredentialsArgs{
				Password: pulumi.String("{password}"),
				Username: pulumi.String("adminUser"),
			},
			ExtendedLocation: &networkcloud.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
				Type: pulumi.String("CustomLocation"),
			},
			Location:              pulumi.String("location"),
			RackId:                pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName"),
			RackSlot:              pulumi.Float64(1),
			ResourceGroupName:     pulumi.String("resourceGroupName"),
			SerialNumber:          pulumi.String("BM1219XXX"),
			StorageApplianceName:  pulumi.String("storageApplianceName"),
			StorageApplianceSkuId: pulumi.String("684E-3B16-399E"),
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
import com.pulumi.azurenative.networkcloud.StorageAppliance;
import com.pulumi.azurenative.networkcloud.StorageApplianceArgs;
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
        var storageAppliance = new StorageAppliance("storageAppliance", StorageApplianceArgs.builder()        
            .administratorCredentials(Map.ofEntries(
                Map.entry("password", "{password}"),
                Map.entry("username", "adminUser")
            ))
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .location("location")
            .rackId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName")
            .rackSlot(1)
            .resourceGroupName("resourceGroupName")
            .serialNumber("BM1219XXX")
            .storageApplianceName("storageApplianceName")
            .storageApplianceSkuId("684E-3B16-399E")
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

const storageAppliance = new azure_native.networkcloud.StorageAppliance("storageAppliance", {
    administratorCredentials: {
        password: "{password}",
        username: "adminUser",
    },
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type: "CustomLocation",
    },
    location: "location",
    rackId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName",
    rackSlot: 1,
    resourceGroupName: "resourceGroupName",
    serialNumber: "BM1219XXX",
    storageApplianceName: "storageApplianceName",
    storageApplianceSkuId: "684E-3B16-399E",
    tags: {
        key1: "myvalue1",
        key2: "myvalue2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_appliance = azure_native.networkcloud.StorageAppliance("storageAppliance",
    administrator_credentials=azure_native.networkcloud.AdministrativeCredentialsArgs(
        password="{password}",
        username="adminUser",
    ),
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type="CustomLocation",
    ),
    location="location",
    rack_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName",
    rack_slot=1,
    resource_group_name="resourceGroupName",
    serial_number="BM1219XXX",
    storage_appliance_name="storageApplianceName",
    storage_appliance_sku_id="684E-3B16-399E",
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    })

```

```yaml
resources:
  storageAppliance:
    type: azure-native:networkcloud:StorageAppliance
    properties:
      administratorCredentials:
        password: '{password}'
        username: adminUser
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName
        type: CustomLocation
      location: location
      rackId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName
      rackSlot: 1
      resourceGroupName: resourceGroupName
      serialNumber: BM1219XXX
      storageApplianceName: storageApplianceName
      storageApplianceSkuId: 684E-3B16-399E
      tags:
        key1: myvalue1
        key2: myvalue2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkcloud:StorageAppliance storageApplianceName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/storageAppliances/storageApplianceName 
```
