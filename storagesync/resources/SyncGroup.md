Sync Group object.
API Version: 2022-06-01.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SyncGroups_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var syncGroup = new AzureNative.StorageSync.SyncGroup("syncGroup", new()
    {
        ResourceGroupName = "SampleResourceGroup_1",
        StorageSyncServiceName = "SampleStorageSyncService_1",
        SyncGroupName = "SampleSyncGroup_1",
    });

});


```

```go
package main

import (
	storagesync "github.com/pulumi/pulumi-azure-native-sdk/storagesync"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storagesync.NewSyncGroup(ctx, "syncGroup", &storagesync.SyncGroupArgs{
			ResourceGroupName:      pulumi.String("SampleResourceGroup_1"),
			StorageSyncServiceName: pulumi.String("SampleStorageSyncService_1"),
			SyncGroupName:          pulumi.String("SampleSyncGroup_1"),
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
import com.pulumi.azurenative.storagesync.SyncGroup;
import com.pulumi.azurenative.storagesync.SyncGroupArgs;
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
        var syncGroup = new SyncGroup("syncGroup", SyncGroupArgs.builder()        
            .resourceGroupName("SampleResourceGroup_1")
            .storageSyncServiceName("SampleStorageSyncService_1")
            .syncGroupName("SampleSyncGroup_1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const syncGroup = new azure_native.storagesync.SyncGroup("syncGroup", {
    resourceGroupName: "SampleResourceGroup_1",
    storageSyncServiceName: "SampleStorageSyncService_1",
    syncGroupName: "SampleSyncGroup_1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sync_group = azure_native.storagesync.SyncGroup("syncGroup",
    resource_group_name="SampleResourceGroup_1",
    storage_sync_service_name="SampleStorageSyncService_1",
    sync_group_name="SampleSyncGroup_1")

```

```yaml
resources:
  syncGroup:
    type: azure-native:storagesync:SyncGroup
    properties:
      resourceGroupName: SampleResourceGroup_1
      storageSyncServiceName: SampleStorageSyncService_1
      syncGroupName: SampleSyncGroup_1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagesync:SyncGroup SampleSyncGroup_1 /subscriptions/3a048283-338f-4002-a9dd-a50fdadcb392/resourceGroups/SampleResourceGroup_1/providers/Microsoft.StorageSync/storageSyncServices/SampleStorageSyncService_1/syncGroups/SampleSyncGroup_1 
```
