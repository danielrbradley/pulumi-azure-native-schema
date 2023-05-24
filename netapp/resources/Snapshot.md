Snapshot of a Volume
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Snapshots_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var snapshot = new AzureNative.NetApp.Snapshot("snapshot", new()
    {
        AccountName = "account1",
        Location = "eastus",
        PoolName = "pool1",
        ResourceGroupName = "myRG",
        SnapshotName = "snapshot1",
        VolumeName = "volume1",
    });

});


```

```go
package main

import (
	netapp "github.com/pulumi/pulumi-azure-native-sdk/netapp"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := netapp.NewSnapshot(ctx, "snapshot", &netapp.SnapshotArgs{
			AccountName:       pulumi.String("account1"),
			Location:          pulumi.String("eastus"),
			PoolName:          pulumi.String("pool1"),
			ResourceGroupName: pulumi.String("myRG"),
			SnapshotName:      pulumi.String("snapshot1"),
			VolumeName:        pulumi.String("volume1"),
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
import com.pulumi.azurenative.netapp.Snapshot;
import com.pulumi.azurenative.netapp.SnapshotArgs;
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
        var snapshot = new Snapshot("snapshot", SnapshotArgs.builder()        
            .accountName("account1")
            .location("eastus")
            .poolName("pool1")
            .resourceGroupName("myRG")
            .snapshotName("snapshot1")
            .volumeName("volume1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const snapshot = new azure_native.netapp.Snapshot("snapshot", {
    accountName: "account1",
    location: "eastus",
    poolName: "pool1",
    resourceGroupName: "myRG",
    snapshotName: "snapshot1",
    volumeName: "volume1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

snapshot = azure_native.netapp.Snapshot("snapshot",
    account_name="account1",
    location="eastus",
    pool_name="pool1",
    resource_group_name="myRG",
    snapshot_name="snapshot1",
    volume_name="volume1")

```

```yaml
resources:
  snapshot:
    type: azure-native:netapp:Snapshot
    properties:
      accountName: account1
      location: eastus
      poolName: pool1
      resourceGroupName: myRG
      snapshotName: snapshot1
      volumeName: volume1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:netapp:Snapshot account1/pool1/volume1/snapshot1 /subscriptions/D633CC2E-722B-4AE1-B636-BBD9E4C60ED9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1/volumes/volume1/snapshots/snapshot1 
```
