Specifies information about the capacity reservation.
API Version: 2022-11-01.
Previous API Version: 2021-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a capacity reservation .
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var capacityReservation = new AzureNative.Compute.CapacityReservation("capacityReservation", new()
    {
        CapacityReservationGroupName = "myCapacityReservationGroup",
        CapacityReservationName = "myCapacityReservation",
        Location = "westus",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 4,
            Name = "Standard_DS1_v2",
        },
        Tags = 
        {
            { "department", "HR" },
        },
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
		_, err := compute.NewCapacityReservation(ctx, "capacityReservation", &compute.CapacityReservationArgs{
			CapacityReservationGroupName: pulumi.String("myCapacityReservationGroup"),
			CapacityReservationName:      pulumi.String("myCapacityReservation"),
			Location:                     pulumi.String("westus"),
			ResourceGroupName:            pulumi.String("myResourceGroup"),
			Sku: &compute.SkuArgs{
				Capacity: pulumi.Float64(4),
				Name:     pulumi.String("Standard_DS1_v2"),
			},
			Tags: pulumi.StringMap{
				"department": pulumi.String("HR"),
			},
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
import com.pulumi.azurenative.compute.CapacityReservation;
import com.pulumi.azurenative.compute.CapacityReservationArgs;
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
        var capacityReservation = new CapacityReservation("capacityReservation", CapacityReservationArgs.builder()        
            .capacityReservationGroupName("myCapacityReservationGroup")
            .capacityReservationName("myCapacityReservation")
            .location("westus")
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 4),
                Map.entry("name", "Standard_DS1_v2")
            ))
            .tags(Map.of("department", "HR"))
            .zones("1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const capacityReservation = new azure_native.compute.CapacityReservation("capacityReservation", {
    capacityReservationGroupName: "myCapacityReservationGroup",
    capacityReservationName: "myCapacityReservation",
    location: "westus",
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 4,
        name: "Standard_DS1_v2",
    },
    tags: {
        department: "HR",
    },
    zones: ["1"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

capacity_reservation = azure_native.compute.CapacityReservation("capacityReservation",
    capacity_reservation_group_name="myCapacityReservationGroup",
    capacity_reservation_name="myCapacityReservation",
    location="westus",
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=4,
        name="Standard_DS1_v2",
    ),
    tags={
        "department": "HR",
    },
    zones=["1"])

```

```yaml
resources:
  capacityReservation:
    type: azure-native:compute:CapacityReservation
    properties:
      capacityReservationGroupName: myCapacityReservationGroup
      capacityReservationName: myCapacityReservation
      location: westus
      resourceGroupName: myResourceGroup
      sku:
        capacity: 4
        name: Standard_DS1_v2
      tags:
        department: HR
      zones:
        - '1'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:CapacityReservation myCapacityReservation /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/capacityReservationGroups/myCapacityReservationGroup/capacityReservations/myCapacityReservation 
```
