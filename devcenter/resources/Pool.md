A pool of Virtual Machines.
API Version: 2022-11-11-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Pools_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.DevCenter.Pool("pool", new()
    {
        DevBoxDefinitionName = "WebDevBox",
        LicenseType = "Windows_Client",
        LocalAdministrator = "Enabled",
        Location = "centralus",
        NetworkConnectionName = "Network1-westus2",
        PoolName = "DevPool",
        ProjectName = "DevProject",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	devcenter "github.com/pulumi/pulumi-azure-native-sdk/devcenter"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devcenter.NewPool(ctx, "pool", &devcenter.PoolArgs{
			DevBoxDefinitionName:  pulumi.String("WebDevBox"),
			LicenseType:           pulumi.String("Windows_Client"),
			LocalAdministrator:    pulumi.String("Enabled"),
			Location:              pulumi.String("centralus"),
			NetworkConnectionName: pulumi.String("Network1-westus2"),
			PoolName:              pulumi.String("DevPool"),
			ProjectName:           pulumi.String("DevProject"),
			ResourceGroupName:     pulumi.String("rg1"),
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
import com.pulumi.azurenative.devcenter.Pool;
import com.pulumi.azurenative.devcenter.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .devBoxDefinitionName("WebDevBox")
            .licenseType("Windows_Client")
            .localAdministrator("Enabled")
            .location("centralus")
            .networkConnectionName("Network1-westus2")
            .poolName("DevPool")
            .projectName("DevProject")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.devcenter.Pool("pool", {
    devBoxDefinitionName: "WebDevBox",
    licenseType: "Windows_Client",
    localAdministrator: "Enabled",
    location: "centralus",
    networkConnectionName: "Network1-westus2",
    poolName: "DevPool",
    projectName: "DevProject",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.devcenter.Pool("pool",
    dev_box_definition_name="WebDevBox",
    license_type="Windows_Client",
    local_administrator="Enabled",
    location="centralus",
    network_connection_name="Network1-westus2",
    pool_name="DevPool",
    project_name="DevProject",
    resource_group_name="rg1")

```

```yaml
resources:
  pool:
    type: azure-native:devcenter:Pool
    properties:
      devBoxDefinitionName: WebDevBox
      licenseType: Windows_Client
      localAdministrator: Enabled
      location: centralus
      networkConnectionName: Network1-westus2
      poolName: DevPool
      projectName: DevProject
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devcenter:Pool DevPool /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/projects/DevProject/pools/DevPool 
```
