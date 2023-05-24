A Database Migration Service resource
API Version: 2021-06-30.
Previous API Version: 2018-04-19. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Services_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.DataMigration.Service("service", new()
    {
        GroupName = "DmsSdkRg",
        Location = "southcentralus",
        ServiceName = "DmsSdkService",
        Sku = new AzureNative.DataMigration.Inputs.ServiceSkuArgs
        {
            Name = "Basic_1vCore",
        },
        VirtualSubnetId = "/subscriptions/fc04246f-04c5-437e-ac5e-206a19e7193f/resourceGroups/DmsSdkTestNetwork/providers/Microsoft.Network/virtualNetworks/DmsSdkTestNetwork/subnets/default",
    });

});


```

```go
package main

import (
	datamigration "github.com/pulumi/pulumi-azure-native-sdk/datamigration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datamigration.NewService(ctx, "service", &datamigration.ServiceArgs{
			GroupName:   pulumi.String("DmsSdkRg"),
			Location:    pulumi.String("southcentralus"),
			ServiceName: pulumi.String("DmsSdkService"),
			Sku: &datamigration.ServiceSkuArgs{
				Name: pulumi.String("Basic_1vCore"),
			},
			VirtualSubnetId: pulumi.String("/subscriptions/fc04246f-04c5-437e-ac5e-206a19e7193f/resourceGroups/DmsSdkTestNetwork/providers/Microsoft.Network/virtualNetworks/DmsSdkTestNetwork/subnets/default"),
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
import com.pulumi.azurenative.datamigration.Service;
import com.pulumi.azurenative.datamigration.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .groupName("DmsSdkRg")
            .location("southcentralus")
            .serviceName("DmsSdkService")
            .sku(Map.of("name", "Basic_1vCore"))
            .virtualSubnetId("/subscriptions/fc04246f-04c5-437e-ac5e-206a19e7193f/resourceGroups/DmsSdkTestNetwork/providers/Microsoft.Network/virtualNetworks/DmsSdkTestNetwork/subnets/default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.datamigration.Service("service", {
    groupName: "DmsSdkRg",
    location: "southcentralus",
    serviceName: "DmsSdkService",
    sku: {
        name: "Basic_1vCore",
    },
    virtualSubnetId: "/subscriptions/fc04246f-04c5-437e-ac5e-206a19e7193f/resourceGroups/DmsSdkTestNetwork/providers/Microsoft.Network/virtualNetworks/DmsSdkTestNetwork/subnets/default",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.datamigration.Service("service",
    group_name="DmsSdkRg",
    location="southcentralus",
    service_name="DmsSdkService",
    sku=azure_native.datamigration.ServiceSkuArgs(
        name="Basic_1vCore",
    ),
    virtual_subnet_id="/subscriptions/fc04246f-04c5-437e-ac5e-206a19e7193f/resourceGroups/DmsSdkTestNetwork/providers/Microsoft.Network/virtualNetworks/DmsSdkTestNetwork/subnets/default")

```

```yaml
resources:
  service:
    type: azure-native:datamigration:Service
    properties:
      groupName: DmsSdkRg
      location: southcentralus
      serviceName: DmsSdkService
      sku:
        name: Basic_1vCore
      virtualSubnetId: /subscriptions/fc04246f-04c5-437e-ac5e-206a19e7193f/resourceGroups/DmsSdkTestNetwork/providers/Microsoft.Network/virtualNetworks/DmsSdkTestNetwork/subnets/default

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datamigration:Service DmsSdkService /subscriptions/fc04246f-04c5-437e-ac5e-206a19e7193f/resourceGroups/DmsSdkRg/providers/Microsoft.DataMigration/services/DmsSdkService 
```
