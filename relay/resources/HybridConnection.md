Description of hybrid connection resource.
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RelayHybridConnectionCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hybridConnection = new AzureNative.Relay.HybridConnection("hybridConnection", new()
    {
        HybridConnectionName = "example-Relay-Hybrid-01",
        NamespaceName = "example-RelayNamespace-01",
        RequiresClientAuthorization = true,
        ResourceGroupName = "resourcegroup",
    });

});


```

```go
package main

import (
	relay "github.com/pulumi/pulumi-azure-native-sdk/relay"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := relay.NewHybridConnection(ctx, "hybridConnection", &relay.HybridConnectionArgs{
			HybridConnectionName:        pulumi.String("example-Relay-Hybrid-01"),
			NamespaceName:               pulumi.String("example-RelayNamespace-01"),
			RequiresClientAuthorization: pulumi.Bool(true),
			ResourceGroupName:           pulumi.String("resourcegroup"),
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
import com.pulumi.azurenative.relay.HybridConnection;
import com.pulumi.azurenative.relay.HybridConnectionArgs;
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
        var hybridConnection = new HybridConnection("hybridConnection", HybridConnectionArgs.builder()        
            .hybridConnectionName("example-Relay-Hybrid-01")
            .namespaceName("example-RelayNamespace-01")
            .requiresClientAuthorization(true)
            .resourceGroupName("resourcegroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hybridConnection = new azure_native.relay.HybridConnection("hybridConnection", {
    hybridConnectionName: "example-Relay-Hybrid-01",
    namespaceName: "example-RelayNamespace-01",
    requiresClientAuthorization: true,
    resourceGroupName: "resourcegroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hybrid_connection = azure_native.relay.HybridConnection("hybridConnection",
    hybrid_connection_name="example-Relay-Hybrid-01",
    namespace_name="example-RelayNamespace-01",
    requires_client_authorization=True,
    resource_group_name="resourcegroup")

```

```yaml
resources:
  hybridConnection:
    type: azure-native:relay:HybridConnection
    properties:
      hybridConnectionName: example-Relay-Hybrid-01
      namespaceName: example-RelayNamespace-01
      requiresClientAuthorization: true
      resourceGroupName: resourcegroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:relay:HybridConnection example-Relay-Hybrid-01 /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/resourcegroup/providers/Microsoft.Relay/namespaces/example-RelayNamespace-01/HybridConnections/example-Relay-Hybrid-01 
```
