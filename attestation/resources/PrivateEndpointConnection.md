The Private Endpoint Connection resource.
API Version: 2020-10-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AttestationProviderPutPrivateEndpointConnection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Attestation.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "{privateEndpointConnectionName}",
        PrivateLinkServiceConnectionState = new AzureNative.Attestation.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Auto-Approved",
            Status = "Approved",
        },
        ProviderName = "sto9699",
        ResourceGroupName = "res7687",
    });

});


```

```go
package main

import (
	attestation "github.com/pulumi/pulumi-azure-native-sdk/attestation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := attestation.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &attestation.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("{privateEndpointConnectionName}"),
			PrivateLinkServiceConnectionState: &attestation.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Auto-Approved"),
				Status:      pulumi.String("Approved"),
			},
			ProviderName:      pulumi.String("sto9699"),
			ResourceGroupName: pulumi.String("res7687"),
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
import com.pulumi.azurenative.attestation.PrivateEndpointConnection;
import com.pulumi.azurenative.attestation.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("{privateEndpointConnectionName}")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Auto-Approved"),
                Map.entry("status", "Approved")
            ))
            .providerName("sto9699")
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.attestation.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "{privateEndpointConnectionName}",
    privateLinkServiceConnectionState: {
        description: "Auto-Approved",
        status: "Approved",
    },
    providerName: "sto9699",
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.attestation.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="{privateEndpointConnectionName}",
    private_link_service_connection_state=azure_native.attestation.PrivateLinkServiceConnectionStateArgs(
        description="Auto-Approved",
        status="Approved",
    ),
    provider_name="sto9699",
    resource_group_name="res7687")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:attestation:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: '{privateEndpointConnectionName}'
      privateLinkServiceConnectionState:
        description: Auto-Approved
        status: Approved
      providerName: sto9699
      resourceGroupName: res7687

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:attestation:PrivateEndpointConnection {privateEndpointConnectionName} /subscriptions/{subscription-id}/resourceGroups/res7231/providers/Microsoft.Attestation/attestationProviders/sto288/privateEndpointConnections/{privateEndpointConnectionName} 
```
