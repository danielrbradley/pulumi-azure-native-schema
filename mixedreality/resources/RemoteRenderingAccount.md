RemoteRenderingAccount Response.
API Version: 2021-01-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create remote rendering account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var remoteRenderingAccount = new AzureNative.MixedReality.RemoteRenderingAccount("remoteRenderingAccount", new()
    {
        AccountName = "MyAccount",
        Identity = new AzureNative.MixedReality.Inputs.IdentityArgs
        {
            Type = AzureNative.MixedReality.ResourceIdentityType.SystemAssigned,
        },
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
		_, err := mixedreality.NewRemoteRenderingAccount(ctx, "remoteRenderingAccount", &mixedreality.RemoteRenderingAccountArgs{
			AccountName: pulumi.String("MyAccount"),
			Identity: &mixedreality.IdentityArgs{
				Type: mixedreality.ResourceIdentityTypeSystemAssigned,
			},
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
import com.pulumi.azurenative.mixedreality.RemoteRenderingAccount;
import com.pulumi.azurenative.mixedreality.RemoteRenderingAccountArgs;
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
        var remoteRenderingAccount = new RemoteRenderingAccount("remoteRenderingAccount", RemoteRenderingAccountArgs.builder()        
            .accountName("MyAccount")
            .identity(Map.of("type", "SystemAssigned"))
            .location("eastus2euap")
            .resourceGroupName("MyResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const remoteRenderingAccount = new azure_native.mixedreality.RemoteRenderingAccount("remoteRenderingAccount", {
    accountName: "MyAccount",
    identity: {
        type: azure_native.mixedreality.ResourceIdentityType.SystemAssigned,
    },
    location: "eastus2euap",
    resourceGroupName: "MyResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

remote_rendering_account = azure_native.mixedreality.RemoteRenderingAccount("remoteRenderingAccount",
    account_name="MyAccount",
    identity=azure_native.mixedreality.IdentityArgs(
        type=azure_native.mixedreality.ResourceIdentityType.SYSTEM_ASSIGNED,
    ),
    location="eastus2euap",
    resource_group_name="MyResourceGroup")

```

```yaml
resources:
  remoteRenderingAccount:
    type: azure-native:mixedreality:RemoteRenderingAccount
    properties:
      accountName: MyAccount
      identity:
        type: SystemAssigned
      location: eastus2euap
      resourceGroupName: MyResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mixedreality:RemoteRenderingAccount MyAccount /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/MyResourceGroup/providers/Microsoft.MixedReality/remoteRenderingAccounts/MyAccount 
```
