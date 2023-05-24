Storage resource for managedEnvironment.
API Version: 2022-10-01.
Previous API Version: 2022-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update environments storage
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedEnvironmentsStorage = new AzureNative.App.ManagedEnvironmentsStorage("managedEnvironmentsStorage", new()
    {
        EnvironmentName = "managedEnv",
        Properties = new AzureNative.App.Inputs.ManagedEnvironmentStoragePropertiesArgs
        {
            AzureFile = new AzureNative.App.Inputs.AzureFilePropertiesArgs
            {
                AccessMode = "ReadOnly",
                AccountKey = "key",
                AccountName = "account1",
                ShareName = "share1",
            },
        },
        ResourceGroupName = "examplerg",
        StorageName = "jlaw-demo1",
    });

});


```

```go
package main

import (
	app "github.com/pulumi/pulumi-azure-native-sdk/app"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := app.NewManagedEnvironmentsStorage(ctx, "managedEnvironmentsStorage", &app.ManagedEnvironmentsStorageArgs{
			EnvironmentName: pulumi.String("managedEnv"),
			Properties: app.ManagedEnvironmentStorageResponseProperties{
				AzureFile: &app.AzureFilePropertiesArgs{
					AccessMode:  pulumi.String("ReadOnly"),
					AccountKey:  pulumi.String("key"),
					AccountName: pulumi.String("account1"),
					ShareName:   pulumi.String("share1"),
				},
			},
			ResourceGroupName: pulumi.String("examplerg"),
			StorageName:       pulumi.String("jlaw-demo1"),
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
import com.pulumi.azurenative.app.ManagedEnvironmentsStorage;
import com.pulumi.azurenative.app.ManagedEnvironmentsStorageArgs;
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
        var managedEnvironmentsStorage = new ManagedEnvironmentsStorage("managedEnvironmentsStorage", ManagedEnvironmentsStorageArgs.builder()        
            .environmentName("managedEnv")
            .properties(Map.of("azureFile", Map.ofEntries(
                Map.entry("accessMode", "ReadOnly"),
                Map.entry("accountKey", "key"),
                Map.entry("accountName", "account1"),
                Map.entry("shareName", "share1")
            )))
            .resourceGroupName("examplerg")
            .storageName("jlaw-demo1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedEnvironmentsStorage = new azure_native.app.ManagedEnvironmentsStorage("managedEnvironmentsStorage", {
    environmentName: "managedEnv",
    properties: {
        azureFile: {
            accessMode: "ReadOnly",
            accountKey: "key",
            accountName: "account1",
            shareName: "share1",
        },
    },
    resourceGroupName: "examplerg",
    storageName: "jlaw-demo1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_environments_storage = azure_native.app.ManagedEnvironmentsStorage("managedEnvironmentsStorage",
    environment_name="managedEnv",
    properties=azure_native.app.ManagedEnvironmentStorageResponsePropertiesArgs(
        azure_file=azure_native.app.AzureFilePropertiesArgs(
            access_mode="ReadOnly",
            account_key="key",
            account_name="account1",
            share_name="share1",
        ),
    ),
    resource_group_name="examplerg",
    storage_name="jlaw-demo1")

```

```yaml
resources:
  managedEnvironmentsStorage:
    type: azure-native:app:ManagedEnvironmentsStorage
    properties:
      environmentName: managedEnv
      properties:
        azureFile:
          accessMode: ReadOnly
          accountKey: key
          accountName: account1
          shareName: share1
      resourceGroupName: examplerg
      storageName: jlaw-demo1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:app:ManagedEnvironmentsStorage jlaw-demo1 /subscriptions/8efdecc5-919e-44eb-b179-915dca89ebf9/resourceGroups/examplerg/providers/Microsoft.App/managedEnvironments/managedEnv/storages/jlaw-demo1 
```
