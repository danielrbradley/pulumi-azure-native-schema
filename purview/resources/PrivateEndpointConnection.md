A private endpoint connection class.
API Version: 2021-07-01.
Previous API Version: 2020-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnections_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Purview.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        AccountName = "account1",
        PrivateEndpointConnectionName = "privateEndpointConnection1",
        PrivateLinkServiceConnectionState = new AzureNative.Purview.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Approved by johndoe@company.com",
            Status = "Approved",
        },
        ResourceGroupName = "SampleResourceGroup",
    });

});


```

```go
package main

import (
	purview "github.com/pulumi/pulumi-azure-native-sdk/purview"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := purview.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &purview.PrivateEndpointConnectionArgs{
			AccountName:                   pulumi.String("account1"),
			PrivateEndpointConnectionName: pulumi.String("privateEndpointConnection1"),
			PrivateLinkServiceConnectionState: &purview.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Approved by johndoe@company.com"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("SampleResourceGroup"),
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
import com.pulumi.azurenative.purview.PrivateEndpointConnection;
import com.pulumi.azurenative.purview.PrivateEndpointConnectionArgs;
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
            .accountName("account1")
            .privateEndpointConnectionName("privateEndpointConnection1")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Approved by johndoe@company.com"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("SampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.purview.PrivateEndpointConnection("privateEndpointConnection", {
    accountName: "account1",
    privateEndpointConnectionName: "privateEndpointConnection1",
    privateLinkServiceConnectionState: {
        description: "Approved by johndoe@company.com",
        status: "Approved",
    },
    resourceGroupName: "SampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.purview.PrivateEndpointConnection("privateEndpointConnection",
    account_name="account1",
    private_endpoint_connection_name="privateEndpointConnection1",
    private_link_service_connection_state=azure_native.purview.PrivateLinkServiceConnectionStateArgs(
        description="Approved by johndoe@company.com",
        status="Approved",
    ),
    resource_group_name="SampleResourceGroup")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:purview:PrivateEndpointConnection
    properties:
      accountName: account1
      privateEndpointConnectionName: privateEndpointConnection1
      privateLinkServiceConnectionState:
        description: Approved by johndoe@company.com
        status: Approved
      resourceGroupName: SampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:purview:PrivateEndpointConnection privateEndpointConnection1 /subscriptions/12345678-1234-1234-12345678abc/resourceGroups/SampleResourceGroup/providers/Microsoft.Purview/accounts/account1/privateEndpointConnections/privateEndpointConnection1 
```
