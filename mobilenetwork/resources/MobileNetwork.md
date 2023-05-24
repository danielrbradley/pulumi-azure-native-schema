Mobile network resource.
API Version: 2022-11-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create mobile network
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var mobileNetwork = new AzureNative.MobileNetwork.MobileNetwork("mobileNetwork", new()
    {
        Location = "eastus",
        MobileNetworkName = "testMobileNetwork",
        PublicLandMobileNetworkIdentifier = new AzureNative.MobileNetwork.Inputs.PlmnIdArgs
        {
            Mcc = "001",
            Mnc = "01",
        },
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
		_, err := mobilenetwork.NewMobileNetwork(ctx, "mobileNetwork", &mobilenetwork.MobileNetworkArgs{
			Location:          pulumi.String("eastus"),
			MobileNetworkName: pulumi.String("testMobileNetwork"),
			PublicLandMobileNetworkIdentifier: &mobilenetwork.PlmnIdArgs{
				Mcc: pulumi.String("001"),
				Mnc: pulumi.String("01"),
			},
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
import com.pulumi.azurenative.mobilenetwork.MobileNetwork;
import com.pulumi.azurenative.mobilenetwork.MobileNetworkArgs;
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
        var mobileNetwork = new MobileNetwork("mobileNetwork", MobileNetworkArgs.builder()        
            .location("eastus")
            .mobileNetworkName("testMobileNetwork")
            .publicLandMobileNetworkIdentifier(Map.ofEntries(
                Map.entry("mcc", "001"),
                Map.entry("mnc", "01")
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const mobileNetwork = new azure_native.mobilenetwork.MobileNetwork("mobileNetwork", {
    location: "eastus",
    mobileNetworkName: "testMobileNetwork",
    publicLandMobileNetworkIdentifier: {
        mcc: "001",
        mnc: "01",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

mobile_network = azure_native.mobilenetwork.MobileNetwork("mobileNetwork",
    location="eastus",
    mobile_network_name="testMobileNetwork",
    public_land_mobile_network_identifier=azure_native.mobilenetwork.PlmnIdArgs(
        mcc="001",
        mnc="01",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  mobileNetwork:
    type: azure-native:mobilenetwork:MobileNetwork
    properties:
      location: eastus
      mobileNetworkName: testMobileNetwork
      publicLandMobileNetworkIdentifier:
        mcc: '001'
        mnc: '01'
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mobilenetwork:MobileNetwork testMobileNetwork /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork 
```
