Azure Traffic Collector resource.
API Version: 2022-11-01.
Previous API Version: 2022-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a traffic collector
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureTrafficCollector = new AzureNative.NetworkFunction.AzureTrafficCollector("azureTrafficCollector", new()
    {
        AzureTrafficCollectorName = "atc",
        Location = "West US",
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "value1" },
        },
    });

});


```

```go
package main

import (
	networkfunction "github.com/pulumi/pulumi-azure-native-sdk/networkfunction"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := networkfunction.NewAzureTrafficCollector(ctx, "azureTrafficCollector", &networkfunction.AzureTrafficCollectorArgs{
			AzureTrafficCollectorName: pulumi.String("atc"),
			Location:                  pulumi.String("West US"),
			ResourceGroupName:         pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
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
import com.pulumi.azurenative.networkfunction.AzureTrafficCollector;
import com.pulumi.azurenative.networkfunction.AzureTrafficCollectorArgs;
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
        var azureTrafficCollector = new AzureTrafficCollector("azureTrafficCollector", AzureTrafficCollectorArgs.builder()        
            .azureTrafficCollectorName("atc")
            .location("West US")
            .resourceGroupName("rg1")
            .tags(Map.of("key1", "value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureTrafficCollector = new azure_native.networkfunction.AzureTrafficCollector("azureTrafficCollector", {
    azureTrafficCollectorName: "atc",
    location: "West US",
    resourceGroupName: "rg1",
    tags: {
        key1: "value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_traffic_collector = azure_native.networkfunction.AzureTrafficCollector("azureTrafficCollector",
    azure_traffic_collector_name="atc",
    location="West US",
    resource_group_name="rg1",
    tags={
        "key1": "value1",
    })

```

```yaml
resources:
  azureTrafficCollector:
    type: azure-native:networkfunction:AzureTrafficCollector
    properties:
      azureTrafficCollectorName: atc
      location: West US
      resourceGroupName: rg1
      tags:
        key1: value1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkfunction:AzureTrafficCollector atc /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.NetworkFunction/azureTrafficCollectors/atc 
```
