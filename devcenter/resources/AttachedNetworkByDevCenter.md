Represents an attached NetworkConnection.
API Version: 2022-11-11-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AttachedNetworks_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var attachedNetworkByDevCenter = new AzureNative.DevCenter.AttachedNetworkByDevCenter("attachedNetworkByDevCenter", new()
    {
        AttachedNetworkConnectionName = "network-uswest3",
        DevCenterName = "Contoso",
        NetworkConnectionId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/NetworkConnections/network-uswest3",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	devcenter "github.com/pulumi/pulumi-azure-native-sdk/devcenter"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devcenter.NewAttachedNetworkByDevCenter(ctx, "attachedNetworkByDevCenter", &devcenter.AttachedNetworkByDevCenterArgs{
			AttachedNetworkConnectionName: pulumi.String("network-uswest3"),
			DevCenterName:                 pulumi.String("Contoso"),
			NetworkConnectionId:           pulumi.String("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/NetworkConnections/network-uswest3"),
			ResourceGroupName:             pulumi.String("rg1"),
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
import com.pulumi.azurenative.devcenter.AttachedNetworkByDevCenter;
import com.pulumi.azurenative.devcenter.AttachedNetworkByDevCenterArgs;
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
        var attachedNetworkByDevCenter = new AttachedNetworkByDevCenter("attachedNetworkByDevCenter", AttachedNetworkByDevCenterArgs.builder()        
            .attachedNetworkConnectionName("network-uswest3")
            .devCenterName("Contoso")
            .networkConnectionId("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/NetworkConnections/network-uswest3")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const attachedNetworkByDevCenter = new azure_native.devcenter.AttachedNetworkByDevCenter("attachedNetworkByDevCenter", {
    attachedNetworkConnectionName: "network-uswest3",
    devCenterName: "Contoso",
    networkConnectionId: "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/NetworkConnections/network-uswest3",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

attached_network_by_dev_center = azure_native.devcenter.AttachedNetworkByDevCenter("attachedNetworkByDevCenter",
    attached_network_connection_name="network-uswest3",
    dev_center_name="Contoso",
    network_connection_id="/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/NetworkConnections/network-uswest3",
    resource_group_name="rg1")

```

```yaml
resources:
  attachedNetworkByDevCenter:
    type: azure-native:devcenter:AttachedNetworkByDevCenter
    properties:
      attachedNetworkConnectionName: network-uswest3
      devCenterName: Contoso
      networkConnectionId: /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/NetworkConnections/network-uswest3
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devcenter:AttachedNetworkByDevCenter network-uswest3 /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso/attachednetworks/network-uswest3 
```
