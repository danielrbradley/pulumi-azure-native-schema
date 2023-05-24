Storage resource for connectedEnvironment.
API Version: 2022-10-01.

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
    var connectedEnvironmentsStorage = new AzureNative.App.ConnectedEnvironmentsStorage("connectedEnvironmentsStorage", new()
    {
        ConnectedEnvironmentName = "env",
        Properties = new AzureNative.App.Inputs.ConnectedEnvironmentStoragePropertiesArgs
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
		_, err := app.NewConnectedEnvironmentsStorage(ctx, "connectedEnvironmentsStorage", &app.ConnectedEnvironmentsStorageArgs{
			ConnectedEnvironmentName: pulumi.String("env"),
			Properties: app.ConnectedEnvironmentStorageResponseProperties{
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
import com.pulumi.azurenative.app.ConnectedEnvironmentsStorage;
import com.pulumi.azurenative.app.ConnectedEnvironmentsStorageArgs;
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
        var connectedEnvironmentsStorage = new ConnectedEnvironmentsStorage("connectedEnvironmentsStorage", ConnectedEnvironmentsStorageArgs.builder()        
            .connectedEnvironmentName("env")
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

const connectedEnvironmentsStorage = new azure_native.app.ConnectedEnvironmentsStorage("connectedEnvironmentsStorage", {
    connectedEnvironmentName: "env",
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

connected_environments_storage = azure_native.app.ConnectedEnvironmentsStorage("connectedEnvironmentsStorage",
    connected_environment_name="env",
    properties=azure_native.app.ConnectedEnvironmentStorageResponsePropertiesArgs(
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
  connectedEnvironmentsStorage:
    type: azure-native:app:ConnectedEnvironmentsStorage
    properties:
      connectedEnvironmentName: env
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
$ pulumi import azure-native:app:ConnectedEnvironmentsStorage jlaw-demo1 /subscriptions/8efdecc5-919e-44eb-b179-915dca89ebf9/resourceGroups/examplerg/providers/Microsoft.App/connectedEnvironments/env/storages/jlaw-demo1 
```
