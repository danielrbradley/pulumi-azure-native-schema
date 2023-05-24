A privateLinkHub
API Version: 2021-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a privateLinkHub
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateLinkHub = new AzureNative.Synapse.PrivateLinkHub("privateLinkHub", new()
    {
        Location = "East US",
        PrivateLinkHubName = "privateLinkHub1",
        ResourceGroupName = "resourceGroup1",
        Tags = 
        {
            { "key", "value" },
        },
    });

});


```

```go
package main

import (
	synapse "github.com/pulumi/pulumi-azure-native-sdk/synapse"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := synapse.NewPrivateLinkHub(ctx, "privateLinkHub", &synapse.PrivateLinkHubArgs{
			Location:           pulumi.String("East US"),
			PrivateLinkHubName: pulumi.String("privateLinkHub1"),
			ResourceGroupName:  pulumi.String("resourceGroup1"),
			Tags: pulumi.StringMap{
				"key": pulumi.String("value"),
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
import com.pulumi.azurenative.synapse.PrivateLinkHub;
import com.pulumi.azurenative.synapse.PrivateLinkHubArgs;
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
        var privateLinkHub = new PrivateLinkHub("privateLinkHub", PrivateLinkHubArgs.builder()        
            .location("East US")
            .privateLinkHubName("privateLinkHub1")
            .resourceGroupName("resourceGroup1")
            .tags(Map.of("key", "value"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateLinkHub = new azure_native.synapse.PrivateLinkHub("privateLinkHub", {
    location: "East US",
    privateLinkHubName: "privateLinkHub1",
    resourceGroupName: "resourceGroup1",
    tags: {
        key: "value",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_link_hub = azure_native.synapse.PrivateLinkHub("privateLinkHub",
    location="East US",
    private_link_hub_name="privateLinkHub1",
    resource_group_name="resourceGroup1",
    tags={
        "key": "value",
    })

```

```yaml
resources:
  privateLinkHub:
    type: azure-native:synapse:PrivateLinkHub
    properties:
      location: East US
      privateLinkHubName: privateLinkHub1
      resourceGroupName: resourceGroup1
      tags:
        key: value

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:synapse:PrivateLinkHub privateLinkHub1 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/resourceGroup1/providers/Microsoft.Synapse/privateLinkHubs/privateLinkHub1 
```
