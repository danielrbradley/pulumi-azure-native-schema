Represents an instance of a orchestrator.
API Version: 2021-03-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### put delegated subnet
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var delegatedSubnetServiceDetails = new AzureNative.DelegatedNetwork.DelegatedSubnetServiceDetails("delegatedSubnetServiceDetails", new()
    {
        ControllerDetails = new AzureNative.DelegatedNetwork.Inputs.ControllerDetailsArgs
        {
            Id = "/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/dnctestcontroller",
        },
        Location = "West US",
        ResourceGroupName = "TestRG",
        ResourceName = "delegated1",
        SubnetDetails = new AzureNative.DelegatedNetwork.Inputs.SubnetDetailsArgs
        {
            Id = "/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet",
        },
    });

});


```

```go
package main

import (
	delegatednetwork "github.com/pulumi/pulumi-azure-native-sdk/delegatednetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := delegatednetwork.NewDelegatedSubnetServiceDetails(ctx, "delegatedSubnetServiceDetails", &delegatednetwork.DelegatedSubnetServiceDetailsArgs{
			ControllerDetails: &delegatednetwork.ControllerDetailsTypeArgs{
				Id: pulumi.String("/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/dnctestcontroller"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("TestRG"),
			ResourceName:      pulumi.String("delegated1"),
			SubnetDetails: &delegatednetwork.SubnetDetailsArgs{
				Id: pulumi.String("/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet"),
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
import com.pulumi.azurenative.delegatednetwork.DelegatedSubnetServiceDetails;
import com.pulumi.azurenative.delegatednetwork.DelegatedSubnetServiceDetailsArgs;
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
        var delegatedSubnetServiceDetails = new DelegatedSubnetServiceDetails("delegatedSubnetServiceDetails", DelegatedSubnetServiceDetailsArgs.builder()        
            .controllerDetails(Map.of("id", "/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/dnctestcontroller"))
            .location("West US")
            .resourceGroupName("TestRG")
            .resourceName("delegated1")
            .subnetDetails(Map.of("id", "/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const delegatedSubnetServiceDetails = new azure_native.delegatednetwork.DelegatedSubnetServiceDetails("delegatedSubnetServiceDetails", {
    controllerDetails: {
        id: "/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/dnctestcontroller",
    },
    location: "West US",
    resourceGroupName: "TestRG",
    resourceName: "delegated1",
    subnetDetails: {
        id: "/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

delegated_subnet_service_details = azure_native.delegatednetwork.DelegatedSubnetServiceDetails("delegatedSubnetServiceDetails",
    controller_details=azure_native.delegatednetwork.ControllerDetailsArgs(
        id="/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/dnctestcontroller",
    ),
    location="West US",
    resource_group_name="TestRG",
    resource_name_="delegated1",
    subnet_details=azure_native.delegatednetwork.SubnetDetailsArgs(
        id="/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet",
    ))

```

```yaml
resources:
  delegatedSubnetServiceDetails:
    type: azure-native:delegatednetwork:DelegatedSubnetServiceDetails
    properties:
      controllerDetails:
        id: /subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/dnctestcontroller
      location: West US
      resourceGroupName: TestRG
      resourceName: delegated1
      subnetDetails:
        id: /subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:delegatednetwork:DelegatedSubnetServiceDetails delegated1 /subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/delegatedSubnets/delegated1 
```
