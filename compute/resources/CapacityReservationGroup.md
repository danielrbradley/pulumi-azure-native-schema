Specifies information about the capacity reservation group that the capacity reservations should be assigned to. <br><br> Currently, a capacity reservation can only be added to a capacity reservation group at creation time. An existing capacity reservation cannot be added or moved to another capacity reservation group.
API Version: 2022-11-01.
Previous API Version: 2021-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a capacity reservation group.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var capacityReservationGroup = new AzureNative.Compute.CapacityReservationGroup("capacityReservationGroup", new()
    {
        CapacityReservationGroupName = "myCapacityReservationGroup",
        Location = "westus",
        ResourceGroupName = "myResourceGroup",
        Tags = 
        {
            { "department", "finance" },
        },
        Zones = new[]
        {
            "1",
            "2",
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
		_, err := compute.NewCapacityReservationGroup(ctx, "capacityReservationGroup", &compute.CapacityReservationGroupArgs{
			CapacityReservationGroupName: pulumi.String("myCapacityReservationGroup"),
			Location:                     pulumi.String("westus"),
			ResourceGroupName:            pulumi.String("myResourceGroup"),
			Tags: pulumi.StringMap{
				"department": pulumi.String("finance"),
			},
			Zones: pulumi.StringArray{
				pulumi.String("1"),
				pulumi.String("2"),
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
import com.pulumi.azurenative.compute.CapacityReservationGroup;
import com.pulumi.azurenative.compute.CapacityReservationGroupArgs;
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
        var capacityReservationGroup = new CapacityReservationGroup("capacityReservationGroup", CapacityReservationGroupArgs.builder()        
            .capacityReservationGroupName("myCapacityReservationGroup")
            .location("westus")
            .resourceGroupName("myResourceGroup")
            .tags(Map.of("department", "finance"))
            .zones(            
                "1",
                "2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const capacityReservationGroup = new azure_native.compute.CapacityReservationGroup("capacityReservationGroup", {
    capacityReservationGroupName: "myCapacityReservationGroup",
    location: "westus",
    resourceGroupName: "myResourceGroup",
    tags: {
        department: "finance",
    },
    zones: [
        "1",
        "2",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

capacity_reservation_group = azure_native.compute.CapacityReservationGroup("capacityReservationGroup",
    capacity_reservation_group_name="myCapacityReservationGroup",
    location="westus",
    resource_group_name="myResourceGroup",
    tags={
        "department": "finance",
    },
    zones=[
        "1",
        "2",
    ])

```

```yaml
resources:
  capacityReservationGroup:
    type: azure-native:compute:CapacityReservationGroup
    properties:
      capacityReservationGroupName: myCapacityReservationGroup
      location: westus
      resourceGroupName: myResourceGroup
      tags:
        department: finance
      zones:
        - '1'
        - '2'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:CapacityReservationGroup myCapacityReservationGroup /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/CapacityReservationGroups/myCapacityReservationGroup 
```
