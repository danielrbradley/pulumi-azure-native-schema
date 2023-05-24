The Private Endpoint Connection resource.
API Version: 2021-03-25-preview.
Previous API Version: 2021-03-25-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var privateEndpointConnectionsSec = new AzureNative.M365SecurityAndCompliance.PrivateEndpointConnectionsSec("privateEndpointConnectionsSec", new()
    {
        PrivateEndpointConnectionName = "myConnection",
        PrivateLinkServiceConnectionState = new AzureNative.M365SecurityAndCompliance.Inputs.PrivateLinkServiceConnectionStateArgs
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
	m365securityandcompliance "github.com/pulumi/pulumi-azure-native-sdk/m365securityandcompliance"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := m365securityandcompliance.NewPrivateEndpointConnectionsSec(ctx, "privateEndpointConnectionsSec", &m365securityandcompliance.PrivateEndpointConnectionsSecArgs{
			PrivateEndpointConnectionName: pulumi.String("myConnection"),
			PrivateLinkServiceConnectionState: &m365securityandcompliance.PrivateLinkServiceConnectionStateArgs{
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
import com.pulumi.azurenative.m365securityandcompliance.PrivateEndpointConnectionsSec;
import com.pulumi.azurenative.m365securityandcompliance.PrivateEndpointConnectionsSecArgs;
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
        var privateEndpointConnectionsSec = new PrivateEndpointConnectionsSec("privateEndpointConnectionsSec", PrivateEndpointConnectionsSecArgs.builder()        
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

const privateEndpointConnectionsSec = new azure_native.m365securityandcompliance.PrivateEndpointConnectionsSec("privateEndpointConnectionsSec", {
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

private_endpoint_connections_sec = azure_native.m365securityandcompliance.PrivateEndpointConnectionsSec("privateEndpointConnectionsSec",
    private_endpoint_connection_name="myConnection",
    private_link_service_connection_state=azure_native.m365securityandcompliance.PrivateLinkServiceConnectionStateArgs(
        description="Auto-Approved",
        status="Approved",
    ),
    resource_group_name="rgname",
    resource_name_="service1")

```

```yaml
resources:
  privateEndpointConnectionsSec:
    type: azure-native:m365securityandcompliance:PrivateEndpointConnectionsSec
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
$ pulumi import azure-native:m365securityandcompliance:PrivateEndpointConnectionsSec myConnection /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.M365SecurityAndCompliance/privateLinkServicesForM365SecurityCenter/service1/privateEndpointConnections/myConnection 
```
