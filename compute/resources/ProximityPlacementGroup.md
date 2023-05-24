Specifies information about the proximity placement group.
API Version: 2022-11-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update a proximity placement group.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var proximityPlacementGroup = new AzureNative.Compute.ProximityPlacementGroup("proximityPlacementGroup", new()
    {
        Intent = new AzureNative.Compute.Inputs.ProximityPlacementGroupPropertiesIntentArgs
        {
            VmSizes = new[]
            {
                "Basic_A0",
                "Basic_A2",
            },
        },
        Location = "westus",
        ProximityPlacementGroupName = "myProximityPlacementGroup",
        ProximityPlacementGroupType = "Standard",
        ResourceGroupName = "myResourceGroup",
        Zones = new[]
        {
            "1",
        },
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewProximityPlacementGroup(ctx, "proximityPlacementGroup", &compute.ProximityPlacementGroupArgs{
			Intent: &compute.ProximityPlacementGroupPropertiesIntentArgs{
				VmSizes: pulumi.StringArray{
					pulumi.String("Basic_A0"),
					pulumi.String("Basic_A2"),
				},
			},
			Location:                    pulumi.String("westus"),
			ProximityPlacementGroupName: pulumi.String("myProximityPlacementGroup"),
			ProximityPlacementGroupType: pulumi.String("Standard"),
			ResourceGroupName:           pulumi.String("myResourceGroup"),
			Zones: pulumi.StringArray{
				pulumi.String("1"),
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
import com.pulumi.azurenative.compute.ProximityPlacementGroup;
import com.pulumi.azurenative.compute.ProximityPlacementGroupArgs;
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
        var proximityPlacementGroup = new ProximityPlacementGroup("proximityPlacementGroup", ProximityPlacementGroupArgs.builder()        
            .intent(Map.of("vmSizes",             
                "Basic_A0",
                "Basic_A2"))
            .location("westus")
            .proximityPlacementGroupName("myProximityPlacementGroup")
            .proximityPlacementGroupType("Standard")
            .resourceGroupName("myResourceGroup")
            .zones("1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const proximityPlacementGroup = new azure_native.compute.ProximityPlacementGroup("proximityPlacementGroup", {
    intent: {
        vmSizes: [
            "Basic_A0",
            "Basic_A2",
        ],
    },
    location: "westus",
    proximityPlacementGroupName: "myProximityPlacementGroup",
    proximityPlacementGroupType: "Standard",
    resourceGroupName: "myResourceGroup",
    zones: ["1"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

proximity_placement_group = azure_native.compute.ProximityPlacementGroup("proximityPlacementGroup",
    intent=azure_native.compute.ProximityPlacementGroupPropertiesIntentArgs(
        vm_sizes=[
            "Basic_A0",
            "Basic_A2",
        ],
    ),
    location="westus",
    proximity_placement_group_name="myProximityPlacementGroup",
    proximity_placement_group_type="Standard",
    resource_group_name="myResourceGroup",
    zones=["1"])

```

```yaml
resources:
  proximityPlacementGroup:
    type: azure-native:compute:ProximityPlacementGroup
    properties:
      intent:
        vmSizes:
          - Basic_A0
          - Basic_A2
      location: westus
      proximityPlacementGroupName: myProximityPlacementGroup
      proximityPlacementGroupType: Standard
      resourceGroupName: myResourceGroup
      zones:
        - '1'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:ProximityPlacementGroup myProximityPlacementGroup /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/proximityPlacementGroups/myProximityPlacementGroup 
```
