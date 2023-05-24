Hub resource.
API Version: 2017-04-26.
Previous API Version: 2017-04-26. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Hubs_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hub = new AzureNative.CustomerInsights.Hub("hub", new()
    {
        HubBillingInfo = new AzureNative.CustomerInsights.Inputs.HubBillingInfoFormatArgs
        {
            MaxUnits = 5,
            MinUnits = 1,
            SkuName = "B0",
        },
        HubName = "sdkTestHub",
        Location = "West US",
        ResourceGroupName = "TestHubRG",
    });

});


```

```go
package main

import (
	customerinsights "github.com/pulumi/pulumi-azure-native-sdk/customerinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := customerinsights.NewHub(ctx, "hub", &customerinsights.HubArgs{
			HubBillingInfo: &customerinsights.HubBillingInfoFormatArgs{
				MaxUnits: pulumi.Int(5),
				MinUnits: pulumi.Int(1),
				SkuName:  pulumi.String("B0"),
			},
			HubName:           pulumi.String("sdkTestHub"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("TestHubRG"),
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
import com.pulumi.azurenative.customerinsights.Hub;
import com.pulumi.azurenative.customerinsights.HubArgs;
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
        var hub = new Hub("hub", HubArgs.builder()        
            .hubBillingInfo(Map.ofEntries(
                Map.entry("maxUnits", 5),
                Map.entry("minUnits", 1),
                Map.entry("skuName", "B0")
            ))
            .hubName("sdkTestHub")
            .location("West US")
            .resourceGroupName("TestHubRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hub = new azure_native.customerinsights.Hub("hub", {
    hubBillingInfo: {
        maxUnits: 5,
        minUnits: 1,
        skuName: "B0",
    },
    hubName: "sdkTestHub",
    location: "West US",
    resourceGroupName: "TestHubRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hub = azure_native.customerinsights.Hub("hub",
    hub_billing_info=azure_native.customerinsights.HubBillingInfoFormatArgs(
        max_units=5,
        min_units=1,
        sku_name="B0",
    ),
    hub_name="sdkTestHub",
    location="West US",
    resource_group_name="TestHubRG")

```

```yaml
resources:
  hub:
    type: azure-native:customerinsights:Hub
    properties:
      hubBillingInfo:
        maxUnits: 5
        minUnits: 1
        skuName: B0
      hubName: sdkTestHub
      location: West US
      resourceGroupName: TestHubRG

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customerinsights:Hub testHub2839 /subscriptions/subid/resourceGroups/TestHubRG/providers/Microsoft.CustomerInsights/hubs/testHub2839 
```
