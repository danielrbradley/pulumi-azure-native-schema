An object that represents a replication for a container registry.
API Version: 2022-12-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ReplicationCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replication = new AzureNative.ContainerRegistry.Replication("replication", new()
    {
        Location = "eastus",
        RegistryName = "myRegistry",
        ReplicationName = "myReplication",
        ResourceGroupName = "myResourceGroup",
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
		_, err := containerregistry.NewReplication(ctx, "replication", &containerregistry.ReplicationArgs{
			Location:          pulumi.String("eastus"),
			RegistryName:      pulumi.String("myRegistry"),
			ReplicationName:   pulumi.String("myReplication"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.containerregistry.Replication;
import com.pulumi.azurenative.containerregistry.ReplicationArgs;
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
        var replication = new Replication("replication", ReplicationArgs.builder()        
            .location("eastus")
            .registryName("myRegistry")
            .replicationName("myReplication")
            .resourceGroupName("myResourceGroup")
            .tags(Map.of("key", "value"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replication = new azure_native.containerregistry.Replication("replication", {
    location: "eastus",
    registryName: "myRegistry",
    replicationName: "myReplication",
    resourceGroupName: "myResourceGroup",
    tags: {
        key: "value",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replication = azure_native.containerregistry.Replication("replication",
    location="eastus",
    registry_name="myRegistry",
    replication_name="myReplication",
    resource_group_name="myResourceGroup",
    tags={
        "key": "value",
    })

```

```yaml
resources:
  replication:
    type: azure-native:containerregistry:Replication
    properties:
      location: eastus
      registryName: myRegistry
      replicationName: myReplication
      resourceGroupName: myResourceGroup
      tags:
        key: value

```

{{% /example %}}
{{% example %}}
### ReplicationCreateZoneRedundant
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replication = new AzureNative.ContainerRegistry.Replication("replication", new()
    {
        Location = "eastus",
        RegionEndpointEnabled = true,
        RegistryName = "myRegistry",
        ReplicationName = "myReplication",
        ResourceGroupName = "myResourceGroup",
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
		_, err := containerregistry.NewReplication(ctx, "replication", &containerregistry.ReplicationArgs{
			Location:              pulumi.String("eastus"),
			RegionEndpointEnabled: pulumi.Bool(true),
			RegistryName:          pulumi.String("myRegistry"),
			ReplicationName:       pulumi.String("myReplication"),
			ResourceGroupName:     pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.containerregistry.Replication;
import com.pulumi.azurenative.containerregistry.ReplicationArgs;
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
        var replication = new Replication("replication", ReplicationArgs.builder()        
            .location("eastus")
            .regionEndpointEnabled(true)
            .registryName("myRegistry")
            .replicationName("myReplication")
            .resourceGroupName("myResourceGroup")
            .tags(Map.of("key", "value"))
            .zoneRedundancy("Enabled")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replication = new azure_native.containerregistry.Replication("replication", {
    location: "eastus",
    regionEndpointEnabled: true,
    registryName: "myRegistry",
    replicationName: "myReplication",
    resourceGroupName: "myResourceGroup",
    tags: {
        key: "value",
    },
    zoneRedundancy: "Enabled",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replication = azure_native.containerregistry.Replication("replication",
    location="eastus",
    region_endpoint_enabled=True,
    registry_name="myRegistry",
    replication_name="myReplication",
    resource_group_name="myResourceGroup",
    tags={
        "key": "value",
    },
    zone_redundancy="Enabled")

```

```yaml
resources:
  replication:
    type: azure-native:containerregistry:Replication
    properties:
      location: eastus
      regionEndpointEnabled: true
      registryName: myRegistry
      replicationName: myReplication
      resourceGroupName: myResourceGroup
      tags:
        key: value
      zoneRedundancy: Enabled

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerregistry:Replication myReplication /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.ContainerRegistry/registries/myRegistry/replications/myReplication 
```
