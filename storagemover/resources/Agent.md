The Agent resource.
API Version: 2023-03-01.
Previous API Version: 2022-07-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Agents_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agent = new AzureNative.StorageMover.Agent("agent", new()
    {
        AgentName = "examples-agentName",
        ArcResourceId = "/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.HybridCompute/machines/examples-hybridComputeName",
        ArcVmUuid = "3bb2c024-eba9-4d18-9e7a-1d772fcc5fe9",
        Description = "Example Agent Description",
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
		_, err := storagemover.NewAgent(ctx, "agent", &storagemover.AgentArgs{
			AgentName:         pulumi.String("examples-agentName"),
			ArcResourceId:     pulumi.String("/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.HybridCompute/machines/examples-hybridComputeName"),
			ArcVmUuid:         pulumi.String("3bb2c024-eba9-4d18-9e7a-1d772fcc5fe9"),
			Description:       pulumi.String("Example Agent Description"),
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
import com.pulumi.azurenative.storagemover.Agent;
import com.pulumi.azurenative.storagemover.AgentArgs;
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
        var agent = new Agent("agent", AgentArgs.builder()        
            .agentName("examples-agentName")
            .arcResourceId("/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.HybridCompute/machines/examples-hybridComputeName")
            .arcVmUuid("3bb2c024-eba9-4d18-9e7a-1d772fcc5fe9")
            .description("Example Agent Description")
            .resourceGroupName("examples-rg")
            .storageMoverName("examples-storageMoverName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agent = new azure_native.storagemover.Agent("agent", {
    agentName: "examples-agentName",
    arcResourceId: "/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.HybridCompute/machines/examples-hybridComputeName",
    arcVmUuid: "3bb2c024-eba9-4d18-9e7a-1d772fcc5fe9",
    description: "Example Agent Description",
    resourceGroupName: "examples-rg",
    storageMoverName: "examples-storageMoverName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent = azure_native.storagemover.Agent("agent",
    agent_name="examples-agentName",
    arc_resource_id="/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.HybridCompute/machines/examples-hybridComputeName",
    arc_vm_uuid="3bb2c024-eba9-4d18-9e7a-1d772fcc5fe9",
    description="Example Agent Description",
    resource_group_name="examples-rg",
    storage_mover_name="examples-storageMoverName")

```

```yaml
resources:
  agent:
    type: azure-native:storagemover:Agent
    properties:
      agentName: examples-agentName
      arcResourceId: /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.HybridCompute/machines/examples-hybridComputeName
      arcVmUuid: 3bb2c024-eba9-4d18-9e7a-1d772fcc5fe9
      description: Example Agent Description
      resourceGroupName: examples-rg
      storageMoverName: examples-storageMoverName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagemover:Agent examples-agentName /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.StorageMover/storageMovers/examples-storageMoverName/agents/examples-agentName 
```
