The Private Endpoint Connection resource.
API Version: 2022-08-01.
Previous API Version: 2021-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementApproveOrRejectPrivateEndpointConnection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnectionByName = new AzureNative.ApiManagement.PrivateEndpointConnectionByName("privateEndpointConnectionByName", new()
    {
        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/privateEndpointConnections/connectionName",
        PrivateEndpointConnectionName = "privateEndpointConnectionName",
        Properties = new AzureNative.ApiManagement.Inputs.PrivateEndpointConnectionRequestPropertiesArgs
        {
            PrivateLinkServiceConnectionState = new AzureNative.ApiManagement.Inputs.PrivateLinkServiceConnectionStateArgs
            {
                Description = "The Private Endpoint Connection is approved.",
                Status = "Approved",
            },
        },
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewPrivateEndpointConnectionByName(ctx, "privateEndpointConnectionByName", &apimanagement.PrivateEndpointConnectionByNameArgs{
			Id:                            pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/privateEndpointConnections/connectionName"),
			PrivateEndpointConnectionName: pulumi.String("privateEndpointConnectionName"),
			Properties: &apimanagement.PrivateEndpointConnectionRequestPropertiesArgs{
				PrivateLinkServiceConnectionState: &apimanagement.PrivateLinkServiceConnectionStateArgs{
					Description: pulumi.String("The Private Endpoint Connection is approved."),
					Status:      pulumi.String("Approved"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.PrivateEndpointConnectionByName;
import com.pulumi.azurenative.apimanagement.PrivateEndpointConnectionByNameArgs;
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
        var privateEndpointConnectionByName = new PrivateEndpointConnectionByName("privateEndpointConnectionByName", PrivateEndpointConnectionByNameArgs.builder()        
            .id("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/privateEndpointConnections/connectionName")
            .privateEndpointConnectionName("privateEndpointConnectionName")
            .properties(Map.of("privateLinkServiceConnectionState", Map.ofEntries(
                Map.entry("description", "The Private Endpoint Connection is approved."),
                Map.entry("status", "Approved")
            )))
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnectionByName = new azure_native.apimanagement.PrivateEndpointConnectionByName("privateEndpointConnectionByName", {
    id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/privateEndpointConnections/connectionName",
    privateEndpointConnectionName: "privateEndpointConnectionName",
    properties: {
        privateLinkServiceConnectionState: {
            description: "The Private Endpoint Connection is approved.",
            status: "Approved",
        },
    },
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection_by_name = azure_native.apimanagement.PrivateEndpointConnectionByName("privateEndpointConnectionByName",
    id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/privateEndpointConnections/connectionName",
    private_endpoint_connection_name="privateEndpointConnectionName",
    properties=azure_native.apimanagement.PrivateEndpointConnectionRequestPropertiesArgs(
        private_link_service_connection_state=azure_native.apimanagement.PrivateLinkServiceConnectionStateArgs(
            description="The Private Endpoint Connection is approved.",
            status="Approved",
        ),
    ),
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  privateEndpointConnectionByName:
    type: azure-native:apimanagement:PrivateEndpointConnectionByName
    properties:
      id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/privateEndpointConnections/connectionName
      privateEndpointConnectionName: privateEndpointConnectionName
      properties:
        privateLinkServiceConnectionState:
          description: The Private Endpoint Connection is approved.
          status: Approved
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:PrivateEndpointConnectionByName privateEndpointConnectionName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/privateEndpointConnections/privateEndpointConnectionName 
```
