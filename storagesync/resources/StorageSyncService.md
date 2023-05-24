Storage Sync Service object.
API Version: 2022-06-01.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StorageSyncServices_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageSyncService = new AzureNative.StorageSync.StorageSyncService("storageSyncService", new()
    {
        IncomingTrafficPolicy = "AllowAllTraffic",
        Location = "WestUS",
        ResourceGroupName = "SampleResourceGroup_1",
        StorageSyncServiceName = "SampleStorageSyncService_1",
        Tags = null,
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
		_, err := storagesync.NewStorageSyncService(ctx, "storageSyncService", &storagesync.StorageSyncServiceArgs{
			IncomingTrafficPolicy:  pulumi.String("AllowAllTraffic"),
			Location:               pulumi.String("WestUS"),
			ResourceGroupName:      pulumi.String("SampleResourceGroup_1"),
			StorageSyncServiceName: pulumi.String("SampleStorageSyncService_1"),
			Tags:                   nil,
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
import com.pulumi.azurenative.storagesync.StorageSyncService;
import com.pulumi.azurenative.storagesync.StorageSyncServiceArgs;
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
        var storageSyncService = new StorageSyncService("storageSyncService", StorageSyncServiceArgs.builder()        
            .incomingTrafficPolicy("AllowAllTraffic")
            .location("WestUS")
            .resourceGroupName("SampleResourceGroup_1")
            .storageSyncServiceName("SampleStorageSyncService_1")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageSyncService = new azure_native.storagesync.StorageSyncService("storageSyncService", {
    incomingTrafficPolicy: "AllowAllTraffic",
    location: "WestUS",
    resourceGroupName: "SampleResourceGroup_1",
    storageSyncServiceName: "SampleStorageSyncService_1",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_sync_service = azure_native.storagesync.StorageSyncService("storageSyncService",
    incoming_traffic_policy="AllowAllTraffic",
    location="WestUS",
    resource_group_name="SampleResourceGroup_1",
    storage_sync_service_name="SampleStorageSyncService_1",
    tags={})

```

```yaml
resources:
  storageSyncService:
    type: azure-native:storagesync:StorageSyncService
    properties:
      incomingTrafficPolicy: AllowAllTraffic
      location: WestUS
      resourceGroupName: SampleResourceGroup_1
      storageSyncServiceName: SampleStorageSyncService_1
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagesync:StorageSyncService SampleStorageSyncService_1 /subscriptions/3a048283-338f-4002-a9dd-a50fdadcb392/resourceGroups/SampleResourceGroup_1/providers/Microsoft.StorageSync/storageSyncServices/SampleStorageSyncService_1 
```
