The private endpoint connection resource.
API Version: 2021-09-01-preview.

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
    var privateEndpointConnection = new AzureNative.AgFoodPlatform.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        FarmBeatsResourceName = "examples-farmbeatsResourceName",
        PrivateEndpointConnectionName = "privateEndpointConnectionName",
        PrivateLinkServiceConnectionState = new AzureNative.AgFoodPlatform.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Approved by johndoe@contoso.com",
            Status = "Approved",
        },
        ResourceGroupName = "examples-rg",
    });

});


```

```go
package main

import (
	agfoodplatform "github.com/pulumi/pulumi-azure-native-sdk/agfoodplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := agfoodplatform.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &agfoodplatform.PrivateEndpointConnectionArgs{
			FarmBeatsResourceName:         pulumi.String("examples-farmbeatsResourceName"),
			PrivateEndpointConnectionName: pulumi.String("privateEndpointConnectionName"),
			PrivateLinkServiceConnectionState: &agfoodplatform.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Approved by johndoe@contoso.com"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("examples-rg"),
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
import com.pulumi.azurenative.agfoodplatform.PrivateEndpointConnection;
import com.pulumi.azurenative.agfoodplatform.PrivateEndpointConnectionArgs;
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
            .farmBeatsResourceName("examples-farmbeatsResourceName")
            .privateEndpointConnectionName("privateEndpointConnectionName")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Approved by johndoe@contoso.com"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("examples-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.agfoodplatform.PrivateEndpointConnection("privateEndpointConnection", {
    farmBeatsResourceName: "examples-farmbeatsResourceName",
    privateEndpointConnectionName: "privateEndpointConnectionName",
    privateLinkServiceConnectionState: {
        description: "Approved by johndoe@contoso.com",
        status: "Approved",
    },
    resourceGroupName: "examples-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.agfoodplatform.PrivateEndpointConnection("privateEndpointConnection",
    farm_beats_resource_name="examples-farmbeatsResourceName",
    private_endpoint_connection_name="privateEndpointConnectionName",
    private_link_service_connection_state=azure_native.agfoodplatform.PrivateLinkServiceConnectionStateArgs(
        description="Approved by johndoe@contoso.com",
        status="Approved",
    ),
    resource_group_name="examples-rg")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:agfoodplatform:PrivateEndpointConnection
    properties:
      farmBeatsResourceName: examples-farmbeatsResourceName
      privateEndpointConnectionName: privateEndpointConnectionName
      privateLinkServiceConnectionState:
        description: Approved by johndoe@contoso.com
        status: Approved
      resourceGroupName: examples-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:agfoodplatform:PrivateEndpointConnection privateEndpointConnectionName /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/examples-rg/providers/Microsoft.AgFoodPlatform/farmBeats/examples-farmbeatsResourceName/privateEndpointConnections/privateEndpointConnectionName 
```
