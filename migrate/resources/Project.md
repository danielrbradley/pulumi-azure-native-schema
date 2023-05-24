Azure Migrate Project.
API Version: 2019-10-01.
Previous API Version: 2019-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Projects_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var project = new AzureNative.Migrate.Project("project", new()
    {
        ETag = "",
        Location = "West Europe",
        ProjectName = "abGoyalProject2",
        Properties = new AzureNative.Migrate.Inputs.ProjectPropertiesArgs
        {
            AssessmentSolutionId = "/subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourcegroups/abgoyal-westeurope/providers/microsoft.migrate/migrateprojects/abgoyalweselfhost/Solutions/Servers-Assessment-ServerAssessment",
            ProjectStatus = "Active",
        },
        ResourceGroupName = "abgoyal-westEurope",
        Tags = null,
    });

});


```

```go
package main

import (
	migrate "github.com/pulumi/pulumi-azure-native-sdk/migrate"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := migrate.NewProject(ctx, "project", &migrate.ProjectArgs{
			ETag:        pulumi.String(""),
			Location:    pulumi.String("West Europe"),
			ProjectName: pulumi.String("abGoyalProject2"),
			Properties: &migrate.ProjectPropertiesArgs{
				AssessmentSolutionId: pulumi.String("/subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourcegroups/abgoyal-westeurope/providers/microsoft.migrate/migrateprojects/abgoyalweselfhost/Solutions/Servers-Assessment-ServerAssessment"),
				ProjectStatus:        pulumi.String("Active"),
			},
			ResourceGroupName: pulumi.String("abgoyal-westEurope"),
			Tags:              nil,
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
import com.pulumi.azurenative.migrate.Project;
import com.pulumi.azurenative.migrate.ProjectArgs;
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
        var project = new Project("project", ProjectArgs.builder()        
            .eTag("")
            .location("West Europe")
            .projectName("abGoyalProject2")
            .properties(Map.ofEntries(
                Map.entry("assessmentSolutionId", "/subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourcegroups/abgoyal-westeurope/providers/microsoft.migrate/migrateprojects/abgoyalweselfhost/Solutions/Servers-Assessment-ServerAssessment"),
                Map.entry("projectStatus", "Active")
            ))
            .resourceGroupName("abgoyal-westEurope")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const project = new azure_native.migrate.Project("project", {
    eTag: "",
    location: "West Europe",
    projectName: "abGoyalProject2",
    properties: {
        assessmentSolutionId: "/subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourcegroups/abgoyal-westeurope/providers/microsoft.migrate/migrateprojects/abgoyalweselfhost/Solutions/Servers-Assessment-ServerAssessment",
        projectStatus: "Active",
    },
    resourceGroupName: "abgoyal-westEurope",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

project = azure_native.migrate.Project("project",
    e_tag="",
    location="West Europe",
    project_name="abGoyalProject2",
    properties=azure_native.migrate.ProjectPropertiesArgs(
        assessment_solution_id="/subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourcegroups/abgoyal-westeurope/providers/microsoft.migrate/migrateprojects/abgoyalweselfhost/Solutions/Servers-Assessment-ServerAssessment",
        project_status="Active",
    ),
    resource_group_name="abgoyal-westEurope",
    tags={})

```

```yaml
resources:
  project:
    type: azure-native:migrate:Project
    properties:
      eTag:
      location: West Europe
      projectName: abGoyalProject2
      properties:
        assessmentSolutionId: /subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourcegroups/abgoyal-westeurope/providers/microsoft.migrate/migrateprojects/abgoyalweselfhost/Solutions/Servers-Assessment-ServerAssessment
        projectStatus: Active
      resourceGroupName: abgoyal-westEurope
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:Project abGoyalProject2 /subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourceGroups/abgoyal-westeurope/providers/Microsoft.Migrate/assessmentprojects/abGoyalProject2 
```
