FarmBeats ARM Resource.
API Version: 2021-09-01-preview.
Previous API Version: 2020-05-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### FarmBeatsModels_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var farmBeatsModel = new AzureNative.AgFoodPlatform.FarmBeatsModel("farmBeatsModel", new()
    {
        FarmBeatsResourceName = "examples-farmbeatsResourceName",
        Location = "eastus2",
        ResourceGroupName = "examples-rg",
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
	agfoodplatform "github.com/pulumi/pulumi-azure-native-sdk/agfoodplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := agfoodplatform.NewFarmBeatsModel(ctx, "farmBeatsModel", &agfoodplatform.FarmBeatsModelArgs{
			FarmBeatsResourceName: pulumi.String("examples-farmbeatsResourceName"),
			Location:              pulumi.String("eastus2"),
			ResourceGroupName:     pulumi.String("examples-rg"),
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
import com.pulumi.azurenative.agfoodplatform.FarmBeatsModel;
import com.pulumi.azurenative.agfoodplatform.FarmBeatsModelArgs;
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
        var farmBeatsModel = new FarmBeatsModel("farmBeatsModel", FarmBeatsModelArgs.builder()        
            .farmBeatsResourceName("examples-farmbeatsResourceName")
            .location("eastus2")
            .resourceGroupName("examples-rg")
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

const farmBeatsModel = new azure_native.agfoodplatform.FarmBeatsModel("farmBeatsModel", {
    farmBeatsResourceName: "examples-farmbeatsResourceName",
    location: "eastus2",
    resourceGroupName: "examples-rg",
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

farm_beats_model = azure_native.agfoodplatform.FarmBeatsModel("farmBeatsModel",
    farm_beats_resource_name="examples-farmbeatsResourceName",
    location="eastus2",
    resource_group_name="examples-rg",
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  farmBeatsModel:
    type: azure-native:agfoodplatform:FarmBeatsModel
    properties:
      farmBeatsResourceName: examples-farmbeatsResourceName
      location: eastus2
      resourceGroupName: examples-rg
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:agfoodplatform:FarmBeatsModel examples-farmbeatsResourceName /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.AgFoodPlatform/farmBeats/examples-farmbeatsResourceName 
```
