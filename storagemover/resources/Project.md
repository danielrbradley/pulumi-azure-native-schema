The Project resource.
API Version: 2023-03-01.
Previous API Version: 2022-07-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var project = new AzureNative.StorageMover.Project("project", new()
    {
        Description = "Example Project Description",
        ProjectName = "examples-projectName",
        ResourceGroupName = "examples-rg",
        StorageMoverName = "examples-storageMoverName",
    });

});


```

```go
package main

import (
	storagemover "github.com/pulumi/pulumi-azure-native-sdk/storagemover"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storagemover.NewProject(ctx, "project", &storagemover.ProjectArgs{
			Description:       pulumi.String("Example Project Description"),
			ProjectName:       pulumi.String("examples-projectName"),
			ResourceGroupName: pulumi.String("examples-rg"),
			StorageMoverName:  pulumi.String("examples-storageMoverName"),
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
import com.pulumi.azurenative.storagemover.Project;
import com.pulumi.azurenative.storagemover.ProjectArgs;
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
            .description("Example Project Description")
            .projectName("examples-projectName")
            .resourceGroupName("examples-rg")
            .storageMoverName("examples-storageMoverName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const project = new azure_native.storagemover.Project("project", {
    description: "Example Project Description",
    projectName: "examples-projectName",
    resourceGroupName: "examples-rg",
    storageMoverName: "examples-storageMoverName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

project = azure_native.storagemover.Project("project",
    description="Example Project Description",
    project_name="examples-projectName",
    resource_group_name="examples-rg",
    storage_mover_name="examples-storageMoverName")

```

```yaml
resources:
  project:
    type: azure-native:storagemover:Project
    properties:
      description: Example Project Description
      projectName: examples-projectName
      resourceGroupName: examples-rg
      storageMoverName: examples-storageMoverName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagemover:Project examples-projectName /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.StorageMover/storageMovers/examples-storageMoverName/projects/examples-projectName 
```
