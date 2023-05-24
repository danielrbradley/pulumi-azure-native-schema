The Scope Connections resource
API Version: 2022-09-01.
Previous API Version: 2022-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Network Manager Scope Connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scopeConnection = new AzureNative.Network.ScopeConnection("scopeConnection", new()
    {
        Description = "This is a scope connection to a cross tenant subscription.",
        NetworkManagerName = "testNetworkManager",
        ResourceGroupName = "rg1",
        ResourceId = "subscriptions/f0dc2b34-dfad-40e4-83e0-2309fed8d00b",
        ScopeConnectionName = "TestScopeConnection",
        TenantId = "6babcaad-604b-40ac-a9d7-9fd97c0b779f",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewScopeConnection(ctx, "scopeConnection", &network.ScopeConnectionArgs{
			Description:         pulumi.String("This is a scope connection to a cross tenant subscription."),
			NetworkManagerName:  pulumi.String("testNetworkManager"),
			ResourceGroupName:   pulumi.String("rg1"),
			ResourceId:          pulumi.String("subscriptions/f0dc2b34-dfad-40e4-83e0-2309fed8d00b"),
			ScopeConnectionName: pulumi.String("TestScopeConnection"),
			TenantId:            pulumi.String("6babcaad-604b-40ac-a9d7-9fd97c0b779f"),
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
import com.pulumi.azurenative.network.ScopeConnection;
import com.pulumi.azurenative.network.ScopeConnectionArgs;
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
        var scopeConnection = new ScopeConnection("scopeConnection", ScopeConnectionArgs.builder()        
            .description("This is a scope connection to a cross tenant subscription.")
            .networkManagerName("testNetworkManager")
            .resourceGroupName("rg1")
            .resourceId("subscriptions/f0dc2b34-dfad-40e4-83e0-2309fed8d00b")
            .scopeConnectionName("TestScopeConnection")
            .tenantId("6babcaad-604b-40ac-a9d7-9fd97c0b779f")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scopeConnection = new azure_native.network.ScopeConnection("scopeConnection", {
    description: "This is a scope connection to a cross tenant subscription.",
    networkManagerName: "testNetworkManager",
    resourceGroupName: "rg1",
    resourceId: "subscriptions/f0dc2b34-dfad-40e4-83e0-2309fed8d00b",
    scopeConnectionName: "TestScopeConnection",
    tenantId: "6babcaad-604b-40ac-a9d7-9fd97c0b779f",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scope_connection = azure_native.network.ScopeConnection("scopeConnection",
    description="This is a scope connection to a cross tenant subscription.",
    network_manager_name="testNetworkManager",
    resource_group_name="rg1",
    resource_id="subscriptions/f0dc2b34-dfad-40e4-83e0-2309fed8d00b",
    scope_connection_name="TestScopeConnection",
    tenant_id="6babcaad-604b-40ac-a9d7-9fd97c0b779f")

```

```yaml
resources:
  scopeConnection:
    type: azure-native:network:ScopeConnection
    properties:
      description: This is a scope connection to a cross tenant subscription.
      networkManagerName: testNetworkManager
      resourceGroupName: rg1
      resourceId: subscriptions/f0dc2b34-dfad-40e4-83e0-2309fed8d00b
      scopeConnectionName: TestScopeConnection
      tenantId: 6babcaad-604b-40ac-a9d7-9fd97c0b779f

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ScopeConnection TestScopeConnection /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroup/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager/scopeConnections/TestScopeConnection 
```
