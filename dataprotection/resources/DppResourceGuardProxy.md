ResourceGuardProxyBaseResource object, used for response and request bodies for ResourceGuardProxy APIs
API Version: 2023-01-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create ResourceGuardProxy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dppResourceGuardProxy = new AzureNative.DataProtection.DppResourceGuardProxy("dppResourceGuardProxy", new()
    {
        Properties = new AzureNative.DataProtection.Inputs.ResourceGuardProxyBaseArgs
        {
            ResourceGuardResourceId = "/subscriptions/f9e67185-f313-4e79-aa71-6458d429369d/resourceGroups/ResourceGuardSecurityAdminRG/providers/Microsoft.DataProtection/resourceGuards/ResourceGuardTestResource",
        },
        ResourceGroupName = "SampleResourceGroup",
        ResourceGuardProxyName = "swaggerExample",
        VaultName = "sampleVault",
    });

});


```

```go
package main

import (
	dataprotection "github.com/pulumi/pulumi-azure-native-sdk/dataprotection"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dataprotection.NewDppResourceGuardProxy(ctx, "dppResourceGuardProxy", &dataprotection.DppResourceGuardProxyArgs{
			Properties: &dataprotection.ResourceGuardProxyBaseArgs{
				ResourceGuardResourceId: pulumi.String("/subscriptions/f9e67185-f313-4e79-aa71-6458d429369d/resourceGroups/ResourceGuardSecurityAdminRG/providers/Microsoft.DataProtection/resourceGuards/ResourceGuardTestResource"),
			},
			ResourceGroupName:      pulumi.String("SampleResourceGroup"),
			ResourceGuardProxyName: pulumi.String("swaggerExample"),
			VaultName:              pulumi.String("sampleVault"),
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
import com.pulumi.azurenative.dataprotection.DppResourceGuardProxy;
import com.pulumi.azurenative.dataprotection.DppResourceGuardProxyArgs;
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
        var dppResourceGuardProxy = new DppResourceGuardProxy("dppResourceGuardProxy", DppResourceGuardProxyArgs.builder()        
            .properties(Map.of("resourceGuardResourceId", "/subscriptions/f9e67185-f313-4e79-aa71-6458d429369d/resourceGroups/ResourceGuardSecurityAdminRG/providers/Microsoft.DataProtection/resourceGuards/ResourceGuardTestResource"))
            .resourceGroupName("SampleResourceGroup")
            .resourceGuardProxyName("swaggerExample")
            .vaultName("sampleVault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dppResourceGuardProxy = new azure_native.dataprotection.DppResourceGuardProxy("dppResourceGuardProxy", {
    properties: {
        resourceGuardResourceId: "/subscriptions/f9e67185-f313-4e79-aa71-6458d429369d/resourceGroups/ResourceGuardSecurityAdminRG/providers/Microsoft.DataProtection/resourceGuards/ResourceGuardTestResource",
    },
    resourceGroupName: "SampleResourceGroup",
    resourceGuardProxyName: "swaggerExample",
    vaultName: "sampleVault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dpp_resource_guard_proxy = azure_native.dataprotection.DppResourceGuardProxy("dppResourceGuardProxy",
    properties=azure_native.dataprotection.ResourceGuardProxyBaseArgs(
        resource_guard_resource_id="/subscriptions/f9e67185-f313-4e79-aa71-6458d429369d/resourceGroups/ResourceGuardSecurityAdminRG/providers/Microsoft.DataProtection/resourceGuards/ResourceGuardTestResource",
    ),
    resource_group_name="SampleResourceGroup",
    resource_guard_proxy_name="swaggerExample",
    vault_name="sampleVault")

```

```yaml
resources:
  dppResourceGuardProxy:
    type: azure-native:dataprotection:DppResourceGuardProxy
    properties:
      properties:
        resourceGuardResourceId: /subscriptions/f9e67185-f313-4e79-aa71-6458d429369d/resourceGroups/ResourceGuardSecurityAdminRG/providers/Microsoft.DataProtection/resourceGuards/ResourceGuardTestResource
      resourceGroupName: SampleResourceGroup
      resourceGuardProxyName: swaggerExample
      vaultName: sampleVault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dataprotection:DppResourceGuardProxy swaggerExample /subscriptions/5e13b949-1218-4d18-8b99-7e12155ec4f7/resourceGroups/SampleResourceGroup/providers/Microsoft.DataProtection/backupVaults/sampleVault/backupResourceGuardProxies/swaggerExample 
```
