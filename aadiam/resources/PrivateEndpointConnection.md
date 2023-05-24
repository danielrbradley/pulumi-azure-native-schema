Private endpoint connection resource.
API Version: 2020-03-01.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AadiamPutPrivateEndpointConnection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.AadIam.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PolicyName = "example-policy-5849",
        PrivateEndpoint = new AzureNative.AadIam.Inputs.PrivateEndpointArgs
        {
            Id = "subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/microsoft.aadiam/privateLinkForAzureAD/ddb1/privateLinkConnections/{privateEndpointConnection name}",
        },
        PrivateEndpointConnectionName = "{privateEndpointConnection name}",
        PrivateLinkServiceConnectionState = new AzureNative.AadIam.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            ActionsRequired = "None",
            Description = "You may pass",
            Status = "Approved",
        },
        ResourceGroupName = "resourcegroup",
    });

});


```

```go
package main

import (
	aadiam "github.com/pulumi/pulumi-azure-native-sdk/aadiam"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := aadiam.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &aadiam.PrivateEndpointConnectionArgs{
			PolicyName: pulumi.String("example-policy-5849"),
			PrivateEndpoint: &aadiam.PrivateEndpointArgs{
				Id: pulumi.String("subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/microsoft.aadiam/privateLinkForAzureAD/ddb1/privateLinkConnections/{privateEndpointConnection name}"),
			},
			PrivateEndpointConnectionName: pulumi.String("{privateEndpointConnection name}"),
			PrivateLinkServiceConnectionState: &aadiam.PrivateLinkServiceConnectionStateArgs{
				ActionsRequired: pulumi.String("None"),
				Description:     pulumi.String("You may pass"),
				Status:          pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("resourcegroup"),
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
import com.pulumi.azurenative.aadiam.PrivateEndpointConnection;
import com.pulumi.azurenative.aadiam.PrivateEndpointConnectionArgs;
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
            .policyName("example-policy-5849")
            .privateEndpoint(Map.of("id", "subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/microsoft.aadiam/privateLinkForAzureAD/ddb1/privateLinkConnections/{privateEndpointConnection name}"))
            .privateEndpointConnectionName("{privateEndpointConnection name}")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("actionsRequired", "None"),
                Map.entry("description", "You may pass"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("resourcegroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.aadiam.PrivateEndpointConnection("privateEndpointConnection", {
    policyName: "example-policy-5849",
    privateEndpoint: {
        id: "subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/microsoft.aadiam/privateLinkForAzureAD/ddb1/privateLinkConnections/{privateEndpointConnection name}",
    },
    privateEndpointConnectionName: "{privateEndpointConnection name}",
    privateLinkServiceConnectionState: {
        actionsRequired: "None",
        description: "You may pass",
        status: "Approved",
    },
    resourceGroupName: "resourcegroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.aadiam.PrivateEndpointConnection("privateEndpointConnection",
    policy_name="example-policy-5849",
    private_endpoint=azure_native.aadiam.PrivateEndpointArgs(
        id="subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/microsoft.aadiam/privateLinkForAzureAD/ddb1/privateLinkConnections/{privateEndpointConnection name}",
    ),
    private_endpoint_connection_name="{privateEndpointConnection name}",
    private_link_service_connection_state=azure_native.aadiam.PrivateLinkServiceConnectionStateArgs(
        actions_required="None",
        description="You may pass",
        status="Approved",
    ),
    resource_group_name="resourcegroup")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:aadiam:PrivateEndpointConnection
    properties:
      policyName: example-policy-5849
      privateEndpoint:
        id: subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/microsoft.aadiam/privateLinkForAzureAD/ddb1/privateLinkConnections/{privateEndpointConnection name}
      privateEndpointConnectionName: '{privateEndpointConnection name}'
      privateLinkServiceConnectionState:
        actionsRequired: None
        description: You may pass
        status: Approved
      resourceGroupName: resourcegroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:aadiam:PrivateEndpointConnection {privateEndpointConnection name} subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/microsoft.aadiam/privateLinkForAzureAD/ddb1/privateLinkConnections/{privateEndpointConnection name} 
```
