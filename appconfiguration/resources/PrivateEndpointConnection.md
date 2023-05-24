A private endpoint connection
API Version: 2022-05-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnection_Update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.AppConfiguration.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        ConfigStoreName = "contoso",
        PrivateEndpointConnectionName = "myConnection",
        PrivateLinkServiceConnectionState = new AzureNative.AppConfiguration.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Auto-Approved",
            Status = "Approved",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	appconfiguration "github.com/pulumi/pulumi-azure-native-sdk/appconfiguration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appconfiguration.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &appconfiguration.PrivateEndpointConnectionArgs{
			ConfigStoreName:               pulumi.String("contoso"),
			PrivateEndpointConnectionName: pulumi.String("myConnection"),
			PrivateLinkServiceConnectionState: &appconfiguration.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Auto-Approved"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.appconfiguration.PrivateEndpointConnection;
import com.pulumi.azurenative.appconfiguration.PrivateEndpointConnectionArgs;
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
            .configStoreName("contoso")
            .privateEndpointConnectionName("myConnection")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Auto-Approved"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.appconfiguration.PrivateEndpointConnection("privateEndpointConnection", {
    configStoreName: "contoso",
    privateEndpointConnectionName: "myConnection",
    privateLinkServiceConnectionState: {
        description: "Auto-Approved",
        status: "Approved",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.appconfiguration.PrivateEndpointConnection("privateEndpointConnection",
    config_store_name="contoso",
    private_endpoint_connection_name="myConnection",
    private_link_service_connection_state=azure_native.appconfiguration.PrivateLinkServiceConnectionStateArgs(
        description="Auto-Approved",
        status="Approved",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:appconfiguration:PrivateEndpointConnection
    properties:
      configStoreName: contoso
      privateEndpointConnectionName: myConnection
      privateLinkServiceConnectionState:
        description: Auto-Approved
        status: Approved
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appconfiguration:PrivateEndpointConnection myConnection /subscriptions/c80fb759-c965-4c6a-9110-9b2b2d038882/resourceGroups/myResourceGroup/providers/Microsoft.AppConfiguration/configurationStores/contoso/privateEndpointConnections/myConnection 
```
