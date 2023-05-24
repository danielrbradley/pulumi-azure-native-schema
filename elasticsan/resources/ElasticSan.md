Response for ElasticSan request.
API Version: 2021-11-20-preview.
Previous API Version: 2021-11-20-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ElasticSans_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var elasticSan = new AzureNative.ElasticSan.ElasticSan("elasticSan", new()
    {
        AvailabilityZones = new[]
        {
            "aaaaaaaaaaaaaaaaa",
        },
        BaseSizeTiB = 26,
        ElasticSanName = "ti7q-k952-1qB3J_5",
        ExtendedCapacitySizeTiB = 7,
        Location = "aaaaaaaaaaaaaaaaaaaaaaaaaaa",
        ResourceGroupName = "rgelasticsan",
        Sku = new AzureNative.ElasticSan.Inputs.SkuArgs
        {
            Name = "Premium_LRS",
            Tier = "Premium",
        },
        Tags = 
        {
            { "key896", "aaaaaaaaaaaaaaaaaa" },
        },
    });

});


```

```go
package main

import (
	elasticsan "github.com/pulumi/pulumi-azure-native-sdk/elasticsan"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := elasticsan.NewElasticSan(ctx, "elasticSan", &elasticsan.ElasticSanArgs{
			AvailabilityZones: pulumi.StringArray{
				pulumi.String("aaaaaaaaaaaaaaaaa"),
			},
			BaseSizeTiB:             pulumi.Float64(26),
			ElasticSanName:          pulumi.String("ti7q-k952-1qB3J_5"),
			ExtendedCapacitySizeTiB: pulumi.Float64(7),
			Location:                pulumi.String("aaaaaaaaaaaaaaaaaaaaaaaaaaa"),
			ResourceGroupName:       pulumi.String("rgelasticsan"),
			Sku: &elasticsan.SkuArgs{
				Name: pulumi.String("Premium_LRS"),
				Tier: pulumi.String("Premium"),
			},
			Tags: pulumi.StringMap{
				"key896": pulumi.String("aaaaaaaaaaaaaaaaaa"),
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
import com.pulumi.azurenative.elasticsan.ElasticSan;
import com.pulumi.azurenative.elasticsan.ElasticSanArgs;
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
        var elasticSan = new ElasticSan("elasticSan", ElasticSanArgs.builder()        
            .availabilityZones("aaaaaaaaaaaaaaaaa")
            .baseSizeTiB(26)
            .elasticSanName("ti7q-k952-1qB3J_5")
            .extendedCapacitySizeTiB(7)
            .location("aaaaaaaaaaaaaaaaaaaaaaaaaaa")
            .resourceGroupName("rgelasticsan")
            .sku(Map.ofEntries(
                Map.entry("name", "Premium_LRS"),
                Map.entry("tier", "Premium")
            ))
            .tags(Map.of("key896", "aaaaaaaaaaaaaaaaaa"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const elasticSan = new azure_native.elasticsan.ElasticSan("elasticSan", {
    availabilityZones: ["aaaaaaaaaaaaaaaaa"],
    baseSizeTiB: 26,
    elasticSanName: "ti7q-k952-1qB3J_5",
    extendedCapacitySizeTiB: 7,
    location: "aaaaaaaaaaaaaaaaaaaaaaaaaaa",
    resourceGroupName: "rgelasticsan",
    sku: {
        name: "Premium_LRS",
        tier: "Premium",
    },
    tags: {
        key896: "aaaaaaaaaaaaaaaaaa",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

elastic_san = azure_native.elasticsan.ElasticSan("elasticSan",
    availability_zones=["aaaaaaaaaaaaaaaaa"],
    base_size_ti_b=26,
    elastic_san_name="ti7q-k952-1qB3J_5",
    extended_capacity_size_ti_b=7,
    location="aaaaaaaaaaaaaaaaaaaaaaaaaaa",
    resource_group_name="rgelasticsan",
    sku=azure_native.elasticsan.SkuArgs(
        name="Premium_LRS",
        tier="Premium",
    ),
    tags={
        "key896": "aaaaaaaaaaaaaaaaaa",
    })

```

```yaml
resources:
  elasticSan:
    type: azure-native:elasticsan:ElasticSan
    properties:
      availabilityZones:
        - aaaaaaaaaaaaaaaaa
      baseSizeTiB: 26
      elasticSanName: ti7q-k952-1qB3J_5
      extendedCapacitySizeTiB: 7
      location: aaaaaaaaaaaaaaaaaaaaaaaaaaa
      resourceGroupName: rgelasticsan
      sku:
        name: Premium_LRS
        tier: Premium
      tags:
        key896: aaaaaaaaaaaaaaaaaa

```

{{% /example %}}
{{% example %}}
### ElasticSans_Create_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var elasticSan = new AzureNative.ElasticSan.ElasticSan("elasticSan", new()
    {
        BaseSizeTiB = 26,
        ElasticSanName = "ti7q-k952-1qB3J_5",
        ExtendedCapacitySizeTiB = 7,
        ResourceGroupName = "rgelasticsan",
        Sku = new AzureNative.ElasticSan.Inputs.SkuArgs
        {
            Name = "Premium_LRS",
        },
    });

});


```

```go
package main

import (
	elasticsan "github.com/pulumi/pulumi-azure-native-sdk/elasticsan"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := elasticsan.NewElasticSan(ctx, "elasticSan", &elasticsan.ElasticSanArgs{
			BaseSizeTiB:             pulumi.Float64(26),
			ElasticSanName:          pulumi.String("ti7q-k952-1qB3J_5"),
			ExtendedCapacitySizeTiB: pulumi.Float64(7),
			ResourceGroupName:       pulumi.String("rgelasticsan"),
			Sku: &elasticsan.SkuArgs{
				Name: pulumi.String("Premium_LRS"),
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
import com.pulumi.azurenative.elasticsan.ElasticSan;
import com.pulumi.azurenative.elasticsan.ElasticSanArgs;
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
        var elasticSan = new ElasticSan("elasticSan", ElasticSanArgs.builder()        
            .baseSizeTiB(26)
            .elasticSanName("ti7q-k952-1qB3J_5")
            .extendedCapacitySizeTiB(7)
            .resourceGroupName("rgelasticsan")
            .sku(Map.of("name", "Premium_LRS"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const elasticSan = new azure_native.elasticsan.ElasticSan("elasticSan", {
    baseSizeTiB: 26,
    elasticSanName: "ti7q-k952-1qB3J_5",
    extendedCapacitySizeTiB: 7,
    resourceGroupName: "rgelasticsan",
    sku: {
        name: "Premium_LRS",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

elastic_san = azure_native.elasticsan.ElasticSan("elasticSan",
    base_size_ti_b=26,
    elastic_san_name="ti7q-k952-1qB3J_5",
    extended_capacity_size_ti_b=7,
    resource_group_name="rgelasticsan",
    sku=azure_native.elasticsan.SkuArgs(
        name="Premium_LRS",
    ))

```

```yaml
resources:
  elasticSan:
    type: azure-native:elasticsan:ElasticSan
    properties:
      baseSizeTiB: 26
      elasticSanName: ti7q-k952-1qB3J_5
      extendedCapacitySizeTiB: 7
      resourceGroupName: rgelasticsan
      sku:
        name: Premium_LRS

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:elasticsan:ElasticSan aaaaaaaaaaa aaaaaaaaaaaaaaaaaaaaaaaaaaaaa 
```
