The Clouds resource definition.
API Version: 2020-06-05-preview.
Previous API Version: 2020-06-05-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateCloud
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cloud = new AzureNative.ScVmm.Cloud("cloud", new()
    {
        CloudName = "HRCloud",
        ExtendedLocation = new AzureNative.ScVmm.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso",
            Type = "customLocation",
        },
        Location = "East US",
        ResourceGroupName = "testrg",
        Uuid = "aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
        VmmServerId = "/subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.SCVMM/VMMServers/ContosoVMMServer",
    });

});


```

```go
package main

import (
	scvmm "github.com/pulumi/pulumi-azure-native-sdk/scvmm"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := scvmm.NewCloud(ctx, "cloud", &scvmm.CloudArgs{
			CloudName: pulumi.String("HRCloud"),
			ExtendedLocation: &scvmm.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso"),
				Type: pulumi.String("customLocation"),
			},
			Location:          pulumi.String("East US"),
			ResourceGroupName: pulumi.String("testrg"),
			Uuid:              pulumi.String("aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"),
			VmmServerId:       pulumi.String("/subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.SCVMM/VMMServers/ContosoVMMServer"),
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
import com.pulumi.azurenative.scvmm.Cloud;
import com.pulumi.azurenative.scvmm.CloudArgs;
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
        var cloud = new Cloud("cloud", CloudArgs.builder()        
            .cloudName("HRCloud")
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso"),
                Map.entry("type", "customLocation")
            ))
            .location("East US")
            .resourceGroupName("testrg")
            .uuid("aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee")
            .vmmServerId("/subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.SCVMM/VMMServers/ContosoVMMServer")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cloud = new azure_native.scvmm.Cloud("cloud", {
    cloudName: "HRCloud",
    extendedLocation: {
        name: "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso",
        type: "customLocation",
    },
    location: "East US",
    resourceGroupName: "testrg",
    uuid: "aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
    vmmServerId: "/subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.SCVMM/VMMServers/ContosoVMMServer",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cloud = azure_native.scvmm.Cloud("cloud",
    cloud_name="HRCloud",
    extended_location=azure_native.scvmm.ExtendedLocationArgs(
        name="/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso",
        type="customLocation",
    ),
    location="East US",
    resource_group_name="testrg",
    uuid="aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
    vmm_server_id="/subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.SCVMM/VMMServers/ContosoVMMServer")

```

```yaml
resources:
  cloud:
    type: azure-native:scvmm:Cloud
    properties:
      cloudName: HRCloud
      extendedLocation:
        name: /subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso
        type: customLocation
      location: East US
      resourceGroupName: testrg
      uuid: aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee
      vmmServerId: /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.SCVMM/VMMServers/ContosoVMMServer

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:scvmm:Cloud HRCloud /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.SCVMM/Clouds/HRCloud 
```
