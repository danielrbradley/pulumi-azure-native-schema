Base class for container with backup items. Containers with specific workloads are derived from this class.
API Version: 2023-02-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RegisterAzure Storage ProtectionContainers
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var protectionContainer = new AzureNative.RecoveryServices.ProtectionContainer("protectionContainer", new()
    {
        ContainerName = "StorageContainer;Storage;SwaggerTestRg;swaggertestsa",
        FabricName = "Azure",
        Properties = new AzureNative.RecoveryServices.Inputs.AzureStorageContainerArgs
        {
            AcquireStorageAccountLock = "Acquire",
            BackupManagementType = "AzureStorage",
            ContainerType = "StorageContainer",
            FriendlyName = "swaggertestsa",
            SourceResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/SwaggerTestRg/providers/Microsoft.Storage/storageAccounts/swaggertestsa",
        },
        ResourceGroupName = "SwaggerTestRg",
        VaultName = "swaggertestvault",
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
		_, err := recoveryservices.NewProtectionContainer(ctx, "protectionContainer", &recoveryservices.ProtectionContainerArgs{
			ContainerName: pulumi.String("StorageContainer;Storage;SwaggerTestRg;swaggertestsa"),
			FabricName:    pulumi.String("Azure"),
			Properties: recoveryservices.AzureStorageContainer{
				AcquireStorageAccountLock: "Acquire",
				BackupManagementType:      "AzureStorage",
				ContainerType:             "StorageContainer",
				FriendlyName:              "swaggertestsa",
				SourceResourceId:          "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/SwaggerTestRg/providers/Microsoft.Storage/storageAccounts/swaggertestsa",
			},
			ResourceGroupName: pulumi.String("SwaggerTestRg"),
			VaultName:         pulumi.String("swaggertestvault"),
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
import com.pulumi.azurenative.recoveryservices.ProtectionContainer;
import com.pulumi.azurenative.recoveryservices.ProtectionContainerArgs;
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
        var protectionContainer = new ProtectionContainer("protectionContainer", ProtectionContainerArgs.builder()        
            .containerName("StorageContainer;Storage;SwaggerTestRg;swaggertestsa")
            .fabricName("Azure")
            .properties(Map.ofEntries(
                Map.entry("acquireStorageAccountLock", "Acquire"),
                Map.entry("backupManagementType", "AzureStorage"),
                Map.entry("containerType", "StorageContainer"),
                Map.entry("friendlyName", "swaggertestsa"),
                Map.entry("sourceResourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/SwaggerTestRg/providers/Microsoft.Storage/storageAccounts/swaggertestsa")
            ))
            .resourceGroupName("SwaggerTestRg")
            .vaultName("swaggertestvault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const protectionContainer = new azure_native.recoveryservices.ProtectionContainer("protectionContainer", {
    containerName: "StorageContainer;Storage;SwaggerTestRg;swaggertestsa",
    fabricName: "Azure",
    properties: {
        acquireStorageAccountLock: "Acquire",
        backupManagementType: "AzureStorage",
        containerType: "StorageContainer",
        friendlyName: "swaggertestsa",
        sourceResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/SwaggerTestRg/providers/Microsoft.Storage/storageAccounts/swaggertestsa",
    },
    resourceGroupName: "SwaggerTestRg",
    vaultName: "swaggertestvault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

protection_container = azure_native.recoveryservices.ProtectionContainer("protectionContainer",
    container_name="StorageContainer;Storage;SwaggerTestRg;swaggertestsa",
    fabric_name="Azure",
    properties=azure_native.recoveryservices.AzureStorageContainerArgs(
        acquire_storage_account_lock="Acquire",
        backup_management_type="AzureStorage",
        container_type="StorageContainer",
        friendly_name="swaggertestsa",
        source_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/SwaggerTestRg/providers/Microsoft.Storage/storageAccounts/swaggertestsa",
    ),
    resource_group_name="SwaggerTestRg",
    vault_name="swaggertestvault")

```

```yaml
resources:
  protectionContainer:
    type: azure-native:recoveryservices:ProtectionContainer
    properties:
      containerName: StorageContainer;Storage;SwaggerTestRg;swaggertestsa
      fabricName: Azure
      properties:
        acquireStorageAccountLock: Acquire
        backupManagementType: AzureStorage
        containerType: StorageContainer
        friendlyName: swaggertestsa
        sourceResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/SwaggerTestRg/providers/Microsoft.Storage/storageAccounts/swaggertestsa
      resourceGroupName: SwaggerTestRg
      vaultName: swaggertestvault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ProtectionContainer StorageContainer;Storage;SwaggerTestRg;swaggertestsa /Subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/SwaggerTestRg/providers/Microsoft.RecoveryServices/vaults/swaggertestvault/backupFabrics/Azure/protectionContainers/StorageContainer;Storage;SwaggerTestRg;swaggertestsa 
```
