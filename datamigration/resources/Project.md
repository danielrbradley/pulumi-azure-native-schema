A project resource
API Version: 2021-06-30.
Previous API Version: 2018-04-19. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var project = new AzureNative.DataMigration.Project("project", new()
    {
        GroupName = "DmsSdkRg",
        Location = "southcentralus",
        ProjectName = "DmsSdkProject",
        ServiceName = "DmsSdkService",
        SourcePlatform = "SQL",
        TargetPlatform = "SQLDB",
    });

});


```

```go
package main

import (
	datamigration "github.com/pulumi/pulumi-azure-native-sdk/datamigration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datamigration.NewProject(ctx, "project", &datamigration.ProjectArgs{
			GroupName:      pulumi.String("DmsSdkRg"),
			Location:       pulumi.String("southcentralus"),
			ProjectName:    pulumi.String("DmsSdkProject"),
			ServiceName:    pulumi.String("DmsSdkService"),
			SourcePlatform: pulumi.String("SQL"),
			TargetPlatform: pulumi.String("SQLDB"),
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
import com.pulumi.azurenative.datamigration.Project;
import com.pulumi.azurenative.datamigration.ProjectArgs;
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
            .groupName("DmsSdkRg")
            .location("southcentralus")
            .projectName("DmsSdkProject")
            .serviceName("DmsSdkService")
            .sourcePlatform("SQL")
            .targetPlatform("SQLDB")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const project = new azure_native.datamigration.Project("project", {
    groupName: "DmsSdkRg",
    location: "southcentralus",
    projectName: "DmsSdkProject",
    serviceName: "DmsSdkService",
    sourcePlatform: "SQL",
    targetPlatform: "SQLDB",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

project = azure_native.datamigration.Project("project",
    group_name="DmsSdkRg",
    location="southcentralus",
    project_name="DmsSdkProject",
    service_name="DmsSdkService",
    source_platform="SQL",
    target_platform="SQLDB")

```

```yaml
resources:
  project:
    type: azure-native:datamigration:Project
    properties:
      groupName: DmsSdkRg
      location: southcentralus
      projectName: DmsSdkProject
      serviceName: DmsSdkService
      sourcePlatform: SQL
      targetPlatform: SQLDB

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datamigration:Project DmsSdkProject /subscriptions/fc04246f-04c5-437e-ac5e-206a19e7193f/resourceGroups/DmsSdkRg/providers/Microsoft.DataMigration/services/DmsSdkService/projects/DmsSdkProject 
```
