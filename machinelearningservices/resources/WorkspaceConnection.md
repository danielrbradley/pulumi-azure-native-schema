
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateWorkspaceConnection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspaceConnection = new AzureNative.MachineLearningServices.WorkspaceConnection("workspaceConnection", new()
    {
        ConnectionName = "connection-1",
        Properties = new AzureNative.MachineLearningServices.Inputs.NoneAuthTypeWorkspaceConnectionPropertiesArgs
        {
            AuthType = "None",
            Category = "ContainerRegistry",
            Target = "www.facebook.com",
        },
        ResourceGroupName = "resourceGroup-1",
        WorkspaceName = "workspace-1",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewWorkspaceConnection(ctx, "workspaceConnection", &machinelearningservices.WorkspaceConnectionArgs{
			ConnectionName: pulumi.String("connection-1"),
			Properties: machinelearningservices.NoneAuthTypeWorkspaceConnectionProperties{
				AuthType: "None",
				Category: "ContainerRegistry",
				Target:   "www.facebook.com",
			},
			ResourceGroupName: pulumi.String("resourceGroup-1"),
			WorkspaceName:     pulumi.String("workspace-1"),
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
import com.pulumi.azurenative.machinelearningservices.WorkspaceConnection;
import com.pulumi.azurenative.machinelearningservices.WorkspaceConnectionArgs;
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
        var workspaceConnection = new WorkspaceConnection("workspaceConnection", WorkspaceConnectionArgs.builder()        
            .connectionName("connection-1")
            .properties(Map.ofEntries(
                Map.entry("authType", "None"),
                Map.entry("category", "ContainerRegistry"),
                Map.entry("target", "www.facebook.com")
            ))
            .resourceGroupName("resourceGroup-1")
            .workspaceName("workspace-1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspaceConnection = new azure_native.machinelearningservices.WorkspaceConnection("workspaceConnection", {
    connectionName: "connection-1",
    properties: {
        authType: "None",
        category: "ContainerRegistry",
        target: "www.facebook.com",
    },
    resourceGroupName: "resourceGroup-1",
    workspaceName: "workspace-1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace_connection = azure_native.machinelearningservices.WorkspaceConnection("workspaceConnection",
    connection_name="connection-1",
    properties=azure_native.machinelearningservices.NoneAuthTypeWorkspaceConnectionPropertiesArgs(
        auth_type="None",
        category="ContainerRegistry",
        target="www.facebook.com",
    ),
    resource_group_name="resourceGroup-1",
    workspace_name="workspace-1")

```

```yaml
resources:
  workspaceConnection:
    type: azure-native:machinelearningservices:WorkspaceConnection
    properties:
      connectionName: connection-1
      properties:
        authType: None
        category: ContainerRegistry
        target: www.facebook.com
      resourceGroupName: resourceGroup-1
      workspaceName: workspace-1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:WorkspaceConnection connection-1 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/resourceGroup-1/providers/Microsoft.MachineLearningServices/workspaces/workspace-1/connections/connection-1 
```
