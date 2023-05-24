Concrete proxy resource types can be created by aliasing this type using a specific property type.
API Version: 2023-03-01-preview.
Previous API Version: 2023-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VolumeSnapshots_CreateOrUpdate_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volumeSnapshot = new AzureNative.ContainerStorage.VolumeSnapshot("volumeSnapshot", new()
    {
        MountOptions = new[]
        {
            "ozllffotmjyosqwx",
        },
        PoolName = "-1Jk-",
        ReclaimPolicy = "Delete",
        ResourceGroupName = "rgcontainerstorage",
        Source = "oytmtfvq",
        VolumeMode = "Filesystem",
        VolumeSnapshotName = "XBOVLQ-UDJ2n5kod886SN",
    });

});


```

```go
package main

import (
	containerstorage "github.com/pulumi/pulumi-azure-native-sdk/containerstorage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerstorage.NewVolumeSnapshot(ctx, "volumeSnapshot", &containerstorage.VolumeSnapshotArgs{
			MountOptions: pulumi.StringArray{
				pulumi.String("ozllffotmjyosqwx"),
			},
			PoolName:           pulumi.String("-1Jk-"),
			ReclaimPolicy:      pulumi.String("Delete"),
			ResourceGroupName:  pulumi.String("rgcontainerstorage"),
			Source:             pulumi.String("oytmtfvq"),
			VolumeMode:         pulumi.String("Filesystem"),
			VolumeSnapshotName: pulumi.String("XBOVLQ-UDJ2n5kod886SN"),
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
import com.pulumi.azurenative.containerstorage.VolumeSnapshot;
import com.pulumi.azurenative.containerstorage.VolumeSnapshotArgs;
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
        var volumeSnapshot = new VolumeSnapshot("volumeSnapshot", VolumeSnapshotArgs.builder()        
            .mountOptions("ozllffotmjyosqwx")
            .poolName("-1Jk-")
            .reclaimPolicy("Delete")
            .resourceGroupName("rgcontainerstorage")
            .source("oytmtfvq")
            .volumeMode("Filesystem")
            .volumeSnapshotName("XBOVLQ-UDJ2n5kod886SN")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volumeSnapshot = new azure_native.containerstorage.VolumeSnapshot("volumeSnapshot", {
    mountOptions: ["ozllffotmjyosqwx"],
    poolName: "-1Jk-",
    reclaimPolicy: "Delete",
    resourceGroupName: "rgcontainerstorage",
    source: "oytmtfvq",
    volumeMode: "Filesystem",
    volumeSnapshotName: "XBOVLQ-UDJ2n5kod886SN",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume_snapshot = azure_native.containerstorage.VolumeSnapshot("volumeSnapshot",
    mount_options=["ozllffotmjyosqwx"],
    pool_name="-1Jk-",
    reclaim_policy="Delete",
    resource_group_name="rgcontainerstorage",
    source="oytmtfvq",
    volume_mode="Filesystem",
    volume_snapshot_name="XBOVLQ-UDJ2n5kod886SN")

```

```yaml
resources:
  volumeSnapshot:
    type: azure-native:containerstorage:VolumeSnapshot
    properties:
      mountOptions:
        - ozllffotmjyosqwx
      poolName: -1Jk-
      reclaimPolicy: Delete
      resourceGroupName: rgcontainerstorage
      source: oytmtfvq
      volumeMode: Filesystem
      volumeSnapshotName: XBOVLQ-UDJ2n5kod886SN

```

{{% /example %}}
{{% example %}}
### VolumeSnapshots_CreateOrUpdate_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volumeSnapshot = new AzureNative.ContainerStorage.VolumeSnapshot("volumeSnapshot", new()
    {
        PoolName = "E-sfxFA3nN-FcID851Rq-Q3u",
        ResourceGroupName = "rgcontainerstorage",
        VolumeSnapshotName = "CjG-k-K4nWgGVV3VL-jT-5",
    });

});


```

```go
package main

import (
	containerstorage "github.com/pulumi/pulumi-azure-native-sdk/containerstorage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerstorage.NewVolumeSnapshot(ctx, "volumeSnapshot", &containerstorage.VolumeSnapshotArgs{
			PoolName:           pulumi.String("E-sfxFA3nN-FcID851Rq-Q3u"),
			ResourceGroupName:  pulumi.String("rgcontainerstorage"),
			VolumeSnapshotName: pulumi.String("CjG-k-K4nWgGVV3VL-jT-5"),
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
import com.pulumi.azurenative.containerstorage.VolumeSnapshot;
import com.pulumi.azurenative.containerstorage.VolumeSnapshotArgs;
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
        var volumeSnapshot = new VolumeSnapshot("volumeSnapshot", VolumeSnapshotArgs.builder()        
            .poolName("E-sfxFA3nN-FcID851Rq-Q3u")
            .resourceGroupName("rgcontainerstorage")
            .volumeSnapshotName("CjG-k-K4nWgGVV3VL-jT-5")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volumeSnapshot = new azure_native.containerstorage.VolumeSnapshot("volumeSnapshot", {
    poolName: "E-sfxFA3nN-FcID851Rq-Q3u",
    resourceGroupName: "rgcontainerstorage",
    volumeSnapshotName: "CjG-k-K4nWgGVV3VL-jT-5",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume_snapshot = azure_native.containerstorage.VolumeSnapshot("volumeSnapshot",
    pool_name="E-sfxFA3nN-FcID851Rq-Q3u",
    resource_group_name="rgcontainerstorage",
    volume_snapshot_name="CjG-k-K4nWgGVV3VL-jT-5")

```

```yaml
resources:
  volumeSnapshot:
    type: azure-native:containerstorage:VolumeSnapshot
    properties:
      poolName: E-sfxFA3nN-FcID851Rq-Q3u
      resourceGroupName: rgcontainerstorage
      volumeSnapshotName: CjG-k-K4nWgGVV3VL-jT-5

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerstorage:VolumeSnapshot nvn vdihfxdstmkozaxfocgt 
```
