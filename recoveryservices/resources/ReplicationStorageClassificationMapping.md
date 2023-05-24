Storage mapping object.
API Version: 2023-02-01.
Previous API Version: 2018-07-10. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create storage classification mapping.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replicationStorageClassificationMapping = new AzureNative.RecoveryServices.ReplicationStorageClassificationMapping("replicationStorageClassificationMapping", new()
    {
        FabricName = "2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0",
        Properties = new AzureNative.RecoveryServices.Inputs.StorageMappingInputPropertiesArgs
        {
            TargetStorageClassificationId = "/Subscriptions/9112a37f-0f3e-46ec-9c00-060c6edca071/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0/replicationStorageClassifications/8891569e-aaef-4a46-a4a0-78c14f2d7b09",
        },
        ResourceGroupName = "resourceGroupPS1",
        ResourceName = "vault1",
        StorageClassificationMappingName = "testStorageMapping",
        StorageClassificationName = "8891569e-aaef-4a46-a4a0-78c14f2d7b09",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewReplicationStorageClassificationMapping(ctx, "replicationStorageClassificationMapping", &recoveryservices.ReplicationStorageClassificationMappingArgs{
			FabricName: pulumi.String("2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0"),
			Properties: &recoveryservices.StorageMappingInputPropertiesArgs{
				TargetStorageClassificationId: pulumi.String("/Subscriptions/9112a37f-0f3e-46ec-9c00-060c6edca071/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0/replicationStorageClassifications/8891569e-aaef-4a46-a4a0-78c14f2d7b09"),
			},
			ResourceGroupName:                pulumi.String("resourceGroupPS1"),
			ResourceName:                     pulumi.String("vault1"),
			StorageClassificationMappingName: pulumi.String("testStorageMapping"),
			StorageClassificationName:        pulumi.String("8891569e-aaef-4a46-a4a0-78c14f2d7b09"),
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
import com.pulumi.azurenative.recoveryservices.ReplicationStorageClassificationMapping;
import com.pulumi.azurenative.recoveryservices.ReplicationStorageClassificationMappingArgs;
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
        var replicationStorageClassificationMapping = new ReplicationStorageClassificationMapping("replicationStorageClassificationMapping", ReplicationStorageClassificationMappingArgs.builder()        
            .fabricName("2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0")
            .properties(Map.of("targetStorageClassificationId", "/Subscriptions/9112a37f-0f3e-46ec-9c00-060c6edca071/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0/replicationStorageClassifications/8891569e-aaef-4a46-a4a0-78c14f2d7b09"))
            .resourceGroupName("resourceGroupPS1")
            .resourceName("vault1")
            .storageClassificationMappingName("testStorageMapping")
            .storageClassificationName("8891569e-aaef-4a46-a4a0-78c14f2d7b09")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replicationStorageClassificationMapping = new azure_native.recoveryservices.ReplicationStorageClassificationMapping("replicationStorageClassificationMapping", {
    fabricName: "2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0",
    properties: {
        targetStorageClassificationId: "/Subscriptions/9112a37f-0f3e-46ec-9c00-060c6edca071/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0/replicationStorageClassifications/8891569e-aaef-4a46-a4a0-78c14f2d7b09",
    },
    resourceGroupName: "resourceGroupPS1",
    resourceName: "vault1",
    storageClassificationMappingName: "testStorageMapping",
    storageClassificationName: "8891569e-aaef-4a46-a4a0-78c14f2d7b09",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replication_storage_classification_mapping = azure_native.recoveryservices.ReplicationStorageClassificationMapping("replicationStorageClassificationMapping",
    fabric_name="2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0",
    properties=azure_native.recoveryservices.StorageMappingInputPropertiesArgs(
        target_storage_classification_id="/Subscriptions/9112a37f-0f3e-46ec-9c00-060c6edca071/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0/replicationStorageClassifications/8891569e-aaef-4a46-a4a0-78c14f2d7b09",
    ),
    resource_group_name="resourceGroupPS1",
    resource_name_="vault1",
    storage_classification_mapping_name="testStorageMapping",
    storage_classification_name="8891569e-aaef-4a46-a4a0-78c14f2d7b09")

```

```yaml
resources:
  replicationStorageClassificationMapping:
    type: azure-native:recoveryservices:ReplicationStorageClassificationMapping
    properties:
      fabricName: 2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0
      properties:
        targetStorageClassificationId: /Subscriptions/9112a37f-0f3e-46ec-9c00-060c6edca071/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0/replicationStorageClassifications/8891569e-aaef-4a46-a4a0-78c14f2d7b09
      resourceGroupName: resourceGroupPS1
      resourceName: vault1
      storageClassificationMappingName: testStorageMapping
      storageClassificationName: 8891569e-aaef-4a46-a4a0-78c14f2d7b09

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ReplicationStorageClassificationMapping testStorageMapping /Subscriptions/9112a37f-0f3e-46ec-9c00-060c6edca071/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/2a48e3770ac08aa2be8bfbd94fcfb1cbf2dcc487b78fb9d3bd778304441b06a0/replicationStorageClassifications/8891569e-aaef-4a46-a4a0-78c14f2d7b09/replicationStorageClassificationMappings/testStorageMapping 
```
