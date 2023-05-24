Private Endpoint Connection Response Properties
API Version: 2023-02-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update PrivateEndpointConnection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.RecoveryServices.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "gaallatestpe2.5704c932-249a-490b-a142-1396838cd3b",
        Properties = new AzureNative.RecoveryServices.Inputs.PrivateEndpointConnectionArgs
        {
            GroupIds = new[]
            {
                "AzureBackup_secondary",
            },
            PrivateEndpoint = new AzureNative.RecoveryServices.Inputs.PrivateEndpointArgs
            {
                Id = "/subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/gaallaRG/providers/Microsoft.Network/privateEndpoints/gaallatestpe3",
            },
            PrivateLinkServiceConnectionState = new AzureNative.RecoveryServices.Inputs.PrivateLinkServiceConnectionStateArgs
            {
                Description = "Approved by johndoe@company.com",
                Status = "Approved",
            },
            ProvisioningState = "Succeeded",
        },
        ResourceGroupName = "gaallaRG",
        VaultName = "gaallavaultbvtd2msi",
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
		_, err := recoveryservices.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &recoveryservices.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("gaallatestpe2.5704c932-249a-490b-a142-1396838cd3b"),
			Properties: recoveryservices.PrivateEndpointConnectionResponse{
				GroupIds: pulumi.StringArray{
					pulumi.String("AzureBackup_secondary"),
				},
				PrivateEndpoint: &recoveryservices.PrivateEndpointArgs{
					Id: pulumi.String("/subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/gaallaRG/providers/Microsoft.Network/privateEndpoints/gaallatestpe3"),
				},
				PrivateLinkServiceConnectionState: &recoveryservices.PrivateLinkServiceConnectionStateArgs{
					Description: pulumi.String("Approved by johndoe@company.com"),
					Status:      pulumi.String("Approved"),
				},
				ProvisioningState: pulumi.String("Succeeded"),
			},
			ResourceGroupName: pulumi.String("gaallaRG"),
			VaultName:         pulumi.String("gaallavaultbvtd2msi"),
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
import com.pulumi.azurenative.recoveryservices.PrivateEndpointConnection;
import com.pulumi.azurenative.recoveryservices.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("gaallatestpe2.5704c932-249a-490b-a142-1396838cd3b")
            .properties(Map.ofEntries(
                Map.entry("groupIds", "AzureBackup_secondary"),
                Map.entry("privateEndpoint", Map.of("id", "/subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/gaallaRG/providers/Microsoft.Network/privateEndpoints/gaallatestpe3")),
                Map.entry("privateLinkServiceConnectionState", Map.ofEntries(
                    Map.entry("description", "Approved by johndoe@company.com"),
                    Map.entry("status", "Approved")
                )),
                Map.entry("provisioningState", "Succeeded")
            ))
            .resourceGroupName("gaallaRG")
            .vaultName("gaallavaultbvtd2msi")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.recoveryservices.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "gaallatestpe2.5704c932-249a-490b-a142-1396838cd3b",
    properties: {
        groupIds: ["AzureBackup_secondary"],
        privateEndpoint: {
            id: "/subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/gaallaRG/providers/Microsoft.Network/privateEndpoints/gaallatestpe3",
        },
        privateLinkServiceConnectionState: {
            description: "Approved by johndoe@company.com",
            status: "Approved",
        },
        provisioningState: "Succeeded",
    },
    resourceGroupName: "gaallaRG",
    vaultName: "gaallavaultbvtd2msi",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.recoveryservices.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="gaallatestpe2.5704c932-249a-490b-a142-1396838cd3b",
    properties=azure_native.recoveryservices.PrivateEndpointConnectionResponseArgs(
        group_ids=["AzureBackup_secondary"],
        private_endpoint=azure_native.recoveryservices.PrivateEndpointArgs(
            id="/subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/gaallaRG/providers/Microsoft.Network/privateEndpoints/gaallatestpe3",
        ),
        private_link_service_connection_state=azure_native.recoveryservices.PrivateLinkServiceConnectionStateArgs(
            description="Approved by johndoe@company.com",
            status="Approved",
        ),
        provisioning_state="Succeeded",
    ),
    resource_group_name="gaallaRG",
    vault_name="gaallavaultbvtd2msi")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:recoveryservices:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: gaallatestpe2.5704c932-249a-490b-a142-1396838cd3b
      properties:
        groupIds:
          - AzureBackup_secondary
        privateEndpoint:
          id: /subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/gaallaRG/providers/Microsoft.Network/privateEndpoints/gaallatestpe3
        privateLinkServiceConnectionState:
          description: Approved by johndoe@company.com
          status: Approved
        provisioningState: Succeeded
      resourceGroupName: gaallaRG
      vaultName: gaallavaultbvtd2msi

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:PrivateEndpointConnection gaallatestpe1.3592346090307038890.backup.5704c932-249a-490b-a142-1396838cd3b /subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/gaallaRG/providers/Microsoft.RecoveryServicesBVTD2/vaults/gaallavaultbvtd2msi/privateEndpointConnections/gaallatestpe3.3592346090307038890.backup.5704c932-249a-490b-a142-1396838cd3b 
```
