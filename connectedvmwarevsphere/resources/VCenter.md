Defines the vCenter.
API Version: 2022-07-15-preview.
Previous API Version: 2020-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateVCenter
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vCenter = new AzureNative.ConnectedVMwarevSphere.VCenter("vCenter", new()
    {
        Credentials = new AzureNative.ConnectedVMwarevSphere.Inputs.VICredentialArgs
        {
            Password = "<password>",
            Username = "tempuser",
        },
        ExtendedLocation = new AzureNative.ConnectedVMwarevSphere.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso",
            Type = "customLocation",
        },
        Fqdn = "ContosoVMware.contoso.com",
        Location = "East US",
        Port = 1234,
        ResourceGroupName = "testrg",
        VcenterName = "ContosoVCenter",
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
		_, err := connectedvmwarevsphere.NewVCenter(ctx, "vCenter", &connectedvmwarevsphere.VCenterArgs{
			Credentials: &connectedvmwarevsphere.VICredentialArgs{
				Password: pulumi.String("<password>"),
				Username: pulumi.String("tempuser"),
			},
			ExtendedLocation: &connectedvmwarevsphere.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso"),
				Type: pulumi.String("customLocation"),
			},
			Fqdn:              pulumi.String("ContosoVMware.contoso.com"),
			Location:          pulumi.String("East US"),
			Port:              pulumi.Int(1234),
			ResourceGroupName: pulumi.String("testrg"),
			VcenterName:       pulumi.String("ContosoVCenter"),
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
import com.pulumi.azurenative.connectedvmwarevsphere.VCenter;
import com.pulumi.azurenative.connectedvmwarevsphere.VCenterArgs;
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
        var vCenter = new VCenter("vCenter", VCenterArgs.builder()        
            .credentials(Map.ofEntries(
                Map.entry("password", "<password>"),
                Map.entry("username", "tempuser")
            ))
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso"),
                Map.entry("type", "customLocation")
            ))
            .fqdn("ContosoVMware.contoso.com")
            .location("East US")
            .port(1234)
            .resourceGroupName("testrg")
            .vcenterName("ContosoVCenter")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vCenter = new azure_native.connectedvmwarevsphere.VCenter("vCenter", {
    credentials: {
        password: "<password>",
        username: "tempuser",
    },
    extendedLocation: {
        name: "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso",
        type: "customLocation",
    },
    fqdn: "ContosoVMware.contoso.com",
    location: "East US",
    port: 1234,
    resourceGroupName: "testrg",
    vcenterName: "ContosoVCenter",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

v_center = azure_native.connectedvmwarevsphere.VCenter("vCenter",
    credentials=azure_native.connectedvmwarevsphere.VICredentialArgs(
        password="<password>",
        username="tempuser",
    ),
    extended_location=azure_native.connectedvmwarevsphere.ExtendedLocationArgs(
        name="/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso",
        type="customLocation",
    ),
    fqdn="ContosoVMware.contoso.com",
    location="East US",
    port=1234,
    resource_group_name="testrg",
    vcenter_name="ContosoVCenter")

```

```yaml
resources:
  vCenter:
    type: azure-native:connectedvmwarevsphere:VCenter
    properties:
      credentials:
        password: <password>
        username: tempuser
      extendedLocation:
        name: /subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.ExtendedLocation/customLocations/contoso
        type: customLocation
      fqdn: ContosoVMware.contoso.com
      location: East US
      port: 1234
      resourceGroupName: testrg
      vcenterName: ContosoVCenter

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:connectedvmwarevsphere:VCenter ContosoVCenter /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ConnectedVMwarevSphere/VCenters/ContosoVCenter 
```
