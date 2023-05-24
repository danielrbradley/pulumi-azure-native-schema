This type describes a network resource.
API Version: 2018-09-01-preview.
Previous API Version: 2018-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdateNetwork
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var network = new AzureNative.ServiceFabricMesh.Network("network", new()
    {
        Location = "EastUS",
        NetworkResourceName = "sampleNetwork",
        Properties = null,
        ResourceGroupName = "sbz_demo",
        Tags = null,
    });

});


```

```go
package main

import (
	servicefabricmesh "github.com/pulumi/pulumi-azure-native-sdk/servicefabricmesh"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabricmesh.NewNetwork(ctx, "network", &servicefabricmesh.NetworkArgs{
			Location:            pulumi.String("EastUS"),
			NetworkResourceName: pulumi.String("sampleNetwork"),
			Properties:          nil,
			ResourceGroupName:   pulumi.String("sbz_demo"),
			Tags:                nil,
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
import com.pulumi.azurenative.servicefabricmesh.Network;
import com.pulumi.azurenative.servicefabricmesh.NetworkArgs;
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
        var network = new Network("network", NetworkArgs.builder()        
            .location("EastUS")
            .networkResourceName("sampleNetwork")
            .properties()
            .resourceGroupName("sbz_demo")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const network = new azure_native.servicefabricmesh.Network("network", {
    location: "EastUS",
    networkResourceName: "sampleNetwork",
    properties: {},
    resourceGroupName: "sbz_demo",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network = azure_native.servicefabricmesh.Network("network",
    location="EastUS",
    network_resource_name="sampleNetwork",
    properties=azure_native.servicefabricmesh.NetworkResourcePropertiesArgs(),
    resource_group_name="sbz_demo",
    tags={})

```

```yaml
resources:
  network:
    type: azure-native:servicefabricmesh:Network
    properties:
      location: EastUS
      networkResourceName: sampleNetwork
      properties: {}
      resourceGroupName: sbz_demo
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicefabricmesh:Network sampleNetwork /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/sbz_demo/providers/Microsoft.ServiceFabricMesh/networks/sampleNetwork 
```
