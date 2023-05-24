Workspace details.
API Version: 2022-04-01-preview.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Workspaces
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.Easm.Workspace("workspace", new()
    {
        Location = "West US",
        ResourceGroupName = "dummyrg",
        WorkspaceName = "ThisisaWorkspace",
    });

});


```

```go
package main

import (
	easm "github.com/pulumi/pulumi-azure-native-sdk/easm"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := easm.NewWorkspace(ctx, "workspace", &easm.WorkspaceArgs{
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("dummyrg"),
			WorkspaceName:     pulumi.String("ThisisaWorkspace"),
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
import com.pulumi.azurenative.easm.Workspace;
import com.pulumi.azurenative.easm.WorkspaceArgs;
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
            .location("West US")
            .resourceGroupName("dummyrg")
            .workspaceName("ThisisaWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.easm.Workspace("workspace", {
    location: "West US",
    resourceGroupName: "dummyrg",
    workspaceName: "ThisisaWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.easm.Workspace("workspace",
    location="West US",
    resource_group_name="dummyrg",
    workspace_name="ThisisaWorkspace")

```

```yaml
resources:
  workspace:
    type: azure-native:easm:Workspace
    properties:
      location: West US
      resourceGroupName: dummyrg
      workspaceName: ThisisaWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:easm:Workspace ThisisaWorkspace /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/dummyrg/providers/Microsoft.Easm/workspaces/ThisisaWorkspace 
```
