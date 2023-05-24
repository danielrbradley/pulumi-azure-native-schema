Workspace resource.
API Version: 2022-12-01.
Previous API Version: 2022-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a workspace
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.HealthcareApis.Workspace("workspace", new()
    {
        Location = "westus",
        ResourceGroupName = "testRG",
        WorkspaceName = "workspace1",
    });

});


```

```go
package main

import (
	healthcareapis "github.com/pulumi/pulumi-azure-native-sdk/healthcareapis"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := healthcareapis.NewWorkspace(ctx, "workspace", &healthcareapis.WorkspaceArgs{
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("testRG"),
			WorkspaceName:     pulumi.String("workspace1"),
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
import com.pulumi.azurenative.healthcareapis.Workspace;
import com.pulumi.azurenative.healthcareapis.WorkspaceArgs;
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
        var workspace = new Workspace("workspace", WorkspaceArgs.builder()        
            .location("westus")
            .resourceGroupName("testRG")
            .workspaceName("workspace1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.healthcareapis.Workspace("workspace", {
    location: "westus",
    resourceGroupName: "testRG",
    workspaceName: "workspace1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.healthcareapis.Workspace("workspace",
    location="westus",
    resource_group_name="testRG",
    workspace_name="workspace1")

```

```yaml
resources:
  workspace:
    type: azure-native:healthcareapis:Workspace
    properties:
      location: westus
      resourceGroupName: testRG
      workspaceName: workspace1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:healthcareapis:Workspace workspace1 /subscriptions/subid/resourceGroups/testRG/providers/Microsoft.HealthcareApis/workspaces/workspace1 
```
