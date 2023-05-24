Data network resource. Must be created in the same location as its parent mobile network.
API Version: 2022-11-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create data network
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataNetwork = new AzureNative.MobileNetwork.DataNetwork("dataNetwork", new()
    {
        DataNetworkName = "testDataNetwork",
        Description = "myFavouriteDataNetwork",
        Location = "eastus",
        MobileNetworkName = "testMobileNetwork",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	mobilenetwork "github.com/pulumi/pulumi-azure-native-sdk/mobilenetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := mobilenetwork.NewDataNetwork(ctx, "dataNetwork", &mobilenetwork.DataNetworkArgs{
			DataNetworkName:   pulumi.String("testDataNetwork"),
			Description:       pulumi.String("myFavouriteDataNetwork"),
			Location:          pulumi.String("eastus"),
			MobileNetworkName: pulumi.String("testMobileNetwork"),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.mobilenetwork.DataNetwork;
import com.pulumi.azurenative.mobilenetwork.DataNetworkArgs;
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
        var dataNetwork = new DataNetwork("dataNetwork", DataNetworkArgs.builder()        
            .dataNetworkName("testDataNetwork")
            .description("myFavouriteDataNetwork")
            .location("eastus")
            .mobileNetworkName("testMobileNetwork")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataNetwork = new azure_native.mobilenetwork.DataNetwork("dataNetwork", {
    dataNetworkName: "testDataNetwork",
    description: "myFavouriteDataNetwork",
    location: "eastus",
    mobileNetworkName: "testMobileNetwork",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_network = azure_native.mobilenetwork.DataNetwork("dataNetwork",
    data_network_name="testDataNetwork",
    description="myFavouriteDataNetwork",
    location="eastus",
    mobile_network_name="testMobileNetwork",
    resource_group_name="rg1")

```

```yaml
resources:
  dataNetwork:
    type: azure-native:mobilenetwork:DataNetwork
    properties:
      dataNetworkName: testDataNetwork
      description: myFavouriteDataNetwork
      location: eastus
      mobileNetworkName: testMobileNetwork
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mobilenetwork:DataNetwork testDataNetwork /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testDataNetwork 
```
