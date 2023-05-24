Represents a project resource.
API Version: 2022-11-11-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Projects_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var project = new AzureNative.DevCenter.Project("project", new()
    {
        Description = "This is my first project.",
        DevCenterId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso",
        Location = "centralus",
        ProjectName = "DevProject",
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "CostCenter", "R&D" },
        },
    });

});


```

```go
package main

import (
	devcenter "github.com/pulumi/pulumi-azure-native-sdk/devcenter"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devcenter.NewProject(ctx, "project", &devcenter.ProjectArgs{
			Description:       pulumi.String("This is my first project."),
			DevCenterId:       pulumi.String("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso"),
			Location:          pulumi.String("centralus"),
			ProjectName:       pulumi.String("DevProject"),
			ResourceGroupName: pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"CostCenter": pulumi.String("R&D"),
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
import com.pulumi.azurenative.devcenter.Project;
import com.pulumi.azurenative.devcenter.ProjectArgs;
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
            .description("This is my first project.")
            .devCenterId("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso")
            .location("centralus")
            .projectName("DevProject")
            .resourceGroupName("rg1")
            .tags(Map.of("CostCenter", "R&D"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const project = new azure_native.devcenter.Project("project", {
    description: "This is my first project.",
    devCenterId: "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso",
    location: "centralus",
    projectName: "DevProject",
    resourceGroupName: "rg1",
    tags: {
        CostCenter: "R&D",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

project = azure_native.devcenter.Project("project",
    description="This is my first project.",
    dev_center_id="/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso",
    location="centralus",
    project_name="DevProject",
    resource_group_name="rg1",
    tags={
        "CostCenter": "R&D",
    })

```

```yaml
resources:
  project:
    type: azure-native:devcenter:Project
    properties:
      description: This is my first project.
      devCenterId: /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso
      location: centralus
      projectName: DevProject
      resourceGroupName: rg1
      tags:
        CostCenter: R&D

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devcenter:Project DevProject /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/projects/DevProject 
```
