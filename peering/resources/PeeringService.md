Peering Service
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a  peering service
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var peeringService = new AzureNative.Peering.PeeringService("peeringService", new()
    {
        Location = "eastus",
        PeeringServiceLocation = "state1",
        PeeringServiceName = "peeringServiceName",
        PeeringServiceProvider = "serviceProvider1",
        ProviderBackupPeeringLocation = "peeringLocation2",
        ProviderPrimaryPeeringLocation = "peeringLocation1",
        ResourceGroupName = "rgName",
    });

});


```

```go
package main

import (
	peering "github.com/pulumi/pulumi-azure-native-sdk/peering"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := peering.NewPeeringService(ctx, "peeringService", &peering.PeeringServiceArgs{
			Location:                       pulumi.String("eastus"),
			PeeringServiceLocation:         pulumi.String("state1"),
			PeeringServiceName:             pulumi.String("peeringServiceName"),
			PeeringServiceProvider:         pulumi.String("serviceProvider1"),
			ProviderBackupPeeringLocation:  pulumi.String("peeringLocation2"),
			ProviderPrimaryPeeringLocation: pulumi.String("peeringLocation1"),
			ResourceGroupName:              pulumi.String("rgName"),
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
import com.pulumi.azurenative.peering.PeeringService;
import com.pulumi.azurenative.peering.PeeringServiceArgs;
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
        var peeringService = new PeeringService("peeringService", PeeringServiceArgs.builder()        
            .location("eastus")
            .peeringServiceLocation("state1")
            .peeringServiceName("peeringServiceName")
            .peeringServiceProvider("serviceProvider1")
            .providerBackupPeeringLocation("peeringLocation2")
            .providerPrimaryPeeringLocation("peeringLocation1")
            .resourceGroupName("rgName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const peeringService = new azure_native.peering.PeeringService("peeringService", {
    location: "eastus",
    peeringServiceLocation: "state1",
    peeringServiceName: "peeringServiceName",
    peeringServiceProvider: "serviceProvider1",
    providerBackupPeeringLocation: "peeringLocation2",
    providerPrimaryPeeringLocation: "peeringLocation1",
    resourceGroupName: "rgName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

peering_service = azure_native.peering.PeeringService("peeringService",
    location="eastus",
    peering_service_location="state1",
    peering_service_name="peeringServiceName",
    peering_service_provider="serviceProvider1",
    provider_backup_peering_location="peeringLocation2",
    provider_primary_peering_location="peeringLocation1",
    resource_group_name="rgName")

```

```yaml
resources:
  peeringService:
    type: azure-native:peering:PeeringService
    properties:
      location: eastus
      peeringServiceLocation: state1
      peeringServiceName: peeringServiceName
      peeringServiceProvider: serviceProvider1
      providerBackupPeeringLocation: peeringLocation2
      providerPrimaryPeeringLocation: peeringLocation1
      resourceGroupName: rgName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:peering:PeeringService peeringServiceName /subscriptions/subId/resourceGroups/rgName/providers/Microsoft.Peering/peeringServices/peeringServiceName 
```
