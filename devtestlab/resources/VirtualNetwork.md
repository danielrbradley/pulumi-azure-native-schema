A virtual network.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VirtualNetworks_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetwork = new AzureNative.DevTestLab.VirtualNetwork("virtualNetwork", new()
    {
        LabName = "{labName}",
        Location = "{location}",
        Name = "{virtualNetworkName}",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "tagName1", "tagValue1" },
        },
    });

});


```

```go
package main

import (
	devtestlab "github.com/pulumi/pulumi-azure-native-sdk/devtestlab"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devtestlab.NewVirtualNetwork(ctx, "virtualNetwork", &devtestlab.VirtualNetworkArgs{
			LabName:           pulumi.String("{labName}"),
			Location:          pulumi.String("{location}"),
			Name:              pulumi.String("{virtualNetworkName}"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"tagName1": pulumi.String("tagValue1"),
			},
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
import com.pulumi.azurenative.devtestlab.VirtualNetwork;
import com.pulumi.azurenative.devtestlab.VirtualNetworkArgs;
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
        var virtualNetwork = new VirtualNetwork("virtualNetwork", VirtualNetworkArgs.builder()        
            .labName("{labName}")
            .location("{location}")
            .name("{virtualNetworkName}")
            .resourceGroupName("resourceGroupName")
            .tags(Map.of("tagName1", "tagValue1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetwork = new azure_native.devtestlab.VirtualNetwork("virtualNetwork", {
    labName: "{labName}",
    location: "{location}",
    name: "{virtualNetworkName}",
    resourceGroupName: "resourceGroupName",
    tags: {
        tagName1: "tagValue1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network = azure_native.devtestlab.VirtualNetwork("virtualNetwork",
    lab_name="{labName}",
    location="{location}",
    name="{virtualNetworkName}",
    resource_group_name="resourceGroupName",
    tags={
        "tagName1": "tagValue1",
    })

```

```yaml
resources:
  virtualNetwork:
    type: azure-native:devtestlab:VirtualNetwork
    properties:
      labName: '{labName}'
      location: '{location}'
      name: '{virtualNetworkName}'
      resourceGroupName: resourceGroupName
      tags:
        tagName1: tagValue1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:VirtualNetwork {virtualNetworkName} /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualnetworks/{virtualNetworkName} 
```
