Describes an existing Private Endpoint connection to the Azure Cognitive Search service.
API Version: 2022-09-01.
Previous API Version: 2020-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnectionUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Search.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "testEndpoint.50bf4fbe-d7c1-4b48-a642-4f5892642546",
        Properties = new AzureNative.Search.Inputs.PrivateEndpointConnectionPropertiesArgs
        {
            PrivateLinkServiceConnectionState = new AzureNative.Search.Inputs.PrivateEndpointConnectionPropertiesPrivateLinkServiceConnectionStateArgs
            {
                Description = "Rejected for some reason",
                Status = AzureNative.Search.PrivateLinkServiceConnectionStatus.Rejected,
            },
        },
        ResourceGroupName = "rg1",
        SearchServiceName = "mysearchservice",
    });

});


```

```go
package main

import (
	search "github.com/pulumi/pulumi-azure-native-sdk/search"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := search.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &search.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("testEndpoint.50bf4fbe-d7c1-4b48-a642-4f5892642546"),
			Properties: search.PrivateEndpointConnectionPropertiesResponse{
				PrivateLinkServiceConnectionState: &search.PrivateEndpointConnectionPropertiesPrivateLinkServiceConnectionStateArgs{
					Description: pulumi.String("Rejected for some reason"),
					Status:      search.PrivateLinkServiceConnectionStatusRejected,
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			SearchServiceName: pulumi.String("mysearchservice"),
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
import com.pulumi.azurenative.search.PrivateEndpointConnection;
import com.pulumi.azurenative.search.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("testEndpoint.50bf4fbe-d7c1-4b48-a642-4f5892642546")
            .properties(Map.of("privateLinkServiceConnectionState", Map.ofEntries(
                Map.entry("description", "Rejected for some reason"),
                Map.entry("status", "Rejected")
            )))
            .resourceGroupName("rg1")
            .searchServiceName("mysearchservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.search.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "testEndpoint.50bf4fbe-d7c1-4b48-a642-4f5892642546",
    properties: {
        privateLinkServiceConnectionState: {
            description: "Rejected for some reason",
            status: azure_native.search.PrivateLinkServiceConnectionStatus.Rejected,
        },
    },
    resourceGroupName: "rg1",
    searchServiceName: "mysearchservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.search.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="testEndpoint.50bf4fbe-d7c1-4b48-a642-4f5892642546",
    properties=azure_native.search.PrivateEndpointConnectionPropertiesResponseArgs(
        private_link_service_connection_state=azure_native.search.PrivateEndpointConnectionPropertiesPrivateLinkServiceConnectionStateArgs(
            description="Rejected for some reason",
            status=azure_native.search.PrivateLinkServiceConnectionStatus.REJECTED,
        ),
    ),
    resource_group_name="rg1",
    search_service_name="mysearchservice")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:search:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: testEndpoint.50bf4fbe-d7c1-4b48-a642-4f5892642546
      properties:
        privateLinkServiceConnectionState:
          description: Rejected for some reason
          status: Rejected
      resourceGroupName: rg1
      searchServiceName: mysearchservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:search:PrivateEndpointConnection testEndpoint.50bf4fbe-d7c1-4b48-a642-4f5892642546 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Search/searchServices/mysearchservice/privateEndpointConnections/testEndpoint.50bf4fbe-d7c1-4b48-a642-4f5892642546 
```
