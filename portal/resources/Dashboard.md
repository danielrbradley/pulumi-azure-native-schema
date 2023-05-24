The shared dashboard resource definition.
API Version: 2020-09-01-preview.
Previous API Version: 2020-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a Dashboard
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dashboard = new AzureNative.Portal.Dashboard("dashboard", new()
    {
        DashboardName = "testDashboard",
        Lenses = new[]
        {
            new AzureNative.Portal.Inputs.DashboardLensArgs
            {
                Order = 1,
                Parts = new[]
                {
                    new AzureNative.Portal.Inputs.DashboardPartsArgs
                    {
                        Position = new AzureNative.Portal.Inputs.DashboardPartsPositionArgs
                        {
                            ColSpan = 3,
                            RowSpan = 4,
                            X = 1,
                            Y = 2,
                        },
                    },
                    new AzureNative.Portal.Inputs.DashboardPartsArgs
                    {
                        Position = new AzureNative.Portal.Inputs.DashboardPartsPositionArgs
                        {
                            ColSpan = 6,
                            RowSpan = 6,
                            X = 5,
                            Y = 5,
                        },
                    },
                },
            },
            new AzureNative.Portal.Inputs.DashboardLensArgs
            {
                Order = 2,
                Parts = new[] {},
            },
        },
        Location = "eastus",
        Metadata = 
        {
            { "metadata", 
            {
                { "ColSpan", 2 },
                { "RowSpan", 1 },
                { "X", 4 },
                { "Y", 3 },
            } },
        },
        ResourceGroupName = "testRG",
        Tags = 
        {
            { "aKey", "aValue" },
            { "anotherKey", "anotherValue" },
        },
    });

});


```

```go
package main

import (
	portal "github.com/pulumi/pulumi-azure-native-sdk/portal"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := portal.NewDashboard(ctx, "dashboard", &portal.DashboardArgs{
			DashboardName: pulumi.String("testDashboard"),
			Lenses: []portal.DashboardLensArgs{
				{
					Order: pulumi.Int(1),
					Parts: []portal.DashboardPartsArgs{
						{
							Position: {
								ColSpan: pulumi.Int(3),
								RowSpan: pulumi.Int(4),
								X:       pulumi.Int(1),
								Y:       pulumi.Int(2),
							},
						},
						{
							Position: {
								ColSpan: pulumi.Int(6),
								RowSpan: pulumi.Int(6),
								X:       pulumi.Int(5),
								Y:       pulumi.Int(5),
							},
						},
					},
				},
				{
					Order: pulumi.Int(2),
					Parts: portal.DashboardPartsArray{},
				},
			},
			Location: pulumi.String("eastus"),
			Metadata: pulumi.AnyMap{
				"metadata": pulumi.Any{
					ColSpan: 2,
					RowSpan: 1,
					X:       4,
					Y:       3,
				},
			},
			ResourceGroupName: pulumi.String("testRG"),
			Tags: pulumi.StringMap{
				"aKey":       pulumi.String("aValue"),
				"anotherKey": pulumi.String("anotherValue"),
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
import com.pulumi.azurenative.portal.Dashboard;
import com.pulumi.azurenative.portal.DashboardArgs;
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
        var dashboard = new Dashboard("dashboard", DashboardArgs.builder()        
            .dashboardName("testDashboard")
            .lenses(            
                Map.ofEntries(
                    Map.entry("order", 1),
                    Map.entry("parts",                     
                        Map.of("position", Map.ofEntries(
                            Map.entry("colSpan", 3),
                            Map.entry("rowSpan", 4),
                            Map.entry("x", 1),
                            Map.entry("y", 2)
                        )),
                        Map.of("position", Map.ofEntries(
                            Map.entry("colSpan", 6),
                            Map.entry("rowSpan", 6),
                            Map.entry("x", 5),
                            Map.entry("y", 5)
                        )))
                ),
                Map.ofEntries(
                    Map.entry("order", 2),
                    Map.entry("parts", )
                ))
            .location("eastus")
            .metadata(Map.of("metadata", Map.ofEntries(
                Map.entry("ColSpan", 2),
                Map.entry("RowSpan", 1),
                Map.entry("X", 4),
                Map.entry("Y", 3)
            )))
            .resourceGroupName("testRG")
            .tags(Map.ofEntries(
                Map.entry("aKey", "aValue"),
                Map.entry("anotherKey", "anotherValue")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dashboard = new azure_native.portal.Dashboard("dashboard", {
    dashboardName: "testDashboard",
    lenses: [
        {
            order: 1,
            parts: [
                {
                    position: {
                        colSpan: 3,
                        rowSpan: 4,
                        x: 1,
                        y: 2,
                    },
                },
                {
                    position: {
                        colSpan: 6,
                        rowSpan: 6,
                        x: 5,
                        y: 5,
                    },
                },
            ],
        },
        {
            order: 2,
            parts: [],
        },
    ],
    location: "eastus",
    metadata: {
        metadata: {
            ColSpan: 2,
            RowSpan: 1,
            X: 4,
            Y: 3,
        },
    },
    resourceGroupName: "testRG",
    tags: {
        aKey: "aValue",
        anotherKey: "anotherValue",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dashboard = azure_native.portal.Dashboard("dashboard",
    dashboard_name="testDashboard",
    lenses=[
        {
            "order": 1,
            "parts": [
                {
                    "position": azure_native.portal.DashboardPartsPositionArgs(
                        col_span=3,
                        row_span=4,
                        x=1,
                        y=2,
                    ),
                },
                {
                    "position": azure_native.portal.DashboardPartsPositionArgs(
                        col_span=6,
                        row_span=6,
                        x=5,
                        y=5,
                    ),
                },
            ],
        },
        {
            "order": 2,
            "parts": [],
        },
    ],
    location="eastus",
    metadata={
        "metadata": {
            "ColSpan": 2,
            "RowSpan": 1,
            "X": 4,
            "Y": 3,
        },
    },
    resource_group_name="testRG",
    tags={
        "aKey": "aValue",
        "anotherKey": "anotherValue",
    })

```

```yaml
resources:
  dashboard:
    type: azure-native:portal:Dashboard
    properties:
      dashboardName: testDashboard
      lenses:
        - order: 1
          parts:
            - position:
                colSpan: 3
                rowSpan: 4
                x: 1
                y: 2
            - position:
                colSpan: 6
                rowSpan: 6
                x: 5
                y: 5
        - order: 2
          parts: []
      location: eastus
      metadata:
        metadata:
          ColSpan: 2
          RowSpan: 1
          X: 4
          Y: 3
      resourceGroupName: testRG
      tags:
        aKey: aValue
        anotherKey: anotherValue

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:portal:Dashboard testDashboard /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/testRG/providers/Microsoft.Portal/dashboards/testDashboard 
```
