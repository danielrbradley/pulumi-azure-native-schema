Contains information about an application in a Batch account.
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApplicationCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var application = new AzureNative.Batch.Application("application", new()
    {
        AccountName = "sampleacct",
        AllowUpdates = false,
        ApplicationName = "app1",
        DisplayName = "myAppName",
        ResourceGroupName = "default-azurebatch-japaneast",
    });

});


```

```go
package main

import (
	batch "github.com/pulumi/pulumi-azure-native-sdk/batch"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := batch.NewApplication(ctx, "application", &batch.ApplicationArgs{
			AccountName:       pulumi.String("sampleacct"),
			AllowUpdates:      pulumi.Bool(false),
			ApplicationName:   pulumi.String("app1"),
			DisplayName:       pulumi.String("myAppName"),
			ResourceGroupName: pulumi.String("default-azurebatch-japaneast"),
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
import com.pulumi.azurenative.batch.Application;
import com.pulumi.azurenative.batch.ApplicationArgs;
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
        var application = new Application("application", ApplicationArgs.builder()        
            .accountName("sampleacct")
            .allowUpdates(false)
            .applicationName("app1")
            .displayName("myAppName")
            .resourceGroupName("default-azurebatch-japaneast")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const application = new azure_native.batch.Application("application", {
    accountName: "sampleacct",
    allowUpdates: false,
    applicationName: "app1",
    displayName: "myAppName",
    resourceGroupName: "default-azurebatch-japaneast",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application = azure_native.batch.Application("application",
    account_name="sampleacct",
    allow_updates=False,
    application_name="app1",
    display_name="myAppName",
    resource_group_name="default-azurebatch-japaneast")

```

```yaml
resources:
  application:
    type: azure-native:batch:Application
    properties:
      accountName: sampleacct
      allowUpdates: false
      applicationName: app1
      displayName: myAppName
      resourceGroupName: default-azurebatch-japaneast

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:batch:Application app1 /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/applications/app1 
```
