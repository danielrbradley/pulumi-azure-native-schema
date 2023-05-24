The Private Endpoint Connection resource.
API Version: 2021-11-01-preview.
Previous API Version: 2021-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update private endpoint connection.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.VideoAnalyzer.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        AccountName = "contososports",
        Name = "10000000-0000-0000-0000-000000000000",
        PrivateLinkServiceConnectionState = new AzureNative.VideoAnalyzer.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Test description.",
            Status = "Approved",
        },
        ResourceGroupName = "contoso",
    });

});


```

```go
package main

import (
	videoanalyzer "github.com/pulumi/pulumi-azure-native-sdk/videoanalyzer"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := videoanalyzer.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &videoanalyzer.PrivateEndpointConnectionArgs{
			AccountName: pulumi.String("contososports"),
			Name:        pulumi.String("10000000-0000-0000-0000-000000000000"),
			PrivateLinkServiceConnectionState: &videoanalyzer.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Test description."),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("contoso"),
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
import com.pulumi.azurenative.videoanalyzer.PrivateEndpointConnection;
import com.pulumi.azurenative.videoanalyzer.PrivateEndpointConnectionArgs;
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
            .accountName("contososports")
            .name("10000000-0000-0000-0000-000000000000")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Test description."),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("contoso")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.videoanalyzer.PrivateEndpointConnection("privateEndpointConnection", {
    accountName: "contososports",
    name: "10000000-0000-0000-0000-000000000000",
    privateLinkServiceConnectionState: {
        description: "Test description.",
        status: "Approved",
    },
    resourceGroupName: "contoso",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.videoanalyzer.PrivateEndpointConnection("privateEndpointConnection",
    account_name="contososports",
    name="10000000-0000-0000-0000-000000000000",
    private_link_service_connection_state=azure_native.videoanalyzer.PrivateLinkServiceConnectionStateArgs(
        description="Test description.",
        status="Approved",
    ),
    resource_group_name="contoso")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:videoanalyzer:PrivateEndpointConnection
    properties:
      accountName: contososports
      name: 10000000-0000-0000-0000-000000000000
      privateLinkServiceConnectionState:
        description: Test description.
        status: Approved
      resourceGroupName: contoso

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:videoanalyzer:PrivateEndpointConnection 10000000-0000-0000-0000-000000000000 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/fabrikam/providers/Microsoft.Media/videoanalyzers/contososports/privateEndpointConnections/10000000-0000-0000-0000-000000000000 
```
