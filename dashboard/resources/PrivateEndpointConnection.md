The Private Endpoint Connection resource.
API Version: 2022-08-01.
Previous API Version: 2022-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnections_Approve
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Dashboard.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "myConnection",
        ResourceGroupName = "myResourceGroup",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	dashboard "github.com/pulumi/pulumi-azure-native-sdk/dashboard"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dashboard.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &dashboard.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("myConnection"),
			ResourceGroupName:             pulumi.String("myResourceGroup"),
			WorkspaceName:                 pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.dashboard.PrivateEndpointConnection;
import com.pulumi.azurenative.dashboard.PrivateEndpointConnectionArgs;
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
            .resourceGroupName("myResourceGroup")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.dashboard.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "myConnection",
    resourceGroupName: "myResourceGroup",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.dashboard.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="myConnection",
    resource_group_name="myResourceGroup",
    workspace_name="myWorkspace")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:dashboard:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: myConnection
      resourceGroupName: myResourceGroup
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dashboard:PrivateEndpointConnection myConnection /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/Microsoft.Dashboard/grafana/myWorkspace/privateEndpointConnections/myConnection 
```
