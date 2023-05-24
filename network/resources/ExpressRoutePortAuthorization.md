ExpressRoutePort Authorization resource definition.
API Version: 2022-09-01.
Previous API Version: 2022-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create ExpressRoutePort Authorization
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var expressRoutePortAuthorization = new AzureNative.Network.ExpressRoutePortAuthorization("expressRoutePortAuthorization", new()
    {
        AuthorizationName = "authorizatinName",
        ExpressRoutePortName = "expressRoutePortName",
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
		_, err := network.NewExpressRoutePortAuthorization(ctx, "expressRoutePortAuthorization", &network.ExpressRoutePortAuthorizationArgs{
			AuthorizationName:    pulumi.String("authorizatinName"),
			ExpressRoutePortName: pulumi.String("expressRoutePortName"),
			ResourceGroupName:    pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.ExpressRoutePortAuthorization;
import com.pulumi.azurenative.network.ExpressRoutePortAuthorizationArgs;
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
        var expressRoutePortAuthorization = new ExpressRoutePortAuthorization("expressRoutePortAuthorization", ExpressRoutePortAuthorizationArgs.builder()        
            .authorizationName("authorizatinName")
            .expressRoutePortName("expressRoutePortName")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const expressRoutePortAuthorization = new azure_native.network.ExpressRoutePortAuthorization("expressRoutePortAuthorization", {
    authorizationName: "authorizatinName",
    expressRoutePortName: "expressRoutePortName",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

express_route_port_authorization = azure_native.network.ExpressRoutePortAuthorization("expressRoutePortAuthorization",
    authorization_name="authorizatinName",
    express_route_port_name="expressRoutePortName",
    resource_group_name="rg1")

```

```yaml
resources:
  expressRoutePortAuthorization:
    type: azure-native:network:ExpressRoutePortAuthorization
    properties:
      authorizationName: authorizatinName
      expressRoutePortName: expressRoutePortName
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ExpressRoutePortAuthorization authorizationName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/ExpressRoutePorts/expressRoutePortName/authorizations/authorizationName 
```
