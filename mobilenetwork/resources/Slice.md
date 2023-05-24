Network slice resource. Must be created in the same location as its parent mobile network.
API Version: 2022-11-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create network slice
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var slice = new AzureNative.MobileNetwork.Slice("slice", new()
    {
        Description = "myFavouriteSlice",
        Location = "eastus",
        MobileNetworkName = "testMobileNetwork",
        ResourceGroupName = "rg1",
        SliceName = "testSlice",
        Snssai = new AzureNative.MobileNetwork.Inputs.SnssaiArgs
        {
            Sd = "1abcde",
            Sst = 1,
        },
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
		_, err := mobilenetwork.NewSlice(ctx, "slice", &mobilenetwork.SliceArgs{
			Description:       pulumi.String("myFavouriteSlice"),
			Location:          pulumi.String("eastus"),
			MobileNetworkName: pulumi.String("testMobileNetwork"),
			ResourceGroupName: pulumi.String("rg1"),
			SliceName:         pulumi.String("testSlice"),
			Snssai: &mobilenetwork.SnssaiArgs{
				Sd:  pulumi.String("1abcde"),
				Sst: pulumi.Int(1),
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
import com.pulumi.azurenative.mobilenetwork.Slice;
import com.pulumi.azurenative.mobilenetwork.SliceArgs;
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
        var slice = new Slice("slice", SliceArgs.builder()        
            .description("myFavouriteSlice")
            .location("eastus")
            .mobileNetworkName("testMobileNetwork")
            .resourceGroupName("rg1")
            .sliceName("testSlice")
            .snssai(Map.ofEntries(
                Map.entry("sd", "1abcde"),
                Map.entry("sst", 1)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const slice = new azure_native.mobilenetwork.Slice("slice", {
    description: "myFavouriteSlice",
    location: "eastus",
    mobileNetworkName: "testMobileNetwork",
    resourceGroupName: "rg1",
    sliceName: "testSlice",
    snssai: {
        sd: "1abcde",
        sst: 1,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

slice = azure_native.mobilenetwork.Slice("slice",
    description="myFavouriteSlice",
    location="eastus",
    mobile_network_name="testMobileNetwork",
    resource_group_name="rg1",
    slice_name="testSlice",
    snssai=azure_native.mobilenetwork.SnssaiArgs(
        sd="1abcde",
        sst=1,
    ))

```

```yaml
resources:
  slice:
    type: azure-native:mobilenetwork:Slice
    properties:
      description: myFavouriteSlice
      location: eastus
      mobileNetworkName: testMobileNetwork
      resourceGroupName: rg1
      sliceName: testSlice
      snssai:
        sd: 1abcde
        sst: 1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mobilenetwork:Slice testSlice /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice 
```
