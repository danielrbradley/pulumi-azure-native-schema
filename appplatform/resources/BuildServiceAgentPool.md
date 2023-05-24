The build service agent pool resource
API Version: 2022-12-01.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### BuildServiceAgentPool_UpdatePut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var buildServiceAgentPool = new AzureNative.AppPlatform.BuildServiceAgentPool("buildServiceAgentPool", new()
    {
        AgentPoolName = "default",
        BuildServiceName = "default",
        Properties = new AzureNative.AppPlatform.Inputs.BuildServiceAgentPoolPropertiesArgs
        {
            PoolSize = new AzureNative.AppPlatform.Inputs.BuildServiceAgentPoolSizePropertiesArgs
            {
                Name = "S3",
            },
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
    });

});


```

```go
package main

import (
	appplatform "github.com/pulumi/pulumi-azure-native-sdk/appplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appplatform.NewBuildServiceAgentPool(ctx, "buildServiceAgentPool", &appplatform.BuildServiceAgentPoolArgs{
			AgentPoolName:    pulumi.String("default"),
			BuildServiceName: pulumi.String("default"),
			Properties: appplatform.BuildServiceAgentPoolPropertiesResponse{
				PoolSize: &appplatform.BuildServiceAgentPoolSizePropertiesArgs{
					Name: pulumi.String("S3"),
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ServiceName:       pulumi.String("myservice"),
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
import com.pulumi.azurenative.appplatform.BuildServiceAgentPool;
import com.pulumi.azurenative.appplatform.BuildServiceAgentPoolArgs;
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
        var buildServiceAgentPool = new BuildServiceAgentPool("buildServiceAgentPool", BuildServiceAgentPoolArgs.builder()        
            .agentPoolName("default")
            .buildServiceName("default")
            .properties(Map.of("poolSize", Map.of("name", "S3")))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const buildServiceAgentPool = new azure_native.appplatform.BuildServiceAgentPool("buildServiceAgentPool", {
    agentPoolName: "default",
    buildServiceName: "default",
    properties: {
        poolSize: {
            name: "S3",
        },
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

build_service_agent_pool = azure_native.appplatform.BuildServiceAgentPool("buildServiceAgentPool",
    agent_pool_name="default",
    build_service_name="default",
    properties=azure_native.appplatform.BuildServiceAgentPoolPropertiesResponseArgs(
        pool_size=azure_native.appplatform.BuildServiceAgentPoolSizePropertiesArgs(
            name="S3",
        ),
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  buildServiceAgentPool:
    type: azure-native:appplatform:BuildServiceAgentPool
    properties:
      agentPoolName: default
      buildServiceName: default
      properties:
        poolSize:
          name: S3
      resourceGroupName: myResourceGroup
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:BuildServiceAgentPool default /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/buildServices/default/agentPools/default 
```
