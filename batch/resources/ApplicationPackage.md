An application package which represents a particular version of an application.
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApplicationPackageCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var applicationPackage = new AzureNative.Batch.ApplicationPackage("applicationPackage", new()
    {
        AccountName = "sampleacct",
        ApplicationName = "app1",
        ResourceGroupName = "default-azurebatch-japaneast",
        VersionName = "1",
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
		_, err := batch.NewApplicationPackage(ctx, "applicationPackage", &batch.ApplicationPackageArgs{
			AccountName:       pulumi.String("sampleacct"),
			ApplicationName:   pulumi.String("app1"),
			ResourceGroupName: pulumi.String("default-azurebatch-japaneast"),
			VersionName:       pulumi.String("1"),
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
import com.pulumi.azurenative.batch.ApplicationPackage;
import com.pulumi.azurenative.batch.ApplicationPackageArgs;
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
        var applicationPackage = new ApplicationPackage("applicationPackage", ApplicationPackageArgs.builder()        
            .accountName("sampleacct")
            .applicationName("app1")
            .resourceGroupName("default-azurebatch-japaneast")
            .versionName("1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const applicationPackage = new azure_native.batch.ApplicationPackage("applicationPackage", {
    accountName: "sampleacct",
    applicationName: "app1",
    resourceGroupName: "default-azurebatch-japaneast",
    versionName: "1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application_package = azure_native.batch.ApplicationPackage("applicationPackage",
    account_name="sampleacct",
    application_name="app1",
    resource_group_name="default-azurebatch-japaneast",
    version_name="1")

```

```yaml
resources:
  applicationPackage:
    type: azure-native:batch:ApplicationPackage
    properties:
      accountName: sampleacct
      applicationName: app1
      resourceGroupName: default-azurebatch-japaneast
      versionName: '1'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:batch:ApplicationPackage 1 /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/applications/app1/versions/1 
```
