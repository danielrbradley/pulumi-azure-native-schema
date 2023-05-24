Definition of ARM tracked top level resource.
API Version: 2022-06-01.
Previous API Version: 2021-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update data collection endpoint
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataCollectionEndpoint = new AzureNative.Insights.DataCollectionEndpoint("dataCollectionEndpoint", new()
    {
        DataCollectionEndpointName = "myCollectionEndpoint",
        Location = "eastus",
        NetworkAcls = new AzureNative.Insights.Inputs.DataCollectionEndpointNetworkAclsArgs
        {
            PublicNetworkAccess = "Enabled",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	insights "github.com/pulumi/pulumi-azure-native-sdk/insights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := insights.NewDataCollectionEndpoint(ctx, "dataCollectionEndpoint", &insights.DataCollectionEndpointArgs{
			DataCollectionEndpointName: pulumi.String("myCollectionEndpoint"),
			Location:                   pulumi.String("eastus"),
			NetworkAcls: &insights.DataCollectionEndpointNetworkAclsArgs{
				PublicNetworkAccess: pulumi.String("Enabled"),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.insights.DataCollectionEndpoint;
import com.pulumi.azurenative.insights.DataCollectionEndpointArgs;
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
        var dataCollectionEndpoint = new DataCollectionEndpoint("dataCollectionEndpoint", DataCollectionEndpointArgs.builder()        
            .dataCollectionEndpointName("myCollectionEndpoint")
            .location("eastus")
            .networkAcls(Map.of("publicNetworkAccess", "Enabled"))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataCollectionEndpoint = new azure_native.insights.DataCollectionEndpoint("dataCollectionEndpoint", {
    dataCollectionEndpointName: "myCollectionEndpoint",
    location: "eastus",
    networkAcls: {
        publicNetworkAccess: "Enabled",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_collection_endpoint = azure_native.insights.DataCollectionEndpoint("dataCollectionEndpoint",
    data_collection_endpoint_name="myCollectionEndpoint",
    location="eastus",
    network_acls=azure_native.insights.DataCollectionEndpointNetworkAclsArgs(
        public_network_access="Enabled",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  dataCollectionEndpoint:
    type: azure-native:insights:DataCollectionEndpoint
    properties:
      dataCollectionEndpointName: myCollectionEndpoint
      location: eastus
      networkAcls:
        publicNetworkAccess: Enabled
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:DataCollectionEndpoint myCollectionEndpoint /subscriptions/703362b3-f278-4e4b-9179-c76eaf41ffc2/resourceGroups/myResourceGroup/providers/Microsoft.Insights/dataCollectionEndpoints/myCollectionEndpoint 
```
