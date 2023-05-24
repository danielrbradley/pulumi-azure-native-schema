The Private Endpoint Connection resource.
API Version: 2021-03-08.
Previous API Version: 2021-03-08. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnection_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnectionsForMIPPolicySync = new AzureNative.SecurityAndCompliance.PrivateEndpointConnectionsForMIPPolicySync("privateEndpointConnectionsForMIPPolicySync", new()
    {
        PrivateEndpointConnectionName = "myConnection",
        PrivateLinkServiceConnectionState = new AzureNative.SecurityAndCompliance.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Auto-Approved",
            Status = "Approved",
        },
        ResourceGroupName = "rgname",
        ResourceName = "service1",
    });

});


```

```go
package main

import (
	securityandcompliance "github.com/pulumi/pulumi-azure-native-sdk/securityandcompliance"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityandcompliance.NewPrivateEndpointConnectionsForMIPPolicySync(ctx, "privateEndpointConnectionsForMIPPolicySync", &securityandcompliance.PrivateEndpointConnectionsForMIPPolicySyncArgs{
			PrivateEndpointConnectionName: pulumi.String("myConnection"),
			PrivateLinkServiceConnectionState: &securityandcompliance.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Auto-Approved"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("rgname"),
			ResourceName:      pulumi.String("service1"),
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
import com.pulumi.azurenative.securityandcompliance.PrivateEndpointConnectionsForMIPPolicySync;
import com.pulumi.azurenative.securityandcompliance.PrivateEndpointConnectionsForMIPPolicySyncArgs;
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
        var privateEndpointConnectionsForMIPPolicySync = new PrivateEndpointConnectionsForMIPPolicySync("privateEndpointConnectionsForMIPPolicySync", PrivateEndpointConnectionsForMIPPolicySyncArgs.builder()        
            .privateEndpointConnectionName("myConnection")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Auto-Approved"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("rgname")
            .resourceName("service1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnectionsForMIPPolicySync = new azure_native.securityandcompliance.PrivateEndpointConnectionsForMIPPolicySync("privateEndpointConnectionsForMIPPolicySync", {
    privateEndpointConnectionName: "myConnection",
    privateLinkServiceConnectionState: {
        description: "Auto-Approved",
        status: "Approved",
    },
    resourceGroupName: "rgname",
    resourceName: "service1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connections_for_mip_policy_sync = azure_native.securityandcompliance.PrivateEndpointConnectionsForMIPPolicySync("privateEndpointConnectionsForMIPPolicySync",
    private_endpoint_connection_name="myConnection",
    private_link_service_connection_state=azure_native.securityandcompliance.PrivateLinkServiceConnectionStateArgs(
        description="Auto-Approved",
        status="Approved",
    ),
    resource_group_name="rgname",
    resource_name_="service1")

```

```yaml
resources:
  privateEndpointConnectionsForMIPPolicySync:
    type: azure-native:securityandcompliance:PrivateEndpointConnectionsForMIPPolicySync
    properties:
      privateEndpointConnectionName: myConnection
      privateLinkServiceConnectionState:
        description: Auto-Approved
        status: Approved
      resourceGroupName: rgname
      resourceName: service1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityandcompliance:PrivateEndpointConnectionsForMIPPolicySync myConnection /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.SecurityAndCompliance/privateLinkServicesForMIPPolicySync/service1/privateEndpointConnections/myConnection 
```
