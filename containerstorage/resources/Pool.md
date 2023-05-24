Pool resource
API Version: 2023-03-01-preview.
Previous API Version: 2023-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Pools_CreateOrUpdate_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.ContainerStorage.Pool("pool", new()
    {
        Assignments = new[]
        {
            "qvheujgnqksryltqtkjty",
        },
        DiskPoolProperties = new AzureNative.ContainerStorage.Inputs.DiskPoolPropertiesArgs
        {
            CsiParams = 
            {
                { "key3964", "og" },
            },
            Disks = new[]
            {
                "wtsj",
            },
            MaxVolumeCapacityGiB = 11,
        },
        ElasticSanPoolProperties = new AzureNative.ContainerStorage.Inputs.ElasticSanPoolPropertiesArgs
        {
            ResourceGroup = "bjdqfuspbvlgkhsyt",
            SanName = "gu",
            VolumeGroup = "csbzebtsmcnhxzqp",
        },
        EphemeralPoolProperties = new AzureNative.ContainerStorage.Inputs.EphemeralPoolPropertiesArgs
        {
            DiskFormat = true,
            DiskSelector = new[]
            {
                "nvpe",
            },
            Disks = new[]
            {
                "zokpazvsbrjvkwhsss",
            },
        },
        Location = "jdfanwoyiigytvanvct",
        PoolCapacityGiB = 23,
        PoolName = "-EXNI2WK48",
        PoolType = 26,
        ResourceGroupName = "rgcontainerstorage",
        Tags = 
        {
            { "key5598", "fxughwwqpqkvojkkuur" },
        },
        Zones = new[]
        {
            "mzjpggkkungkugtucivmxfjnxmzdj",
        },
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
		_, err := containerstorage.NewPool(ctx, "pool", &containerstorage.PoolArgs{
			Assignments: pulumi.StringArray{
				pulumi.String("qvheujgnqksryltqtkjty"),
			},
			DiskPoolProperties: &containerstorage.DiskPoolPropertiesArgs{
				CsiParams: pulumi.StringMap{
					"key3964": pulumi.String("og"),
				},
				Disks: pulumi.StringArray{
					pulumi.String("wtsj"),
				},
				MaxVolumeCapacityGiB: pulumi.Float64(11),
			},
			ElasticSanPoolProperties: &containerstorage.ElasticSanPoolPropertiesArgs{
				ResourceGroup: pulumi.String("bjdqfuspbvlgkhsyt"),
				SanName:       pulumi.String("gu"),
				VolumeGroup:   pulumi.String("csbzebtsmcnhxzqp"),
			},
			EphemeralPoolProperties: &containerstorage.EphemeralPoolPropertiesArgs{
				DiskFormat: pulumi.Bool(true),
				DiskSelector: pulumi.StringArray{
					pulumi.String("nvpe"),
				},
				Disks: pulumi.StringArray{
					pulumi.String("zokpazvsbrjvkwhsss"),
				},
			},
			Location:          pulumi.String("jdfanwoyiigytvanvct"),
			PoolCapacityGiB:   pulumi.Float64(23),
			PoolName:          pulumi.String("-EXNI2WK48"),
			PoolType:          pulumi.Float64(26),
			ResourceGroupName: pulumi.String("rgcontainerstorage"),
			Tags: pulumi.StringMap{
				"key5598": pulumi.String("fxughwwqpqkvojkkuur"),
			},
			Zones: pulumi.StringArray{
				pulumi.String("mzjpggkkungkugtucivmxfjnxmzdj"),
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
import com.pulumi.azurenative.containerstorage.Pool;
import com.pulumi.azurenative.containerstorage.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .assignments("qvheujgnqksryltqtkjty")
            .diskPoolProperties(Map.ofEntries(
                Map.entry("csiParams", Map.of("key3964", "og")),
                Map.entry("disks", "wtsj"),
                Map.entry("maxVolumeCapacityGiB", 11)
            ))
            .elasticSanPoolProperties(Map.ofEntries(
                Map.entry("resourceGroup", "bjdqfuspbvlgkhsyt"),
                Map.entry("sanName", "gu"),
                Map.entry("volumeGroup", "csbzebtsmcnhxzqp")
            ))
            .ephemeralPoolProperties(Map.ofEntries(
                Map.entry("diskFormat", true),
                Map.entry("diskSelector", "nvpe"),
                Map.entry("disks", "zokpazvsbrjvkwhsss")
            ))
            .location("jdfanwoyiigytvanvct")
            .poolCapacityGiB(23)
            .poolName("-EXNI2WK48")
            .poolType(26)
            .resourceGroupName("rgcontainerstorage")
            .tags(Map.of("key5598", "fxughwwqpqkvojkkuur"))
            .zones("mzjpggkkungkugtucivmxfjnxmzdj")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.containerstorage.Pool("pool", {
    assignments: ["qvheujgnqksryltqtkjty"],
    diskPoolProperties: {
        csiParams: {
            key3964: "og",
        },
        disks: ["wtsj"],
        maxVolumeCapacityGiB: 11,
    },
    elasticSanPoolProperties: {
        resourceGroup: "bjdqfuspbvlgkhsyt",
        sanName: "gu",
        volumeGroup: "csbzebtsmcnhxzqp",
    },
    ephemeralPoolProperties: {
        diskFormat: true,
        diskSelector: ["nvpe"],
        disks: ["zokpazvsbrjvkwhsss"],
    },
    location: "jdfanwoyiigytvanvct",
    poolCapacityGiB: 23,
    poolName: "-EXNI2WK48",
    poolType: 26,
    resourceGroupName: "rgcontainerstorage",
    tags: {
        key5598: "fxughwwqpqkvojkkuur",
    },
    zones: ["mzjpggkkungkugtucivmxfjnxmzdj"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.containerstorage.Pool("pool",
    assignments=["qvheujgnqksryltqtkjty"],
    disk_pool_properties=azure_native.containerstorage.DiskPoolPropertiesArgs(
        csi_params={
            "key3964": "og",
        },
        disks=["wtsj"],
        max_volume_capacity_gi_b=11,
    ),
    elastic_san_pool_properties=azure_native.containerstorage.ElasticSanPoolPropertiesArgs(
        resource_group="bjdqfuspbvlgkhsyt",
        san_name="gu",
        volume_group="csbzebtsmcnhxzqp",
    ),
    ephemeral_pool_properties=azure_native.containerstorage.EphemeralPoolPropertiesArgs(
        disk_format=True,
        disk_selector=["nvpe"],
        disks=["zokpazvsbrjvkwhsss"],
    ),
    location="jdfanwoyiigytvanvct",
    pool_capacity_gi_b=23,
    pool_name="-EXNI2WK48",
    pool_type=26,
    resource_group_name="rgcontainerstorage",
    tags={
        "key5598": "fxughwwqpqkvojkkuur",
    },
    zones=["mzjpggkkungkugtucivmxfjnxmzdj"])

```

```yaml
resources:
  pool:
    type: azure-native:containerstorage:Pool
    properties:
      assignments:
        - qvheujgnqksryltqtkjty
      diskPoolProperties:
        csiParams:
          key3964: og
        disks:
          - wtsj
        maxVolumeCapacityGiB: 11
      elasticSanPoolProperties:
        resourceGroup: bjdqfuspbvlgkhsyt
        sanName: gu
        volumeGroup: csbzebtsmcnhxzqp
      ephemeralPoolProperties:
        diskFormat: true
        diskSelector:
          - nvpe
        disks:
          - zokpazvsbrjvkwhsss
      location: jdfanwoyiigytvanvct
      poolCapacityGiB: 23
      poolName: -EXNI2WK48
      poolType: 26
      resourceGroupName: rgcontainerstorage
      tags:
        key5598: fxughwwqpqkvojkkuur
      zones:
        - mzjpggkkungkugtucivmxfjnxmzdj

```

{{% /example %}}
{{% example %}}
### Pools_CreateOrUpdate_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.ContainerStorage.Pool("pool", new()
    {
        Location = "jdfanwoyiigytvanvct",
        PoolName = "J873cXX1w3sIX",
        ResourceGroupName = "rgcontainerstorage",
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
		_, err := containerstorage.NewPool(ctx, "pool", &containerstorage.PoolArgs{
			Location:          pulumi.String("jdfanwoyiigytvanvct"),
			PoolName:          pulumi.String("J873cXX1w3sIX"),
			ResourceGroupName: pulumi.String("rgcontainerstorage"),
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
import com.pulumi.azurenative.containerstorage.Pool;
import com.pulumi.azurenative.containerstorage.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .location("jdfanwoyiigytvanvct")
            .poolName("J873cXX1w3sIX")
            .resourceGroupName("rgcontainerstorage")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.containerstorage.Pool("pool", {
    location: "jdfanwoyiigytvanvct",
    poolName: "J873cXX1w3sIX",
    resourceGroupName: "rgcontainerstorage",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.containerstorage.Pool("pool",
    location="jdfanwoyiigytvanvct",
    pool_name="J873cXX1w3sIX",
    resource_group_name="rgcontainerstorage")

```

```yaml
resources:
  pool:
    type: azure-native:containerstorage:Pool
    properties:
      location: jdfanwoyiigytvanvct
      poolName: J873cXX1w3sIX
      resourceGroupName: rgcontainerstorage

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerstorage:Pool rgzqqcqrypwtqhgnvcdilsbquamov a 
```
