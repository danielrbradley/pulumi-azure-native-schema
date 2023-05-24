The storageSpaces resource definition.
API Version: 2022-09-01-preview.
Previous API Version: 2022-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutStorageSpace
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageSpaceRetrieve = new AzureNative.HybridContainerService.StorageSpaceRetrieve("storageSpaceRetrieve", new()
    {
        ExtendedLocation = new AzureNative.HybridContainerService.Inputs.StorageSpacesExtendedLocationArgs
        {
            Name = "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation",
            Type = "CustomLocation",
        },
        Location = "westus",
        Properties = new AzureNative.HybridContainerService.Inputs.StorageSpacesPropertiesArgs
        {
            HciStorageProfile = new AzureNative.HybridContainerService.Inputs.StorageSpacesPropertiesHciStorageProfileArgs
            {
                MocGroup = "target-group",
                MocLocation = "MocLocation",
                MocStorageContainer = "WssdStorageContainer",
            },
        },
        ResourceGroupName = "test-arcappliance-resgrp",
        StorageSpacesName = "test-storage",
    });

});


```

```go
package main

import (
	hybridcontainerservice "github.com/pulumi/pulumi-azure-native-sdk/hybridcontainerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridcontainerservice.NewStorageSpaceRetrieve(ctx, "storageSpaceRetrieve", &hybridcontainerservice.StorageSpaceRetrieveArgs{
			ExtendedLocation: &hybridcontainerservice.StorageSpacesExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation"),
				Type: pulumi.String("CustomLocation"),
			},
			Location: pulumi.String("westus"),
			Properties: hybridcontainerservice.StorageSpacesPropertiesResponse{
				HciStorageProfile: &hybridcontainerservice.StorageSpacesPropertiesHciStorageProfileArgs{
					MocGroup:            pulumi.String("target-group"),
					MocLocation:         pulumi.String("MocLocation"),
					MocStorageContainer: pulumi.String("WssdStorageContainer"),
				},
			},
			ResourceGroupName: pulumi.String("test-arcappliance-resgrp"),
			StorageSpacesName: pulumi.String("test-storage"),
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
import com.pulumi.azurenative.hybridcontainerservice.StorageSpaceRetrieve;
import com.pulumi.azurenative.hybridcontainerservice.StorageSpaceRetrieveArgs;
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
        var storageSpaceRetrieve = new StorageSpaceRetrieve("storageSpaceRetrieve", StorageSpaceRetrieveArgs.builder()        
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation"),
                Map.entry("type", "CustomLocation")
            ))
            .location("westus")
            .properties(Map.of("hciStorageProfile", Map.ofEntries(
                Map.entry("mocGroup", "target-group"),
                Map.entry("mocLocation", "MocLocation"),
                Map.entry("mocStorageContainer", "WssdStorageContainer")
            )))
            .resourceGroupName("test-arcappliance-resgrp")
            .storageSpacesName("test-storage")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageSpaceRetrieve = new azure_native.hybridcontainerservice.StorageSpaceRetrieve("storageSpaceRetrieve", {
    extendedLocation: {
        name: "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation",
        type: "CustomLocation",
    },
    location: "westus",
    properties: {
        hciStorageProfile: {
            mocGroup: "target-group",
            mocLocation: "MocLocation",
            mocStorageContainer: "WssdStorageContainer",
        },
    },
    resourceGroupName: "test-arcappliance-resgrp",
    storageSpacesName: "test-storage",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_space_retrieve = azure_native.hybridcontainerservice.StorageSpaceRetrieve("storageSpaceRetrieve",
    extended_location=azure_native.hybridcontainerservice.StorageSpacesExtendedLocationArgs(
        name="/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation",
        type="CustomLocation",
    ),
    location="westus",
    properties=azure_native.hybridcontainerservice.StorageSpacesPropertiesResponseArgs(
        hci_storage_profile=azure_native.hybridcontainerservice.StorageSpacesPropertiesHciStorageProfileArgs(
            moc_group="target-group",
            moc_location="MocLocation",
            moc_storage_container="WssdStorageContainer",
        ),
    ),
    resource_group_name="test-arcappliance-resgrp",
    storage_spaces_name="test-storage")

```

```yaml
resources:
  storageSpaceRetrieve:
    type: azure-native:hybridcontainerservice:StorageSpaceRetrieve
    properties:
      extendedLocation:
        name: /subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation
        type: CustomLocation
      location: westus
      properties:
        hciStorageProfile:
          mocGroup: target-group
          mocLocation: MocLocation
          mocStorageContainer: WssdStorageContainer
      resourceGroupName: test-arcappliance-resgrp
      storageSpacesName: test-storage

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridcontainerservice:StorageSpaceRetrieve test-storage /subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/storageSpaces/test-storage 
```
