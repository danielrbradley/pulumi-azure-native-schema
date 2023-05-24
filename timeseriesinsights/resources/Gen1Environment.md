An environment is a set of time-series data available for query, and is the top level Azure Time Series Insights resource. Gen1 environments have data retention limits.
API Version: 2020-05-15.
Previous API Version: 2020-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### EnvironmentsCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gen1Environment = new AzureNative.TimeSeriesInsights.Gen1Environment("gen1Environment", new()
    {
        DataRetentionTime = "P31D",
        EnvironmentName = "env1",
        Kind = "Gen1",
        Location = "West US",
        PartitionKeyProperties = new[]
        {
            new AzureNative.TimeSeriesInsights.Inputs.TimeSeriesIdPropertyArgs
            {
                Name = "DeviceId1",
                Type = "String",
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.TimeSeriesInsights.Inputs.SkuArgs
        {
            Capacity = 1,
            Name = "S1",
        },
    });

});


```

```go
package main

import (
	timeseriesinsights "github.com/pulumi/pulumi-azure-native-sdk/timeseriesinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := timeseriesinsights.NewGen1Environment(ctx, "gen1Environment", &timeseriesinsights.Gen1EnvironmentArgs{
			DataRetentionTime: pulumi.String("P31D"),
			EnvironmentName:   pulumi.String("env1"),
			Kind:              pulumi.String("Gen1"),
			Location:          pulumi.String("West US"),
			PartitionKeyProperties: []timeseriesinsights.TimeSeriesIdPropertyArgs{
				{
					Name: pulumi.String("DeviceId1"),
					Type: pulumi.String("String"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &timeseriesinsights.SkuArgs{
				Capacity: pulumi.Int(1),
				Name:     pulumi.String("S1"),
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
import com.pulumi.azurenative.timeseriesinsights.Gen1Environment;
import com.pulumi.azurenative.timeseriesinsights.Gen1EnvironmentArgs;
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
        var gen1Environment = new Gen1Environment("gen1Environment", Gen1EnvironmentArgs.builder()        
            .dataRetentionTime("P31D")
            .environmentName("env1")
            .kind("Gen1")
            .location("West US")
            .partitionKeyProperties(Map.ofEntries(
                Map.entry("name", "DeviceId1"),
                Map.entry("type", "String")
            ))
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "S1")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gen1Environment = new azure_native.timeseriesinsights.Gen1Environment("gen1Environment", {
    dataRetentionTime: "P31D",
    environmentName: "env1",
    kind: "Gen1",
    location: "West US",
    partitionKeyProperties: [{
        name: "DeviceId1",
        type: "String",
    }],
    resourceGroupName: "rg1",
    sku: {
        capacity: 1,
        name: "S1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gen1_environment = azure_native.timeseriesinsights.Gen1Environment("gen1Environment",
    data_retention_time="P31D",
    environment_name="env1",
    kind="Gen1",
    location="West US",
    partition_key_properties=[azure_native.timeseriesinsights.TimeSeriesIdPropertyArgs(
        name="DeviceId1",
        type="String",
    )],
    resource_group_name="rg1",
    sku=azure_native.timeseriesinsights.SkuArgs(
        capacity=1,
        name="S1",
    ))

```

```yaml
resources:
  gen1Environment:
    type: azure-native:timeseriesinsights:Gen1Environment
    properties:
      dataRetentionTime: P31D
      environmentName: env1
      kind: Gen1
      location: West US
      partitionKeyProperties:
        - name: DeviceId1
          type: String
      resourceGroupName: rg1
      sku:
        capacity: 1
        name: S1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:timeseriesinsights:Gen1Environment env1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.TimeSeriesInsights/Environments/env1 
```
