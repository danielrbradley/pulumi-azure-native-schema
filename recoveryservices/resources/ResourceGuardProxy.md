
API Version: 2023-02-01.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var resourceGuardProxy = new AzureNative.RecoveryServices.ResourceGuardProxy("resourceGuardProxy", new()
    {
        Properties = new AzureNative.RecoveryServices.Inputs.ResourceGuardProxyBaseArgs
        {
            ResourceGuardResourceId = "/subscriptions/c999d45b-944f-418c-a0d8-c3fcfd1802c8/resourceGroups/vaultguardRGNew/providers/Microsoft.DataProtection/resourceGuards/VaultGuardTestNew",
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
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewResourceGuardProxy(ctx, "resourceGuardProxy", &recoveryservices.ResourceGuardProxyArgs{
			Properties: &recoveryservices.ResourceGuardProxyBaseArgs{
				ResourceGuardResourceId: pulumi.String("/subscriptions/c999d45b-944f-418c-a0d8-c3fcfd1802c8/resourceGroups/vaultguardRGNew/providers/Microsoft.DataProtection/resourceGuards/VaultGuardTestNew"),
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
import com.pulumi.azurenative.recoveryservices.ResourceGuardProxy;
import com.pulumi.azurenative.recoveryservices.ResourceGuardProxyArgs;
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
        var resourceGuardProxy = new ResourceGuardProxy("resourceGuardProxy", ResourceGuardProxyArgs.builder()        
            .properties(Map.of("resourceGuardResourceId", "/subscriptions/c999d45b-944f-418c-a0d8-c3fcfd1802c8/resourceGroups/vaultguardRGNew/providers/Microsoft.DataProtection/resourceGuards/VaultGuardTestNew"))
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

const resourceGuardProxy = new azure_native.recoveryservices.ResourceGuardProxy("resourceGuardProxy", {
    properties: {
        resourceGuardResourceId: "/subscriptions/c999d45b-944f-418c-a0d8-c3fcfd1802c8/resourceGroups/vaultguardRGNew/providers/Microsoft.DataProtection/resourceGuards/VaultGuardTestNew",
    },
    resourceGroupName: "SampleResourceGroup",
    resourceGuardProxyName: "swaggerExample",
    vaultName: "sampleVault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

resource_guard_proxy = azure_native.recoveryservices.ResourceGuardProxy("resourceGuardProxy",
    properties=azure_native.recoveryservices.ResourceGuardProxyBaseArgs(
        resource_guard_resource_id="/subscriptions/c999d45b-944f-418c-a0d8-c3fcfd1802c8/resourceGroups/vaultguardRGNew/providers/Microsoft.DataProtection/resourceGuards/VaultGuardTestNew",
    ),
    resource_group_name="SampleResourceGroup",
    resource_guard_proxy_name="swaggerExample",
    vault_name="sampleVault")

```

```yaml
resources:
  resourceGuardProxy:
    type: azure-native:recoveryservices:ResourceGuardProxy
    properties:
      properties:
        resourceGuardResourceId: /subscriptions/c999d45b-944f-418c-a0d8-c3fcfd1802c8/resourceGroups/vaultguardRGNew/providers/Microsoft.DataProtection/resourceGuards/VaultGuardTestNew
      resourceGroupName: SampleResourceGroup
      resourceGuardProxyName: swaggerExample
      vaultName: sampleVault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ResourceGuardProxy swaggerExample /backupmanagement/resources/sampleVault/backupResourceGuardProxies/swaggerExample 
```
