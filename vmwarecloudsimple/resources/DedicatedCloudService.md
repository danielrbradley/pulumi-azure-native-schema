Dedicated cloud service model
API Version: 2019-04-01.
Previous API Version: 2019-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateDedicatedCloudService
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dedicatedCloudService = new AzureNative.VMwareCloudSimple.DedicatedCloudService("dedicatedCloudService", new()
    {
        DedicatedCloudServiceName = "myService",
        GatewaySubnet = "10.0.0.0",
        Location = "westus",
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	vmwarecloudsimple "github.com/pulumi/pulumi-azure-native-sdk/vmwarecloudsimple"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := vmwarecloudsimple.NewDedicatedCloudService(ctx, "dedicatedCloudService", &vmwarecloudsimple.DedicatedCloudServiceArgs{
			DedicatedCloudServiceName: pulumi.String("myService"),
			GatewaySubnet:             pulumi.String("10.0.0.0"),
			Location:                  pulumi.String("westus"),
			ResourceGroupName:         pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.vmwarecloudsimple.DedicatedCloudService;
import com.pulumi.azurenative.vmwarecloudsimple.DedicatedCloudServiceArgs;
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
        var dedicatedCloudService = new DedicatedCloudService("dedicatedCloudService", DedicatedCloudServiceArgs.builder()        
            .dedicatedCloudServiceName("myService")
            .gatewaySubnet("10.0.0.0")
            .location("westus")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dedicatedCloudService = new azure_native.vmwarecloudsimple.DedicatedCloudService("dedicatedCloudService", {
    dedicatedCloudServiceName: "myService",
    gatewaySubnet: "10.0.0.0",
    location: "westus",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dedicated_cloud_service = azure_native.vmwarecloudsimple.DedicatedCloudService("dedicatedCloudService",
    dedicated_cloud_service_name="myService",
    gateway_subnet="10.0.0.0",
    location="westus",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  dedicatedCloudService:
    type: azure-native:vmwarecloudsimple:DedicatedCloudService
    properties:
      dedicatedCloudServiceName: myService
      gatewaySubnet: 10.0.0.0
      location: westus
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:vmwarecloudsimple:DedicatedCloudService myService /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.VMwareCloudSimple/dedicatedCloudServices/myService 
```
