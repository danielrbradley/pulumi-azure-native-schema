Define the move collection.
API Version: 2022-08-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### MoveCollections_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var moveCollection = new AzureNative.Migrate.MoveCollection("moveCollection", new()
    {
        Identity = new AzureNative.Migrate.Inputs.IdentityArgs
        {
            Type = "SystemAssigned",
        },
        Location = "eastus2",
        MoveCollectionName = "movecollection1",
        Properties = new AzureNative.Migrate.Inputs.MoveCollectionPropertiesArgs
        {
            SourceRegion = "eastus",
            TargetRegion = "westus",
        },
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	migrate "github.com/pulumi/pulumi-azure-native-sdk/migrate"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := migrate.NewMoveCollection(ctx, "moveCollection", &migrate.MoveCollectionArgs{
			Identity: &migrate.IdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Location:           pulumi.String("eastus2"),
			MoveCollectionName: pulumi.String("movecollection1"),
			Properties: &migrate.MoveCollectionPropertiesArgs{
				SourceRegion: pulumi.String("eastus"),
				TargetRegion: pulumi.String("westus"),
			},
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.migrate.MoveCollection;
import com.pulumi.azurenative.migrate.MoveCollectionArgs;
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
        var moveCollection = new MoveCollection("moveCollection", MoveCollectionArgs.builder()        
            .identity(Map.of("type", "SystemAssigned"))
            .location("eastus2")
            .moveCollectionName("movecollection1")
            .properties(Map.ofEntries(
                Map.entry("sourceRegion", "eastus"),
                Map.entry("targetRegion", "westus")
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const moveCollection = new azure_native.migrate.MoveCollection("moveCollection", {
    identity: {
        type: "SystemAssigned",
    },
    location: "eastus2",
    moveCollectionName: "movecollection1",
    properties: {
        sourceRegion: "eastus",
        targetRegion: "westus",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

move_collection = azure_native.migrate.MoveCollection("moveCollection",
    identity=azure_native.migrate.IdentityArgs(
        type="SystemAssigned",
    ),
    location="eastus2",
    move_collection_name="movecollection1",
    properties=azure_native.migrate.MoveCollectionPropertiesArgs(
        source_region="eastus",
        target_region="westus",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  moveCollection:
    type: azure-native:migrate:MoveCollection
    properties:
      identity:
        type: SystemAssigned
      location: eastus2
      moveCollectionName: movecollection1
      properties:
        sourceRegion: eastus
        targetRegion: westus
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:MoveCollection movecollection1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Migrate/MoveCollections/movecollection1 
```
