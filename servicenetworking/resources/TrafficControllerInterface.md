Concrete tracked resource types can be created by aliasing this type using a specific property type.
API Version: 2022-10-01-preview.
Previous API Version: 2022-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put Traffic Controller
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var trafficControllerInterface = new AzureNative.ServiceNetworking.TrafficControllerInterface("trafficControllerInterface", new()
    {
        Location = "NorthCentralUS",
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "value1" },
        },
        TrafficControllerName = "tc1",
    });

});


```

```go
package main

import (
	servicenetworking "github.com/pulumi/pulumi-azure-native-sdk/servicenetworking"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicenetworking.NewTrafficControllerInterface(ctx, "trafficControllerInterface", &servicenetworking.TrafficControllerInterfaceArgs{
			Location:          pulumi.String("NorthCentralUS"),
			ResourceGroupName: pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			TrafficControllerName: pulumi.String("tc1"),
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
import com.pulumi.azurenative.servicenetworking.TrafficControllerInterface;
import com.pulumi.azurenative.servicenetworking.TrafficControllerInterfaceArgs;
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
        var trafficControllerInterface = new TrafficControllerInterface("trafficControllerInterface", TrafficControllerInterfaceArgs.builder()        
            .location("NorthCentralUS")
            .resourceGroupName("rg1")
            .tags(Map.of("key1", "value1"))
            .trafficControllerName("tc1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const trafficControllerInterface = new azure_native.servicenetworking.TrafficControllerInterface("trafficControllerInterface", {
    location: "NorthCentralUS",
    resourceGroupName: "rg1",
    tags: {
        key1: "value1",
    },
    trafficControllerName: "tc1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

traffic_controller_interface = azure_native.servicenetworking.TrafficControllerInterface("trafficControllerInterface",
    location="NorthCentralUS",
    resource_group_name="rg1",
    tags={
        "key1": "value1",
    },
    traffic_controller_name="tc1")

```

```yaml
resources:
  trafficControllerInterface:
    type: azure-native:servicenetworking:TrafficControllerInterface
    properties:
      location: NorthCentralUS
      resourceGroupName: rg1
      tags:
        key1: value1
      trafficControllerName: tc1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicenetworking:TrafficControllerInterface tc1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ServiceNetworking/trafficControllers/tc1 
```
