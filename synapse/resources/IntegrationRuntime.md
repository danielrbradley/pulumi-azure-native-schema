Integration runtime resource type.
API Version: 2021-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create integration runtime
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationRuntime = new AzureNative.Synapse.IntegrationRuntime("integrationRuntime", new()
    {
        IntegrationRuntimeName = "exampleIntegrationRuntime",
        Properties = new AzureNative.Synapse.Inputs.SelfHostedIntegrationRuntimeArgs
        {
            Description = "A selfhosted integration runtime",
            Type = "SelfHosted",
        },
        ResourceGroupName = "exampleResourceGroup",
        WorkspaceName = "exampleWorkspace",
    });

});


```

```go
package main

import (
	synapse "github.com/pulumi/pulumi-azure-native-sdk/synapse"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := synapse.NewIntegrationRuntime(ctx, "integrationRuntime", &synapse.IntegrationRuntimeArgs{
			IntegrationRuntimeName: pulumi.String("exampleIntegrationRuntime"),
			Properties: synapse.SelfHostedIntegrationRuntime{
				Description: "A selfhosted integration runtime",
				Type:        "SelfHosted",
			},
			ResourceGroupName: pulumi.String("exampleResourceGroup"),
			WorkspaceName:     pulumi.String("exampleWorkspace"),
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
import com.pulumi.azurenative.synapse.IntegrationRuntime;
import com.pulumi.azurenative.synapse.IntegrationRuntimeArgs;
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
        var integrationRuntime = new IntegrationRuntime("integrationRuntime", IntegrationRuntimeArgs.builder()        
            .integrationRuntimeName("exampleIntegrationRuntime")
            .properties(Map.ofEntries(
                Map.entry("description", "A selfhosted integration runtime"),
                Map.entry("type", "SelfHosted")
            ))
            .resourceGroupName("exampleResourceGroup")
            .workspaceName("exampleWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationRuntime = new azure_native.synapse.IntegrationRuntime("integrationRuntime", {
    integrationRuntimeName: "exampleIntegrationRuntime",
    properties: {
        description: "A selfhosted integration runtime",
        type: "SelfHosted",
    },
    resourceGroupName: "exampleResourceGroup",
    workspaceName: "exampleWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_runtime = azure_native.synapse.IntegrationRuntime("integrationRuntime",
    integration_runtime_name="exampleIntegrationRuntime",
    properties=azure_native.synapse.SelfHostedIntegrationRuntimeArgs(
        description="A selfhosted integration runtime",
        type="SelfHosted",
    ),
    resource_group_name="exampleResourceGroup",
    workspace_name="exampleWorkspace")

```

```yaml
resources:
  integrationRuntime:
    type: azure-native:synapse:IntegrationRuntime
    properties:
      integrationRuntimeName: exampleIntegrationRuntime
      properties:
        description: A selfhosted integration runtime
        type: SelfHosted
      resourceGroupName: exampleResourceGroup
      workspaceName: exampleWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:synapse:IntegrationRuntime exampleIntegrationRuntime /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.Synapse/workspaces/exampleWorkspaceName/integrationruntimes/exampleIntegrationRuntime 
```
