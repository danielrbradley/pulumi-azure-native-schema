An object that represents a container registry.
API Version: 2022-12-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RegistryCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registry = new AzureNative.ContainerRegistry.Registry("registry", new()
    {
        AdminUserEnabled = true,
        Location = "westus",
        RegistryName = "myRegistry",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.ContainerRegistry.Inputs.SkuArgs
        {
            Name = "Standard",
        },
        Tags = 
        {
            { "key", "value" },
        },
    });

});


```

```go
package main

import (
	containerregistry "github.com/pulumi/pulumi-azure-native-sdk/containerregistry"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerregistry.NewRegistry(ctx, "registry", &containerregistry.RegistryArgs{
			AdminUserEnabled:  pulumi.Bool(true),
			Location:          pulumi.String("westus"),
			RegistryName:      pulumi.String("myRegistry"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &containerregistry.SkuArgs{
				Name: pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"key": pulumi.String("value"),
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
import com.pulumi.azurenative.containerregistry.Registry;
import com.pulumi.azurenative.containerregistry.RegistryArgs;
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
        var registry = new Registry("registry", RegistryArgs.builder()        
            .adminUserEnabled(true)
            .location("westus")
            .registryName("myRegistry")
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "Standard"))
            .tags(Map.of("key", "value"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registry = new azure_native.containerregistry.Registry("registry", {
    adminUserEnabled: true,
    location: "westus",
    registryName: "myRegistry",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "Standard",
    },
    tags: {
        key: "value",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registry = azure_native.containerregistry.Registry("registry",
    admin_user_enabled=True,
    location="westus",
    registry_name="myRegistry",
    resource_group_name="myResourceGroup",
    sku=azure_native.containerregistry.SkuArgs(
        name="Standard",
    ),
    tags={
        "key": "value",
    })

```

```yaml
resources:
  registry:
    type: azure-native:containerregistry:Registry
    properties:
      adminUserEnabled: true
      location: westus
      registryName: myRegistry
      resourceGroupName: myResourceGroup
      sku:
        name: Standard
      tags:
        key: value

```

{{% /example %}}
{{% example %}}
### RegistryCreateZoneRedundant
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registry = new AzureNative.ContainerRegistry.Registry("registry", new()
    {
        Location = "westus",
        RegistryName = "myRegistry",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.ContainerRegistry.Inputs.SkuArgs
        {
            Name = "Standard",
        },
        Tags = 
        {
            { "key", "value" },
        },
        ZoneRedundancy = "Enabled",
    });

});


```

```go
package main

import (
	containerregistry "github.com/pulumi/pulumi-azure-native-sdk/containerregistry"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerregistry.NewRegistry(ctx, "registry", &containerregistry.RegistryArgs{
			Location:          pulumi.String("westus"),
			RegistryName:      pulumi.String("myRegistry"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &containerregistry.SkuArgs{
				Name: pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"key": pulumi.String("value"),
			},
			ZoneRedundancy: pulumi.String("Enabled"),
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
import com.pulumi.azurenative.containerregistry.Registry;
import com.pulumi.azurenative.containerregistry.RegistryArgs;
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
        var registry = new Registry("registry", RegistryArgs.builder()        
            .location("westus")
            .registryName("myRegistry")
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "Standard"))
            .tags(Map.of("key", "value"))
            .zoneRedundancy("Enabled")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registry = new azure_native.containerregistry.Registry("registry", {
    location: "westus",
    registryName: "myRegistry",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "Standard",
    },
    tags: {
        key: "value",
    },
    zoneRedundancy: "Enabled",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registry = azure_native.containerregistry.Registry("registry",
    location="westus",
    registry_name="myRegistry",
    resource_group_name="myResourceGroup",
    sku=azure_native.containerregistry.SkuArgs(
        name="Standard",
    ),
    tags={
        "key": "value",
    },
    zone_redundancy="Enabled")

```

```yaml
resources:
  registry:
    type: azure-native:containerregistry:Registry
    properties:
      location: westus
      registryName: myRegistry
      resourceGroupName: myResourceGroup
      sku:
        name: Standard
      tags:
        key: value
      zoneRedundancy: Enabled

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerregistry:Registry myRegistry /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.ContainerRegistry/registries/myRegistry 
```
