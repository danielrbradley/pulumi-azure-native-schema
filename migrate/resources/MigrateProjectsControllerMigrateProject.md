Migrate project.
API Version: 2020-05-01.

{{% examples %}}
## Example Usage
{{% example %}}
### MigrateProject_Put
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var migrateProjectsControllerMigrateProject = new AzureNative.Migrate.MigrateProjectsControllerMigrateProject("migrateProjectsControllerMigrateProject", new()
    {
        Location = "eastus",
        MigrateProjectName = "projTest1",
        Properties = new AzureNative.Migrate.Inputs.MigrateProjectPropertiesArgs
        {
            PublicNetworkAccess = "Enabled",
        },
        ResourceGroupName = "pajindTest1",
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
		_, err := migrate.NewMigrateProjectsControllerMigrateProject(ctx, "migrateProjectsControllerMigrateProject", &migrate.MigrateProjectsControllerMigrateProjectArgs{
			Location:           pulumi.String("eastus"),
			MigrateProjectName: pulumi.String("projTest1"),
			Properties: &migrate.MigrateProjectPropertiesArgs{
				PublicNetworkAccess: pulumi.String("Enabled"),
			},
			ResourceGroupName: pulumi.String("pajindTest1"),
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
import com.pulumi.azurenative.migrate.MigrateProjectsControllerMigrateProject;
import com.pulumi.azurenative.migrate.MigrateProjectsControllerMigrateProjectArgs;
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
        var migrateProjectsControllerMigrateProject = new MigrateProjectsControllerMigrateProject("migrateProjectsControllerMigrateProject", MigrateProjectsControllerMigrateProjectArgs.builder()        
            .location("eastus")
            .migrateProjectName("projTest1")
            .properties(Map.of("publicNetworkAccess", "Enabled"))
            .resourceGroupName("pajindTest1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const migrateProjectsControllerMigrateProject = new azure_native.migrate.MigrateProjectsControllerMigrateProject("migrateProjectsControllerMigrateProject", {
    location: "eastus",
    migrateProjectName: "projTest1",
    properties: {
        publicNetworkAccess: "Enabled",
    },
    resourceGroupName: "pajindTest1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

migrate_projects_controller_migrate_project = azure_native.migrate.MigrateProjectsControllerMigrateProject("migrateProjectsControllerMigrateProject",
    location="eastus",
    migrate_project_name="projTest1",
    properties=azure_native.migrate.MigrateProjectPropertiesArgs(
        public_network_access="Enabled",
    ),
    resource_group_name="pajindTest1")

```

```yaml
resources:
  migrateProjectsControllerMigrateProject:
    type: azure-native:migrate:MigrateProjectsControllerMigrateProject
    properties:
      location: eastus
      migrateProjectName: projTest1
      properties:
        publicNetworkAccess: Enabled
      resourceGroupName: pajindTest1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:MigrateProjectsControllerMigrateProject proj90 /subscriptions/4bd2aa0f-2bd2-4d67-91a8-5a4533d58600/resourceGroups/pajindTest1/providers/Microsoft.Migrate/MigrateProjects/proj90 
```
