Integration runtime resource type.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### IntegrationRuntimes_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationRuntime = new AzureNative.DataFactory.IntegrationRuntime("integrationRuntime", new()
    {
        FactoryName = "exampleFactoryName",
        IntegrationRuntimeName = "exampleIntegrationRuntime",
        Properties = new AzureNative.DataFactory.Inputs.SelfHostedIntegrationRuntimeArgs
        {
            Description = "A selfhosted integration runtime",
            Type = "SelfHosted",
        },
        ResourceGroupName = "exampleResourceGroup",
    });

});


```

```go
package main

import (
	datafactory "github.com/pulumi/pulumi-azure-native-sdk/datafactory"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datafactory.NewIntegrationRuntime(ctx, "integrationRuntime", &datafactory.IntegrationRuntimeArgs{
			FactoryName:            pulumi.String("exampleFactoryName"),
			IntegrationRuntimeName: pulumi.String("exampleIntegrationRuntime"),
			Properties: datafactory.SelfHostedIntegrationRuntime{
				Description: "A selfhosted integration runtime",
				Type:        "SelfHosted",
			},
			ResourceGroupName: pulumi.String("exampleResourceGroup"),
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
import com.pulumi.azurenative.datafactory.IntegrationRuntime;
import com.pulumi.azurenative.datafactory.IntegrationRuntimeArgs;
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
            .factoryName("exampleFactoryName")
            .integrationRuntimeName("exampleIntegrationRuntime")
            .properties(Map.ofEntries(
                Map.entry("description", "A selfhosted integration runtime"),
                Map.entry("type", "SelfHosted")
            ))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationRuntime = new azure_native.datafactory.IntegrationRuntime("integrationRuntime", {
    factoryName: "exampleFactoryName",
    integrationRuntimeName: "exampleIntegrationRuntime",
    properties: {
        description: "A selfhosted integration runtime",
        type: "SelfHosted",
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_runtime = azure_native.datafactory.IntegrationRuntime("integrationRuntime",
    factory_name="exampleFactoryName",
    integration_runtime_name="exampleIntegrationRuntime",
    properties=azure_native.datafactory.SelfHostedIntegrationRuntimeArgs(
        description="A selfhosted integration runtime",
        type="SelfHosted",
    ),
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  integrationRuntime:
    type: azure-native:datafactory:IntegrationRuntime
    properties:
      factoryName: exampleFactoryName
      integrationRuntimeName: exampleIntegrationRuntime
      properties:
        description: A selfhosted integration runtime
        type: SelfHosted
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datafactory:IntegrationRuntime exampleIntegrationRuntime /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/integrationruntimes/exampleIntegrationRuntime 
```
