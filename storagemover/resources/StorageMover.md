The Storage Mover resource, which is a container for a group of Agents, Projects, and Endpoints.
API Version: 2023-03-01.
Previous API Version: 2022-07-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StorageMovers_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageMover = new AzureNative.StorageMover.StorageMover("storageMover", new()
    {
        Description = "Example Storage Mover Description",
        Location = "eastus2",
        ResourceGroupName = "examples-rg",
        StorageMoverName = "examples-storageMoverName",
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
    });

});


```

```go
package main

import (
	storagemover "github.com/pulumi/pulumi-azure-native-sdk/storagemover"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storagemover.NewStorageMover(ctx, "storageMover", &storagemover.StorageMoverArgs{
			Description:       pulumi.String("Example Storage Mover Description"),
			Location:          pulumi.String("eastus2"),
			ResourceGroupName: pulumi.String("examples-rg"),
			StorageMoverName:  pulumi.String("examples-storageMoverName"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
				"key2": pulumi.String("value2"),
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
import com.pulumi.azurenative.storagemover.StorageMover;
import com.pulumi.azurenative.storagemover.StorageMoverArgs;
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
        var storageMover = new StorageMover("storageMover", StorageMoverArgs.builder()        
            .description("Example Storage Mover Description")
            .location("eastus2")
            .resourceGroupName("examples-rg")
            .storageMoverName("examples-storageMoverName")
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageMover = new azure_native.storagemover.StorageMover("storageMover", {
    description: "Example Storage Mover Description",
    location: "eastus2",
    resourceGroupName: "examples-rg",
    storageMoverName: "examples-storageMoverName",
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_mover = azure_native.storagemover.StorageMover("storageMover",
    description="Example Storage Mover Description",
    location="eastus2",
    resource_group_name="examples-rg",
    storage_mover_name="examples-storageMoverName",
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  storageMover:
    type: azure-native:storagemover:StorageMover
    properties:
      description: Example Storage Mover Description
      location: eastus2
      resourceGroupName: examples-rg
      storageMoverName: examples-storageMoverName
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagemover:StorageMover examples-storageMoverName /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.StorageMover/storageMovers/examples-storageMoverName 
```
