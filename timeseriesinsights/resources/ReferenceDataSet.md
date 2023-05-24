A reference data set provides metadata about the events in an environment. Metadata in the reference data set will be joined with events as they are read from event sources. The metadata that makes up the reference data set is uploaded or modified through the Time Series Insights data plane APIs.
API Version: 2020-05-15.
Previous API Version: 2020-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ReferenceDataSetsCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var referenceDataSet = new AzureNative.TimeSeriesInsights.ReferenceDataSet("referenceDataSet", new()
    {
        EnvironmentName = "env1",
        KeyProperties = new[]
        {
            new AzureNative.TimeSeriesInsights.Inputs.ReferenceDataSetKeyPropertyArgs
            {
                Name = "DeviceId1",
                Type = "String",
            },
            new AzureNative.TimeSeriesInsights.Inputs.ReferenceDataSetKeyPropertyArgs
            {
                Name = "DeviceFloor",
                Type = "Double",
            },
        },
        Location = "West US",
        ReferenceDataSetName = "rds1",
        ResourceGroupName = "rg1",
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
		_, err := timeseriesinsights.NewReferenceDataSet(ctx, "referenceDataSet", &timeseriesinsights.ReferenceDataSetArgs{
			EnvironmentName: pulumi.String("env1"),
			KeyProperties: []timeseriesinsights.ReferenceDataSetKeyPropertyArgs{
				{
					Name: pulumi.String("DeviceId1"),
					Type: pulumi.String("String"),
				},
				{
					Name: pulumi.String("DeviceFloor"),
					Type: pulumi.String("Double"),
				},
			},
			Location:             pulumi.String("West US"),
			ReferenceDataSetName: pulumi.String("rds1"),
			ResourceGroupName:    pulumi.String("rg1"),
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
import com.pulumi.azurenative.timeseriesinsights.ReferenceDataSet;
import com.pulumi.azurenative.timeseriesinsights.ReferenceDataSetArgs;
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
        var referenceDataSet = new ReferenceDataSet("referenceDataSet", ReferenceDataSetArgs.builder()        
            .environmentName("env1")
            .keyProperties(            
                Map.ofEntries(
                    Map.entry("name", "DeviceId1"),
                    Map.entry("type", "String")
                ),
                Map.ofEntries(
                    Map.entry("name", "DeviceFloor"),
                    Map.entry("type", "Double")
                ))
            .location("West US")
            .referenceDataSetName("rds1")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const referenceDataSet = new azure_native.timeseriesinsights.ReferenceDataSet("referenceDataSet", {
    environmentName: "env1",
    keyProperties: [
        {
            name: "DeviceId1",
            type: "String",
        },
        {
            name: "DeviceFloor",
            type: "Double",
        },
    ],
    location: "West US",
    referenceDataSetName: "rds1",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

reference_data_set = azure_native.timeseriesinsights.ReferenceDataSet("referenceDataSet",
    environment_name="env1",
    key_properties=[
        azure_native.timeseriesinsights.ReferenceDataSetKeyPropertyArgs(
            name="DeviceId1",
            type="String",
        ),
        azure_native.timeseriesinsights.ReferenceDataSetKeyPropertyArgs(
            name="DeviceFloor",
            type="Double",
        ),
    ],
    location="West US",
    reference_data_set_name="rds1",
    resource_group_name="rg1")

```

```yaml
resources:
  referenceDataSet:
    type: azure-native:timeseriesinsights:ReferenceDataSet
    properties:
      environmentName: env1
      keyProperties:
        - name: DeviceId1
          type: String
        - name: DeviceFloor
          type: Double
      location: West US
      referenceDataSetName: rds1
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:timeseriesinsights:ReferenceDataSet rds1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.TimeSeriesInsights/Environments/env1/referenceDataSets/rds1 
```
