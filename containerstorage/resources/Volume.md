Concrete proxy resource types can be created by aliasing this type using a specific property type.
API Version: 2023-03-01-preview.
Previous API Version: 2023-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Volumes_CreateOrUpdate_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volume = new AzureNative.ContainerStorage.Volume("volume", new()
    {
        CapacityGiB = 4,
        Labels = 
        {
            { "key6929", "cylq" },
        },
        MountOptions = new[]
        {
            "bztwmyruogigzqnwzpnjxjo",
        },
        PoolName = "L-7Vr5xE3",
        ReclaimPolicy = "Delete",
        ResourceGroupName = "rgcontainerstorage",
        VolumeMode = "Filesystem",
        VolumeName = "y4borPc1GHLej48W3",
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
		_, err := containerstorage.NewVolume(ctx, "volume", &containerstorage.VolumeArgs{
			CapacityGiB: pulumi.Float64(4),
			Labels: pulumi.StringMap{
				"key6929": pulumi.String("cylq"),
			},
			MountOptions: pulumi.StringArray{
				pulumi.String("bztwmyruogigzqnwzpnjxjo"),
			},
			PoolName:          pulumi.String("L-7Vr5xE3"),
			ReclaimPolicy:     pulumi.String("Delete"),
			ResourceGroupName: pulumi.String("rgcontainerstorage"),
			VolumeMode:        pulumi.String("Filesystem"),
			VolumeName:        pulumi.String("y4borPc1GHLej48W3"),
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
import com.pulumi.azurenative.containerstorage.Volume;
import com.pulumi.azurenative.containerstorage.VolumeArgs;
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
        var volume = new Volume("volume", VolumeArgs.builder()        
            .capacityGiB(4)
            .labels(Map.of("key6929", "cylq"))
            .mountOptions("bztwmyruogigzqnwzpnjxjo")
            .poolName("L-7Vr5xE3")
            .reclaimPolicy("Delete")
            .resourceGroupName("rgcontainerstorage")
            .volumeMode("Filesystem")
            .volumeName("y4borPc1GHLej48W3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volume = new azure_native.containerstorage.Volume("volume", {
    capacityGiB: 4,
    labels: {
        key6929: "cylq",
    },
    mountOptions: ["bztwmyruogigzqnwzpnjxjo"],
    poolName: "L-7Vr5xE3",
    reclaimPolicy: "Delete",
    resourceGroupName: "rgcontainerstorage",
    volumeMode: "Filesystem",
    volumeName: "y4borPc1GHLej48W3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume = azure_native.containerstorage.Volume("volume",
    capacity_gi_b=4,
    labels={
        "key6929": "cylq",
    },
    mount_options=["bztwmyruogigzqnwzpnjxjo"],
    pool_name="L-7Vr5xE3",
    reclaim_policy="Delete",
    resource_group_name="rgcontainerstorage",
    volume_mode="Filesystem",
    volume_name="y4borPc1GHLej48W3")

```

```yaml
resources:
  volume:
    type: azure-native:containerstorage:Volume
    properties:
      capacityGiB: 4
      labels:
        key6929: cylq
      mountOptions:
        - bztwmyruogigzqnwzpnjxjo
      poolName: L-7Vr5xE3
      reclaimPolicy: Delete
      resourceGroupName: rgcontainerstorage
      volumeMode: Filesystem
      volumeName: y4borPc1GHLej48W3

```

{{% /example %}}
{{% example %}}
### Volumes_CreateOrUpdate_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volume = new AzureNative.ContainerStorage.Volume("volume", new()
    {
        PoolName = "-3-0",
        ResourceGroupName = "rgcontainerstorage",
        VolumeName = "q-r6KY54UA6G5TPSTL83",
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
		_, err := containerstorage.NewVolume(ctx, "volume", &containerstorage.VolumeArgs{
			PoolName:          pulumi.String("-3-0"),
			ResourceGroupName: pulumi.String("rgcontainerstorage"),
			VolumeName:        pulumi.String("q-r6KY54UA6G5TPSTL83"),
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
import com.pulumi.azurenative.containerstorage.Volume;
import com.pulumi.azurenative.containerstorage.VolumeArgs;
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
        var volume = new Volume("volume", VolumeArgs.builder()        
            .poolName("-3-0")
            .resourceGroupName("rgcontainerstorage")
            .volumeName("q-r6KY54UA6G5TPSTL83")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volume = new azure_native.containerstorage.Volume("volume", {
    poolName: "-3-0",
    resourceGroupName: "rgcontainerstorage",
    volumeName: "q-r6KY54UA6G5TPSTL83",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume = azure_native.containerstorage.Volume("volume",
    pool_name="-3-0",
    resource_group_name="rgcontainerstorage",
    volume_name="q-r6KY54UA6G5TPSTL83")

```

```yaml
resources:
  volume:
    type: azure-native:containerstorage:Volume
    properties:
      poolName: -3-0
      resourceGroupName: rgcontainerstorage
      volumeName: q-r6KY54UA6G5TPSTL83

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerstorage:Volume qw uhsbnbojqymtspvbxzzjoepbyhgr 
```
