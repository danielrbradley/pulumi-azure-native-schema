A private endpoint connection
API Version: 2020-10-30-preview.
Previous API Version: 2020-10-30-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Approve or reject a private endpoint connection with a given name.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.PowerPlatform.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        EnterprisePolicyName = "ddb1",
        PrivateEndpointConnectionName = "privateEndpointConnectionName",
        PrivateLinkServiceConnectionState = new AzureNative.PowerPlatform.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Approved by johndoe@contoso.com",
            Status = "Approved",
        },
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	powerplatform "github.com/pulumi/pulumi-azure-native-sdk/powerplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := powerplatform.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &powerplatform.PrivateEndpointConnectionArgs{
			EnterprisePolicyName:          pulumi.String("ddb1"),
			PrivateEndpointConnectionName: pulumi.String("privateEndpointConnectionName"),
			PrivateLinkServiceConnectionState: &powerplatform.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Approved by johndoe@contoso.com"),
				Status:      pulumi.String("Approved"),
			},
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
import com.pulumi.azurenative.powerplatform.PrivateEndpointConnection;
import com.pulumi.azurenative.powerplatform.PrivateEndpointConnectionArgs;
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
        var privateEndpointConnection = new PrivateEndpointConnection("privateEndpointConnection", PrivateEndpointConnectionArgs.builder()        
            .enterprisePolicyName("ddb1")
            .privateEndpointConnectionName("privateEndpointConnectionName")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Approved by johndoe@contoso.com"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.powerplatform.PrivateEndpointConnection("privateEndpointConnection", {
    enterprisePolicyName: "ddb1",
    privateEndpointConnectionName: "privateEndpointConnectionName",
    privateLinkServiceConnectionState: {
        description: "Approved by johndoe@contoso.com",
        status: "Approved",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.powerplatform.PrivateEndpointConnection("privateEndpointConnection",
    enterprise_policy_name="ddb1",
    private_endpoint_connection_name="privateEndpointConnectionName",
    private_link_service_connection_state=azure_native.powerplatform.PrivateLinkServiceConnectionStateArgs(
        description="Approved by johndoe@contoso.com",
        status="Approved",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:powerplatform:PrivateEndpointConnection
    properties:
      enterprisePolicyName: ddb1
      privateEndpointConnectionName: privateEndpointConnectionName
      privateLinkServiceConnectionState:
        description: Approved by johndoe@contoso.com
        status: Approved
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:powerplatform:PrivateEndpointConnection privateEndpointConnectionName /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/rg1/providers/Microsoft.PowerPlatform/enterprisePolicies/ddb1/privateEndpointConnections/privateEndpointConnectionName 
```
