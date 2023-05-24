Authorization in an ExpressRouteCircuit resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create ExpressRouteCircuit Authorization
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var expressRouteCircuitAuthorization = new AzureNative.Network.ExpressRouteCircuitAuthorization("expressRouteCircuitAuthorization", new()
    {
        AuthorizationName = "authorizatinName",
        CircuitName = "circuitName",
        ResourceGroupName = "rg1",
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
		_, err := network.NewExpressRouteCircuitAuthorization(ctx, "expressRouteCircuitAuthorization", &network.ExpressRouteCircuitAuthorizationArgs{
			AuthorizationName: pulumi.String("authorizatinName"),
			CircuitName:       pulumi.String("circuitName"),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.ExpressRouteCircuitAuthorization;
import com.pulumi.azurenative.network.ExpressRouteCircuitAuthorizationArgs;
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
        var expressRouteCircuitAuthorization = new ExpressRouteCircuitAuthorization("expressRouteCircuitAuthorization", ExpressRouteCircuitAuthorizationArgs.builder()        
            .authorizationName("authorizatinName")
            .circuitName("circuitName")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const expressRouteCircuitAuthorization = new azure_native.network.ExpressRouteCircuitAuthorization("expressRouteCircuitAuthorization", {
    authorizationName: "authorizatinName",
    circuitName: "circuitName",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

express_route_circuit_authorization = azure_native.network.ExpressRouteCircuitAuthorization("expressRouteCircuitAuthorization",
    authorization_name="authorizatinName",
    circuit_name="circuitName",
    resource_group_name="rg1")

```

```yaml
resources:
  expressRouteCircuitAuthorization:
    type: azure-native:network:ExpressRouteCircuitAuthorization
    properties:
      authorizationName: authorizatinName
      circuitName: circuitName
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ExpressRouteCircuitAuthorization authorizationName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteCircuits/circuitName/authorizations/authorizationName 
```
