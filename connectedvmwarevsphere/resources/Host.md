Define the host.
API Version: 2022-07-15-preview.
Previous API Version: 2020-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateHost
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var host = new AzureNative.ConnectedVMwarevSphere.Host("host", new()
    {
        ExtendedLocation = new AzureNative.ConnectedVMwarevSphere.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso",
            Type = "customLocation",
        },
        HostName = "HRHost",
        Location = "East US",
        MoRefId = "aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
        ResourceGroupName = "testrg",
        VCenterId = "/subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ConnectedVMwarevSphere/VCenters/ContosoVCenter",
    });

});


```

```go
package main

import (
	connectedvmwarevsphere "github.com/pulumi/pulumi-azure-native-sdk/connectedvmwarevsphere"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := connectedvmwarevsphere.NewHost(ctx, "host", &connectedvmwarevsphere.HostArgs{
			ExtendedLocation: &connectedvmwarevsphere.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso"),
				Type: pulumi.String("customLocation"),
			},
			HostName:          pulumi.String("HRHost"),
			Location:          pulumi.String("East US"),
			MoRefId:           pulumi.String("aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"),
			ResourceGroupName: pulumi.String("testrg"),
			VCenterId:         pulumi.String("/subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ConnectedVMwarevSphere/VCenters/ContosoVCenter"),
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
import com.pulumi.azurenative.connectedvmwarevsphere.Host;
import com.pulumi.azurenative.connectedvmwarevsphere.HostArgs;
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
        var host = new Host("host", HostArgs.builder()        
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso"),
                Map.entry("type", "customLocation")
            ))
            .hostName("HRHost")
            .location("East US")
            .moRefId("aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee")
            .resourceGroupName("testrg")
            .vCenterId("/subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ConnectedVMwarevSphere/VCenters/ContosoVCenter")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const host = new azure_native.connectedvmwarevsphere.Host("host", {
    extendedLocation: {
        name: "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso",
        type: "customLocation",
    },
    hostName: "HRHost",
    location: "East US",
    moRefId: "aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
    resourceGroupName: "testrg",
    vCenterId: "/subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ConnectedVMwarevSphere/VCenters/ContosoVCenter",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

host = azure_native.connectedvmwarevsphere.Host("host",
    extended_location=azure_native.connectedvmwarevsphere.ExtendedLocationArgs(
        name="/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso",
        type="customLocation",
    ),
    host_name="HRHost",
    location="East US",
    mo_ref_id="aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
    resource_group_name="testrg",
    v_center_id="/subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ConnectedVMwarevSphere/VCenters/ContosoVCenter")

```

```yaml
resources:
  host:
    type: azure-native:connectedvmwarevsphere:Host
    properties:
      extendedLocation:
        name: /subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso
        type: customLocation
      hostName: HRHost
      location: East US
      moRefId: aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee
      resourceGroupName: testrg
      vCenterId: /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ConnectedVMwarevSphere/VCenters/ContosoVCenter

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:connectedvmwarevsphere:Host HRHost /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ConnectedVMwarevSphere/Hosts/HRHost 
```
