IoT Security solution configuration and resource information.
API Version: 2019-08-01.
Previous API Version: 2019-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a IoT security solution
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var iotSecuritySolution = new AzureNative.Security.IotSecuritySolution("iotSecuritySolution", new()
    {
        DisabledDataSources = new[] {},
        DisplayName = "Solution Default",
        Export = new[] {},
        IotHubs = new[]
        {
            "/subscriptions/075423e9-7d33-4166-8bdf-3920b04e3735/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/FirstIotHub",
        },
        Location = "East Us",
        RecommendationsConfiguration = new[]
        {
            new AzureNative.Security.Inputs.RecommendationConfigurationPropertiesArgs
            {
                RecommendationType = "IoT_OpenPorts",
                Status = "Disabled",
            },
            new AzureNative.Security.Inputs.RecommendationConfigurationPropertiesArgs
            {
                RecommendationType = "IoT_SharedCredentials",
                Status = "Disabled",
            },
        },
        ResourceGroupName = "MyGroup",
        SolutionName = "default",
        Status = "Enabled",
        Tags = null,
        UnmaskedIpLoggingStatus = "Enabled",
        UserDefinedResources = new AzureNative.Security.Inputs.UserDefinedResourcesPropertiesArgs
        {
            Query = "where type != \"microsoft.devices/iothubs\" | where name contains \"iot\"",
            QuerySubscriptions = new[]
            {
                "075423e9-7d33-4166-8bdf-3920b04e3735",
            },
        },
        Workspace = "/subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1",
    });

});


```

```go
package main

import (
	security "github.com/pulumi/pulumi-azure-native-sdk/security"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := security.NewIotSecuritySolution(ctx, "iotSecuritySolution", &security.IotSecuritySolutionArgs{
			DisabledDataSources: pulumi.StringArray{},
			DisplayName:         pulumi.String("Solution Default"),
			Export:              pulumi.StringArray{},
			IotHubs: pulumi.StringArray{
				pulumi.String("/subscriptions/075423e9-7d33-4166-8bdf-3920b04e3735/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/FirstIotHub"),
			},
			Location: pulumi.String("East Us"),
			RecommendationsConfiguration: []security.RecommendationConfigurationPropertiesArgs{
				{
					RecommendationType: pulumi.String("IoT_OpenPorts"),
					Status:             pulumi.String("Disabled"),
				},
				{
					RecommendationType: pulumi.String("IoT_SharedCredentials"),
					Status:             pulumi.String("Disabled"),
				},
			},
			ResourceGroupName:       pulumi.String("MyGroup"),
			SolutionName:            pulumi.String("default"),
			Status:                  pulumi.String("Enabled"),
			Tags:                    nil,
			UnmaskedIpLoggingStatus: pulumi.String("Enabled"),
			UserDefinedResources: &security.UserDefinedResourcesPropertiesArgs{
				Query: pulumi.String("where type != \"microsoft.devices/iothubs\" | where name contains \"iot\""),
				QuerySubscriptions: pulumi.StringArray{
					pulumi.String("075423e9-7d33-4166-8bdf-3920b04e3735"),
				},
			},
			Workspace: pulumi.String("/subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1"),
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
import com.pulumi.azurenative.security.IotSecuritySolution;
import com.pulumi.azurenative.security.IotSecuritySolutionArgs;
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
        var iotSecuritySolution = new IotSecuritySolution("iotSecuritySolution", IotSecuritySolutionArgs.builder()        
            .disabledDataSources()
            .displayName("Solution Default")
            .export()
            .iotHubs("/subscriptions/075423e9-7d33-4166-8bdf-3920b04e3735/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/FirstIotHub")
            .location("East Us")
            .recommendationsConfiguration(            
                Map.ofEntries(
                    Map.entry("recommendationType", "IoT_OpenPorts"),
                    Map.entry("status", "Disabled")
                ),
                Map.ofEntries(
                    Map.entry("recommendationType", "IoT_SharedCredentials"),
                    Map.entry("status", "Disabled")
                ))
            .resourceGroupName("MyGroup")
            .solutionName("default")
            .status("Enabled")
            .tags()
            .unmaskedIpLoggingStatus("Enabled")
            .userDefinedResources(Map.ofEntries(
                Map.entry("query", "where type != \"microsoft.devices/iothubs\" | where name contains \"iot\""),
                Map.entry("querySubscriptions", "075423e9-7d33-4166-8bdf-3920b04e3735")
            ))
            .workspace("/subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const iotSecuritySolution = new azure_native.security.IotSecuritySolution("iotSecuritySolution", {
    disabledDataSources: [],
    displayName: "Solution Default",
    "export": [],
    iotHubs: ["/subscriptions/075423e9-7d33-4166-8bdf-3920b04e3735/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/FirstIotHub"],
    location: "East Us",
    recommendationsConfiguration: [
        {
            recommendationType: "IoT_OpenPorts",
            status: "Disabled",
        },
        {
            recommendationType: "IoT_SharedCredentials",
            status: "Disabled",
        },
    ],
    resourceGroupName: "MyGroup",
    solutionName: "default",
    status: "Enabled",
    tags: {},
    unmaskedIpLoggingStatus: "Enabled",
    userDefinedResources: {
        query: "where type != \"microsoft.devices/iothubs\" | where name contains \"iot\"",
        querySubscriptions: ["075423e9-7d33-4166-8bdf-3920b04e3735"],
    },
    workspace: "/subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

iot_security_solution = azure_native.security.IotSecuritySolution("iotSecuritySolution",
    disabled_data_sources=[],
    display_name="Solution Default",
    export=[],
    iot_hubs=["/subscriptions/075423e9-7d33-4166-8bdf-3920b04e3735/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/FirstIotHub"],
    location="East Us",
    recommendations_configuration=[
        azure_native.security.RecommendationConfigurationPropertiesArgs(
            recommendation_type="IoT_OpenPorts",
            status="Disabled",
        ),
        azure_native.security.RecommendationConfigurationPropertiesArgs(
            recommendation_type="IoT_SharedCredentials",
            status="Disabled",
        ),
    ],
    resource_group_name="MyGroup",
    solution_name="default",
    status="Enabled",
    tags={},
    unmasked_ip_logging_status="Enabled",
    user_defined_resources=azure_native.security.UserDefinedResourcesPropertiesArgs(
        query="where type != \"microsoft.devices/iothubs\" | where name contains \"iot\"",
        query_subscriptions=["075423e9-7d33-4166-8bdf-3920b04e3735"],
    ),
    workspace="/subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1")

```

```yaml
resources:
  iotSecuritySolution:
    type: azure-native:security:IotSecuritySolution
    properties:
      disabledDataSources: []
      displayName: Solution Default
      export: []
      iotHubs:
        - /subscriptions/075423e9-7d33-4166-8bdf-3920b04e3735/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/FirstIotHub
      location: East Us
      recommendationsConfiguration:
        - recommendationType: IoT_OpenPorts
          status: Disabled
        - recommendationType: IoT_SharedCredentials
          status: Disabled
      resourceGroupName: MyGroup
      solutionName: default
      status: Enabled
      tags: {}
      unmaskedIpLoggingStatus: Enabled
      userDefinedResources:
        query: where type != "microsoft.devices/iothubs" | where name contains "iot"
        querySubscriptions:
          - 075423e9-7d33-4166-8bdf-3920b04e3735
      workspace: /subscriptions/c4930e90-cd72-4aa5-93e9-2d081d129569/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:security:IotSecuritySolution default /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/MyGroup/providers/Microsoft.Security/Locations/eastus/IoTSecuritySolutions/default 
```
