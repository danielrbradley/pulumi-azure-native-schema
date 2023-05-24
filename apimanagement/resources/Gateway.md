Gateway details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateGateway
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gateway = new AzureNative.ApiManagement.Gateway("gateway", new()
    {
        Description = "my gateway 1",
        GatewayId = "gw1",
        LocationData = new AzureNative.ApiManagement.Inputs.ResourceLocationDataContractArgs
        {
            Name = "my location",
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
		_, err := apimanagement.NewGateway(ctx, "gateway", &apimanagement.GatewayArgs{
			Description: pulumi.String("my gateway 1"),
			GatewayId:   pulumi.String("gw1"),
			LocationData: &apimanagement.ResourceLocationDataContractArgs{
				Name: pulumi.String("my location"),
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
import com.pulumi.azurenative.apimanagement.Gateway;
import com.pulumi.azurenative.apimanagement.GatewayArgs;
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
        var gateway = new Gateway("gateway", GatewayArgs.builder()        
            .description("my gateway 1")
            .gatewayId("gw1")
            .locationData(Map.of("name", "my location"))
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gateway = new azure_native.apimanagement.Gateway("gateway", {
    description: "my gateway 1",
    gatewayId: "gw1",
    locationData: {
        name: "my location",
    },
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gateway = azure_native.apimanagement.Gateway("gateway",
    description="my gateway 1",
    gateway_id="gw1",
    location_data=azure_native.apimanagement.ResourceLocationDataContractArgs(
        name="my location",
    ),
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  gateway:
    type: azure-native:apimanagement:Gateway
    properties:
      description: my gateway 1
      gatewayId: gw1
      locationData:
        name: my location
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Gateway a1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/gateways/gw1 
```
