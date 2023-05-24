A favorite process identifier.
API Version: 2022-04-01-preview.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### FavoriteProcessCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var favoriteProcess = new AzureNative.TestBase.FavoriteProcess("favoriteProcess", new()
    {
        ActualProcessName = "testApp&.exe",
        FavoriteProcessResourceName = "testAppProcess",
        PackageName = "contoso-package2",
        ResourceGroupName = "contoso-rg1",
        TestBaseAccountName = "contoso-testBaseAccount1",
    });

});


```

```go
package main

import (
	testbase "github.com/pulumi/pulumi-azure-native-sdk/testbase"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := testbase.NewFavoriteProcess(ctx, "favoriteProcess", &testbase.FavoriteProcessArgs{
			ActualProcessName:           pulumi.String("testApp&.exe"),
			FavoriteProcessResourceName: pulumi.String("testAppProcess"),
			PackageName:                 pulumi.String("contoso-package2"),
			ResourceGroupName:           pulumi.String("contoso-rg1"),
			TestBaseAccountName:         pulumi.String("contoso-testBaseAccount1"),
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
import com.pulumi.azurenative.testbase.FavoriteProcess;
import com.pulumi.azurenative.testbase.FavoriteProcessArgs;
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
        var favoriteProcess = new FavoriteProcess("favoriteProcess", FavoriteProcessArgs.builder()        
            .actualProcessName("testApp&.exe")
            .favoriteProcessResourceName("testAppProcess")
            .packageName("contoso-package2")
            .resourceGroupName("contoso-rg1")
            .testBaseAccountName("contoso-testBaseAccount1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const favoriteProcess = new azure_native.testbase.FavoriteProcess("favoriteProcess", {
    actualProcessName: "testApp&.exe",
    favoriteProcessResourceName: "testAppProcess",
    packageName: "contoso-package2",
    resourceGroupName: "contoso-rg1",
    testBaseAccountName: "contoso-testBaseAccount1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

favorite_process = azure_native.testbase.FavoriteProcess("favoriteProcess",
    actual_process_name="testApp&.exe",
    favorite_process_resource_name="testAppProcess",
    package_name="contoso-package2",
    resource_group_name="contoso-rg1",
    test_base_account_name="contoso-testBaseAccount1")

```

```yaml
resources:
  favoriteProcess:
    type: azure-native:testbase:FavoriteProcess
    properties:
      actualProcessName: testApp&.exe
      favoriteProcessResourceName: testAppProcess
      packageName: contoso-package2
      resourceGroupName: contoso-rg1
      testBaseAccountName: contoso-testBaseAccount1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:testbase:FavoriteProcess testAppProcess /subscriptions/subscription-id/resourceGroups/contoso-rg1/providers/Microsoft.TestBase/testBaseAccounts/contoso-testBaseAccount1/packages/contoso-package2/favoriteProcesses/testAppProcess 
```
