Private endpoint connection resource.
API Version: 2023-02-01.
Previous API Version: 2019-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### KeyVaultPutPrivateEndpointConnection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.KeyVault.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "sample-pec",
        PrivateLinkServiceConnectionState = new AzureNative.KeyVault.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "My name is Joe and I'm approving this.",
            Status = "Approved",
        },
        ResourceGroupName = "sample-group",
        VaultName = "sample-vault",
    });

});


```

```go
package main

import (
	keyvault "github.com/pulumi/pulumi-azure-native-sdk/keyvault"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := keyvault.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &keyvault.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("sample-pec"),
			PrivateLinkServiceConnectionState: &keyvault.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("My name is Joe and I'm approving this."),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("sample-group"),
			VaultName:         pulumi.String("sample-vault"),
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
import com.pulumi.azurenative.keyvault.PrivateEndpointConnection;
import com.pulumi.azurenative.keyvault.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("sample-pec")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "My name is Joe and I'm approving this."),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("sample-group")
            .vaultName("sample-vault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.keyvault.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "sample-pec",
    privateLinkServiceConnectionState: {
        description: "My name is Joe and I'm approving this.",
        status: "Approved",
    },
    resourceGroupName: "sample-group",
    vaultName: "sample-vault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.keyvault.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="sample-pec",
    private_link_service_connection_state=azure_native.keyvault.PrivateLinkServiceConnectionStateArgs(
        description="My name is Joe and I'm approving this.",
        status="Approved",
    ),
    resource_group_name="sample-group",
    vault_name="sample-vault")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:keyvault:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: sample-pec
      privateLinkServiceConnectionState:
        description: My name is Joe and I'm approving this.
        status: Approved
      resourceGroupName: sample-group
      vaultName: sample-vault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:keyvault:PrivateEndpointConnection sample-pec /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/sample-group/providers/Microsoft.KeyVault/vaults/sample-vault/privateEndpointConnections/sample-pec 
```
