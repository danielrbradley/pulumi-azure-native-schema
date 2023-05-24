The Private Endpoint Connection resource.
API Version: 2022-12-01.
Previous API Version: 2022-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var privateEndpointConnection = new AzureNative.HealthcareApis.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "myConnection",
        PrivateLinkServiceConnectionState = new AzureNative.HealthcareApis.Inputs.PrivateLinkServiceConnectionStateArgs
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
	healthcareapis "github.com/pulumi/pulumi-azure-native-sdk/healthcareapis"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := healthcareapis.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &healthcareapis.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("myConnection"),
			PrivateLinkServiceConnectionState: &healthcareapis.PrivateLinkServiceConnectionStateArgs{
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
import com.pulumi.azurenative.healthcareapis.PrivateEndpointConnection;
import com.pulumi.azurenative.healthcareapis.PrivateEndpointConnectionArgs;
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

const privateEndpointConnection = new azure_native.healthcareapis.PrivateEndpointConnection("privateEndpointConnection", {
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

private_endpoint_connection = azure_native.healthcareapis.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="myConnection",
    private_link_service_connection_state=azure_native.healthcareapis.PrivateLinkServiceConnectionStateArgs(
        description="Auto-Approved",
        status="Approved",
    ),
    resource_group_name="rgname",
    resource_name_="service1")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:healthcareapis:PrivateEndpointConnection
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
$ pulumi import azure-native:healthcareapis:PrivateEndpointConnection myConnection /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.HealthcareApis/services/service1/privateEndpointConnections/myConnection 
```
