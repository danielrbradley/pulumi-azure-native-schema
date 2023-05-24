An Azure resource which represents Maps Creator product and provides ability to manage private location data.
API Version: 2021-02-01.
Previous API Version: 2020-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Creator Resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var creator = new AzureNative.Maps.Creator("creator", new()
    {
        AccountName = "myMapsAccount",
        CreatorName = "myCreator",
        Location = "eastus2",
        Properties = new AzureNative.Maps.Inputs.CreatorPropertiesArgs
        {
            StorageUnits = 5,
        },
        ResourceGroupName = "myResourceGroup",
        Tags = 
        {
            { "test", "true" },
        },
    });

});


```

```go
package main

import (
	maps "github.com/pulumi/pulumi-azure-native-sdk/maps"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := maps.NewCreator(ctx, "creator", &maps.CreatorArgs{
			AccountName: pulumi.String("myMapsAccount"),
			CreatorName: pulumi.String("myCreator"),
			Location:    pulumi.String("eastus2"),
			Properties: &maps.CreatorPropertiesArgs{
				StorageUnits: pulumi.Int(5),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Tags: pulumi.StringMap{
				"test": pulumi.String("true"),
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
import com.pulumi.azurenative.maps.Creator;
import com.pulumi.azurenative.maps.CreatorArgs;
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
        var creator = new Creator("creator", CreatorArgs.builder()        
            .accountName("myMapsAccount")
            .creatorName("myCreator")
            .location("eastus2")
            .properties(Map.of("storageUnits", 5))
            .resourceGroupName("myResourceGroup")
            .tags(Map.of("test", "true"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const creator = new azure_native.maps.Creator("creator", {
    accountName: "myMapsAccount",
    creatorName: "myCreator",
    location: "eastus2",
    properties: {
        storageUnits: 5,
    },
    resourceGroupName: "myResourceGroup",
    tags: {
        test: "true",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

creator = azure_native.maps.Creator("creator",
    account_name="myMapsAccount",
    creator_name="myCreator",
    location="eastus2",
    properties=azure_native.maps.CreatorPropertiesArgs(
        storage_units=5,
    ),
    resource_group_name="myResourceGroup",
    tags={
        "test": "true",
    })

```

```yaml
resources:
  creator:
    type: azure-native:maps:Creator
    properties:
      accountName: myMapsAccount
      creatorName: myCreator
      location: eastus2
      properties:
        storageUnits: 5
      resourceGroupName: myResourceGroup
      tags:
        test: 'true'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:maps:Creator myCreator /subscriptions/21a9967a-e8a9-4656-a70b-96ff1c4d05a0/resourceGroups/myResourceGroup/providers/Microsoft.Maps/accounts/myMapsAccount/creators/myCreator 
```
