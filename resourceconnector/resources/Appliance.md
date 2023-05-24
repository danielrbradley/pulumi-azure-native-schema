Appliances definition.
API Version: 2022-10-27.
Previous API Version: 2021-10-31-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create/Update Appliance
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var appliance = new AzureNative.ResourceConnector.Appliance("appliance", new()
    {
        Distro = "AKSEdge",
        InfrastructureConfig = new AzureNative.ResourceConnector.Inputs.AppliancePropertiesInfrastructureConfigArgs
        {
            Provider = "VMWare",
        },
        Location = "West US",
        ResourceGroupName = "testresourcegroup",
        ResourceName = "appliance01",
    });

});


```

```go
package main

import (
	resourceconnector "github.com/pulumi/pulumi-azure-native-sdk/resourceconnector"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resourceconnector.NewAppliance(ctx, "appliance", &resourceconnector.ApplianceArgs{
			Distro: pulumi.String("AKSEdge"),
			InfrastructureConfig: &resourceconnector.AppliancePropertiesInfrastructureConfigArgs{
				Provider: pulumi.String("VMWare"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("testresourcegroup"),
			ResourceName:      pulumi.String("appliance01"),
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
import com.pulumi.azurenative.resourceconnector.Appliance;
import com.pulumi.azurenative.resourceconnector.ApplianceArgs;
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
        var appliance = new Appliance("appliance", ApplianceArgs.builder()        
            .distro("AKSEdge")
            .infrastructureConfig(Map.of("provider", "VMWare"))
            .location("West US")
            .resourceGroupName("testresourcegroup")
            .resourceName("appliance01")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const appliance = new azure_native.resourceconnector.Appliance("appliance", {
    distro: "AKSEdge",
    infrastructureConfig: {
        provider: "VMWare",
    },
    location: "West US",
    resourceGroupName: "testresourcegroup",
    resourceName: "appliance01",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

appliance = azure_native.resourceconnector.Appliance("appliance",
    distro="AKSEdge",
    infrastructure_config=azure_native.resourceconnector.AppliancePropertiesInfrastructureConfigArgs(
        provider="VMWare",
    ),
    location="West US",
    resource_group_name="testresourcegroup",
    resource_name_="appliance01")

```

```yaml
resources:
  appliance:
    type: azure-native:resourceconnector:Appliance
    properties:
      distro: AKSEdge
      infrastructureConfig:
        provider: VMWare
      location: West US
      resourceGroupName: testresourcegroup
      resourceName: appliance01

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resourceconnector:Appliance appliance01 /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/testrg/providers/Microsoft.ResourceConnector/appliances/appliance01 
```
