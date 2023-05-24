Represents an instance of a Dedicated Capacity resource.
API Version: 2021-01-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create capacity
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var capacityDetails = new AzureNative.PowerBIDedicated.CapacityDetails("capacityDetails", new()
    {
        Administration = new AzureNative.PowerBIDedicated.Inputs.DedicatedCapacityAdministratorsArgs
        {
            Members = new[]
            {
                "azsdktest@microsoft.com",
                "azsdktest2@microsoft.com",
            },
        },
        DedicatedCapacityName = "azsdktest",
        Location = "West US",
        ResourceGroupName = "TestRG",
        Sku = new AzureNative.PowerBIDedicated.Inputs.CapacitySkuArgs
        {
            Name = "A1",
            Tier = "PBIE_Azure",
        },
        Tags = 
        {
            { "testKey", "testValue" },
        },
    });

});


```

```go
package main

import (
	powerbidedicated "github.com/pulumi/pulumi-azure-native-sdk/powerbidedicated"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := powerbidedicated.NewCapacityDetails(ctx, "capacityDetails", &powerbidedicated.CapacityDetailsArgs{
			Administration: &powerbidedicated.DedicatedCapacityAdministratorsArgs{
				Members: pulumi.StringArray{
					pulumi.String("azsdktest@microsoft.com"),
					pulumi.String("azsdktest2@microsoft.com"),
				},
			},
			DedicatedCapacityName: pulumi.String("azsdktest"),
			Location:              pulumi.String("West US"),
			ResourceGroupName:     pulumi.String("TestRG"),
			Sku: &powerbidedicated.CapacitySkuArgs{
				Name: pulumi.String("A1"),
				Tier: pulumi.String("PBIE_Azure"),
			},
			Tags: pulumi.StringMap{
				"testKey": pulumi.String("testValue"),
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
import com.pulumi.azurenative.powerbidedicated.CapacityDetails;
import com.pulumi.azurenative.powerbidedicated.CapacityDetailsArgs;
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
        var capacityDetails = new CapacityDetails("capacityDetails", CapacityDetailsArgs.builder()        
            .administration(Map.of("members",             
                "azsdktest@microsoft.com",
                "azsdktest2@microsoft.com"))
            .dedicatedCapacityName("azsdktest")
            .location("West US")
            .resourceGroupName("TestRG")
            .sku(Map.ofEntries(
                Map.entry("name", "A1"),
                Map.entry("tier", "PBIE_Azure")
            ))
            .tags(Map.of("testKey", "testValue"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const capacityDetails = new azure_native.powerbidedicated.CapacityDetails("capacityDetails", {
    administration: {
        members: [
            "azsdktest@microsoft.com",
            "azsdktest2@microsoft.com",
        ],
    },
    dedicatedCapacityName: "azsdktest",
    location: "West US",
    resourceGroupName: "TestRG",
    sku: {
        name: "A1",
        tier: "PBIE_Azure",
    },
    tags: {
        testKey: "testValue",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

capacity_details = azure_native.powerbidedicated.CapacityDetails("capacityDetails",
    administration=azure_native.powerbidedicated.DedicatedCapacityAdministratorsArgs(
        members=[
            "azsdktest@microsoft.com",
            "azsdktest2@microsoft.com",
        ],
    ),
    dedicated_capacity_name="azsdktest",
    location="West US",
    resource_group_name="TestRG",
    sku=azure_native.powerbidedicated.CapacitySkuArgs(
        name="A1",
        tier="PBIE_Azure",
    ),
    tags={
        "testKey": "testValue",
    })

```

```yaml
resources:
  capacityDetails:
    type: azure-native:powerbidedicated:CapacityDetails
    properties:
      administration:
        members:
          - azsdktest@microsoft.com
          - azsdktest2@microsoft.com
      dedicatedCapacityName: azsdktest
      location: West US
      resourceGroupName: TestRG
      sku:
        name: A1
        tier: PBIE_Azure
      tags:
        testKey: testValue

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:powerbidedicated:CapacityDetails azsdktest /subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.PowerBIDedicated/capacities/azsdktest 
```
