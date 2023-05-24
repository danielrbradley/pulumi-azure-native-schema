The agentPool resource definition
API Version: 2022-09-01-preview.
Previous API Version: 2022-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutAgentPool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var agentPool = new AzureNative.HybridContainerService.AgentPool("agentPool", new()
    {
        AgentPoolName = "test-hybridaksnodepool",
        Count = 1,
        Location = "westus",
        OsType = "Linux",
        ResourceGroupName = "test-arcappliance-resgrp",
        ResourceName = "test-hybridakscluster",
        VmSize = "Standard_A4_v2",
    });

});


```

```go
package main

import (
	hybridcontainerservice "github.com/pulumi/pulumi-azure-native-sdk/hybridcontainerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridcontainerservice.NewAgentPool(ctx, "agentPool", &hybridcontainerservice.AgentPoolArgs{
			AgentPoolName:     pulumi.String("test-hybridaksnodepool"),
			Count:             pulumi.Int(1),
			Location:          pulumi.String("westus"),
			OsType:            pulumi.String("Linux"),
			ResourceGroupName: pulumi.String("test-arcappliance-resgrp"),
			ResourceName:      pulumi.String("test-hybridakscluster"),
			VmSize:            pulumi.String("Standard_A4_v2"),
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
import com.pulumi.azurenative.hybridcontainerservice.AgentPool;
import com.pulumi.azurenative.hybridcontainerservice.AgentPoolArgs;
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
        var agentPool = new AgentPool("agentPool", AgentPoolArgs.builder()        
            .agentPoolName("test-hybridaksnodepool")
            .count(1)
            .location("westus")
            .osType("Linux")
            .resourceGroupName("test-arcappliance-resgrp")
            .resourceName("test-hybridakscluster")
            .vmSize("Standard_A4_v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const agentPool = new azure_native.hybridcontainerservice.AgentPool("agentPool", {
    agentPoolName: "test-hybridaksnodepool",
    count: 1,
    location: "westus",
    osType: "Linux",
    resourceGroupName: "test-arcappliance-resgrp",
    resourceName: "test-hybridakscluster",
    vmSize: "Standard_A4_v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

agent_pool = azure_native.hybridcontainerservice.AgentPool("agentPool",
    agent_pool_name="test-hybridaksnodepool",
    count=1,
    location="westus",
    os_type="Linux",
    resource_group_name="test-arcappliance-resgrp",
    resource_name_="test-hybridakscluster",
    vm_size="Standard_A4_v2")

```

```yaml
resources:
  agentPool:
    type: azure-native:hybridcontainerservice:AgentPool
    properties:
      agentPoolName: test-hybridaksnodepool
      count: 1
      location: westus
      osType: Linux
      resourceGroupName: test-arcappliance-resgrp
      resourceName: test-hybridakscluster
      vmSize: Standard_A4_v2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridcontainerservice:AgentPool test-hybridaksnodepool /subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/provisionedClusters/test-hybridakscluster/agentPools/test-hybridaksnodepool 
```
