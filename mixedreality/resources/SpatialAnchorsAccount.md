SpatialAnchorsAccount Response.
API Version: 2021-01-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create spatial anchor account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var spatialAnchorsAccount = new AzureNative.MixedReality.SpatialAnchorsAccount("spatialAnchorsAccount", new()
    {
        AccountName = "MyAccount",
        Location = "eastus2euap",
        ResourceGroupName = "MyResourceGroup",
    });

});


```

```go
package main

import (
	mixedreality "github.com/pulumi/pulumi-azure-native-sdk/mixedreality"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := mixedreality.NewSpatialAnchorsAccount(ctx, "spatialAnchorsAccount", &mixedreality.SpatialAnchorsAccountArgs{
			AccountName:       pulumi.String("MyAccount"),
			Location:          pulumi.String("eastus2euap"),
			ResourceGroupName: pulumi.String("MyResourceGroup"),
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
import com.pulumi.azurenative.mixedreality.SpatialAnchorsAccount;
import com.pulumi.azurenative.mixedreality.SpatialAnchorsAccountArgs;
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
        var spatialAnchorsAccount = new SpatialAnchorsAccount("spatialAnchorsAccount", SpatialAnchorsAccountArgs.builder()        
            .accountName("MyAccount")
            .location("eastus2euap")
            .resourceGroupName("MyResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const spatialAnchorsAccount = new azure_native.mixedreality.SpatialAnchorsAccount("spatialAnchorsAccount", {
    accountName: "MyAccount",
    location: "eastus2euap",
    resourceGroupName: "MyResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

spatial_anchors_account = azure_native.mixedreality.SpatialAnchorsAccount("spatialAnchorsAccount",
    account_name="MyAccount",
    location="eastus2euap",
    resource_group_name="MyResourceGroup")

```

```yaml
resources:
  spatialAnchorsAccount:
    type: azure-native:mixedreality:SpatialAnchorsAccount
    properties:
      accountName: MyAccount
      location: eastus2euap
      resourceGroupName: MyResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mixedreality:SpatialAnchorsAccount MyAccount /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/MyResourceGroup/providers/Microsoft.MixedReality/spatialAnchorsAccounts/MyAccount 
```
