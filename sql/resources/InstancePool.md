An Azure SQL instance pool.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create an instance pool with all properties.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var instancePool = new AzureNative.Sql.InstancePool("instancePool", new()
    {
        InstancePoolName = "testIP",
        LicenseType = "LicenseIncluded",
        Location = "japaneast",
        ResourceGroupName = "group1",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Family = "Gen5",
            Name = "GP_Gen5",
            Tier = "GeneralPurpose",
        },
        SubnetId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1",
        Tags = 
        {
            { "a", "b" },
        },
        VCores = 8,
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewInstancePool(ctx, "instancePool", &sql.InstancePoolArgs{
			InstancePoolName:  pulumi.String("testIP"),
			LicenseType:       pulumi.String("LicenseIncluded"),
			Location:          pulumi.String("japaneast"),
			ResourceGroupName: pulumi.String("group1"),
			Sku: &sql.SkuArgs{
				Family: pulumi.String("Gen5"),
				Name:   pulumi.String("GP_Gen5"),
				Tier:   pulumi.String("GeneralPurpose"),
			},
			SubnetId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1"),
			Tags: pulumi.StringMap{
				"a": pulumi.String("b"),
			},
			VCores: pulumi.Int(8),
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
import com.pulumi.azurenative.sql.InstancePool;
import com.pulumi.azurenative.sql.InstancePoolArgs;
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
        var instancePool = new InstancePool("instancePool", InstancePoolArgs.builder()        
            .instancePoolName("testIP")
            .licenseType("LicenseIncluded")
            .location("japaneast")
            .resourceGroupName("group1")
            .sku(Map.ofEntries(
                Map.entry("family", "Gen5"),
                Map.entry("name", "GP_Gen5"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .subnetId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1")
            .tags(Map.of("a", "b"))
            .vCores(8)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const instancePool = new azure_native.sql.InstancePool("instancePool", {
    instancePoolName: "testIP",
    licenseType: "LicenseIncluded",
    location: "japaneast",
    resourceGroupName: "group1",
    sku: {
        family: "Gen5",
        name: "GP_Gen5",
        tier: "GeneralPurpose",
    },
    subnetId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1",
    tags: {
        a: "b",
    },
    vCores: 8,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

instance_pool = azure_native.sql.InstancePool("instancePool",
    instance_pool_name="testIP",
    license_type="LicenseIncluded",
    location="japaneast",
    resource_group_name="group1",
    sku=azure_native.sql.SkuArgs(
        family="Gen5",
        name="GP_Gen5",
        tier="GeneralPurpose",
    ),
    subnet_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1",
    tags={
        "a": "b",
    },
    v_cores=8)

```

```yaml
resources:
  instancePool:
    type: azure-native:sql:InstancePool
    properties:
      instancePoolName: testIP
      licenseType: LicenseIncluded
      location: japaneast
      resourceGroupName: group1
      sku:
        family: Gen5
        name: GP_Gen5
        tier: GeneralPurpose
      subnetId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1
      tags:
        a: b
      vCores: 8

```

{{% /example %}}
{{% example %}}
### Create an instance pool with min properties.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var instancePool = new AzureNative.Sql.InstancePool("instancePool", new()
    {
        InstancePoolName = "testIP",
        LicenseType = "LicenseIncluded",
        Location = "japaneast",
        ResourceGroupName = "group1",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Family = "Gen5",
            Name = "GP_Gen5",
            Tier = "GeneralPurpose",
        },
        SubnetId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1",
        VCores = 8,
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewInstancePool(ctx, "instancePool", &sql.InstancePoolArgs{
			InstancePoolName:  pulumi.String("testIP"),
			LicenseType:       pulumi.String("LicenseIncluded"),
			Location:          pulumi.String("japaneast"),
			ResourceGroupName: pulumi.String("group1"),
			Sku: &sql.SkuArgs{
				Family: pulumi.String("Gen5"),
				Name:   pulumi.String("GP_Gen5"),
				Tier:   pulumi.String("GeneralPurpose"),
			},
			SubnetId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1"),
			VCores:   pulumi.Int(8),
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
import com.pulumi.azurenative.sql.InstancePool;
import com.pulumi.azurenative.sql.InstancePoolArgs;
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
        var instancePool = new InstancePool("instancePool", InstancePoolArgs.builder()        
            .instancePoolName("testIP")
            .licenseType("LicenseIncluded")
            .location("japaneast")
            .resourceGroupName("group1")
            .sku(Map.ofEntries(
                Map.entry("family", "Gen5"),
                Map.entry("name", "GP_Gen5"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .subnetId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1")
            .vCores(8)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const instancePool = new azure_native.sql.InstancePool("instancePool", {
    instancePoolName: "testIP",
    licenseType: "LicenseIncluded",
    location: "japaneast",
    resourceGroupName: "group1",
    sku: {
        family: "Gen5",
        name: "GP_Gen5",
        tier: "GeneralPurpose",
    },
    subnetId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1",
    vCores: 8,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

instance_pool = azure_native.sql.InstancePool("instancePool",
    instance_pool_name="testIP",
    license_type="LicenseIncluded",
    location="japaneast",
    resource_group_name="group1",
    sku=azure_native.sql.SkuArgs(
        family="Gen5",
        name="GP_Gen5",
        tier="GeneralPurpose",
    ),
    subnet_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1",
    v_cores=8)

```

```yaml
resources:
  instancePool:
    type: azure-native:sql:InstancePool
    properties:
      instancePoolName: testIP
      licenseType: LicenseIncluded
      location: japaneast
      resourceGroupName: group1
      sku:
        family: Gen5
        name: GP_Gen5
        tier: GeneralPurpose
      subnetId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet1
      vCores: 8

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:InstancePool testIP /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/instancePools/testIP 
```
