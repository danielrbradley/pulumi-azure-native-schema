The VmmServers resource definition.
API Version: 2020-06-05-preview.
Previous API Version: 2020-06-05-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateVMMServer
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vmmServer = new AzureNative.ScVmm.VmmServer("vmmServer", new()
    {
        Credentials = new AzureNative.ScVmm.Inputs.VMMServerPropertiesCredentialsArgs
        {
            Password = "password",
            Username = "testuser",
        },
        ExtendedLocation = new AzureNative.ScVmm.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso",
            Type = "customLocation",
        },
        Fqdn = "VMM.contoso.com",
        Location = "East US",
        Port = 1234,
        ResourceGroupName = "testrg",
        VmmServerName = "ContosoVMMServer",
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
		_, err := scvmm.NewVmmServer(ctx, "vmmServer", &scvmm.VmmServerArgs{
			Credentials: &scvmm.VMMServerPropertiesCredentialsArgs{
				Password: pulumi.String("password"),
				Username: pulumi.String("testuser"),
			},
			ExtendedLocation: &scvmm.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso"),
				Type: pulumi.String("customLocation"),
			},
			Fqdn:              pulumi.String("VMM.contoso.com"),
			Location:          pulumi.String("East US"),
			Port:              pulumi.Int(1234),
			ResourceGroupName: pulumi.String("testrg"),
			VmmServerName:     pulumi.String("ContosoVMMServer"),
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
import com.pulumi.azurenative.scvmm.VmmServer;
import com.pulumi.azurenative.scvmm.VmmServerArgs;
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
        var vmmServer = new VmmServer("vmmServer", VmmServerArgs.builder()        
            .credentials(Map.ofEntries(
                Map.entry("password", "password"),
                Map.entry("username", "testuser")
            ))
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso"),
                Map.entry("type", "customLocation")
            ))
            .fqdn("VMM.contoso.com")
            .location("East US")
            .port(1234)
            .resourceGroupName("testrg")
            .vmmServerName("ContosoVMMServer")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vmmServer = new azure_native.scvmm.VmmServer("vmmServer", {
    credentials: {
        password: "password",
        username: "testuser",
    },
    extendedLocation: {
        name: "/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso",
        type: "customLocation",
    },
    fqdn: "VMM.contoso.com",
    location: "East US",
    port: 1234,
    resourceGroupName: "testrg",
    vmmServerName: "ContosoVMMServer",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vmm_server = azure_native.scvmm.VmmServer("vmmServer",
    credentials=azure_native.scvmm.VMMServerPropertiesCredentialsArgs(
        password="password",
        username="testuser",
    ),
    extended_location=azure_native.scvmm.ExtendedLocationArgs(
        name="/subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso",
        type="customLocation",
    ),
    fqdn="VMM.contoso.com",
    location="East US",
    port=1234,
    resource_group_name="testrg",
    vmm_server_name="ContosoVMMServer")

```

```yaml
resources:
  vmmServer:
    type: azure-native:scvmm:VmmServer
    properties:
      credentials:
        password: password
        username: testuser
      extendedLocation:
        name: /subscriptions/a5015e1c-867f-4533-8541-85cd470d0cfb/resourceGroups/demoRG/providers/Microsoft.Arc/customLocations/contoso
        type: customLocation
      fqdn: VMM.contoso.com
      location: East US
      port: 1234
      resourceGroupName: testrg
      vmmServerName: ContosoVMMServer

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:scvmm:VmmServer ContosoVMMServer /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.SCVMM/VMMServers/ContosoVMMServer 
```
