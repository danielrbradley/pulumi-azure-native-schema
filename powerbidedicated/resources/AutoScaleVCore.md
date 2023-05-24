Represents an instance of an auto scale v-core resource.
API Version: 2021-01-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create auto scale v-core
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var autoScaleVCore = new AzureNative.PowerBIDedicated.AutoScaleVCore("autoScaleVCore", new()
    {
        CapacityLimit = 10,
        CapacityObjectId = "a28f00bd-5330-4572-88f1-fa883e074785",
        Location = "West US",
        ResourceGroupName = "TestRG",
        Sku = new AzureNative.PowerBIDedicated.Inputs.AutoScaleVCoreSkuArgs
        {
            Capacity = 0,
            Name = "AutoScale",
            Tier = "AutoScale",
        },
        Tags = 
        {
            { "testKey", "testValue" },
        },
        VcoreName = "testvcore",
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
		_, err := powerbidedicated.NewAutoScaleVCore(ctx, "autoScaleVCore", &powerbidedicated.AutoScaleVCoreArgs{
			CapacityLimit:     pulumi.Int(10),
			CapacityObjectId:  pulumi.String("a28f00bd-5330-4572-88f1-fa883e074785"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("TestRG"),
			Sku: &powerbidedicated.AutoScaleVCoreSkuArgs{
				Capacity: pulumi.Int(0),
				Name:     pulumi.String("AutoScale"),
				Tier:     pulumi.String("AutoScale"),
			},
			Tags: pulumi.StringMap{
				"testKey": pulumi.String("testValue"),
			},
			VcoreName: pulumi.String("testvcore"),
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
import com.pulumi.azurenative.powerbidedicated.AutoScaleVCore;
import com.pulumi.azurenative.powerbidedicated.AutoScaleVCoreArgs;
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
        var autoScaleVCore = new AutoScaleVCore("autoScaleVCore", AutoScaleVCoreArgs.builder()        
            .capacityLimit(10)
            .capacityObjectId("a28f00bd-5330-4572-88f1-fa883e074785")
            .location("West US")
            .resourceGroupName("TestRG")
            .sku(Map.ofEntries(
                Map.entry("capacity", 0),
                Map.entry("name", "AutoScale"),
                Map.entry("tier", "AutoScale")
            ))
            .tags(Map.of("testKey", "testValue"))
            .vcoreName("testvcore")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const autoScaleVCore = new azure_native.powerbidedicated.AutoScaleVCore("autoScaleVCore", {
    capacityLimit: 10,
    capacityObjectId: "a28f00bd-5330-4572-88f1-fa883e074785",
    location: "West US",
    resourceGroupName: "TestRG",
    sku: {
        capacity: 0,
        name: "AutoScale",
        tier: "AutoScale",
    },
    tags: {
        testKey: "testValue",
    },
    vcoreName: "testvcore",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

auto_scale_v_core = azure_native.powerbidedicated.AutoScaleVCore("autoScaleVCore",
    capacity_limit=10,
    capacity_object_id="a28f00bd-5330-4572-88f1-fa883e074785",
    location="West US",
    resource_group_name="TestRG",
    sku=azure_native.powerbidedicated.AutoScaleVCoreSkuArgs(
        capacity=0,
        name="AutoScale",
        tier="AutoScale",
    ),
    tags={
        "testKey": "testValue",
    },
    vcore_name="testvcore")

```

```yaml
resources:
  autoScaleVCore:
    type: azure-native:powerbidedicated:AutoScaleVCore
    properties:
      capacityLimit: 10
      capacityObjectId: a28f00bd-5330-4572-88f1-fa883e074785
      location: West US
      resourceGroupName: TestRG
      sku:
        capacity: 0
        name: AutoScale
        tier: AutoScale
      tags:
        testKey: testValue
      vcoreName: testvcore

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:powerbidedicated:AutoScaleVCore testvcore /subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.PowerBIDedicated/autoScaleVCores/testvcore 
```
