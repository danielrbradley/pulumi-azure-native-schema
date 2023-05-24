AzureStorageInfo dictionary resource.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update Azure Storage Accounts
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webAppAzureStorageAccounts = new AzureNative.Web.WebAppAzureStorageAccounts("webAppAzureStorageAccounts", new()
    {
        Name = "sitef6141",
        Properties = 
        {
            { "account1", new AzureNative.Web.Inputs.AzureStorageInfoValueArgs
            {
                AccessKey = "26515^%@#*",
                AccountName = "testsa",
                MountPath = "/mounts/a/files",
                ShareName = "web",
                Type = AzureNative.Web.AzureStorageType.AzureFiles,
            } },
        },
        ResourceGroupName = "testrg123",
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewWebAppAzureStorageAccounts(ctx, "webAppAzureStorageAccounts", &web.WebAppAzureStorageAccountsArgs{
			Name: pulumi.String("sitef6141"),
			Properties: web.AzureStorageInfoValueMap{
				"account1": &web.AzureStorageInfoValueArgs{
					AccessKey:   pulumi.String("26515^%@#*"),
					AccountName: pulumi.String("testsa"),
					MountPath:   pulumi.String("/mounts/a/files"),
					ShareName:   pulumi.String("web"),
					Type:        web.AzureStorageTypeAzureFiles,
				},
			},
			ResourceGroupName: pulumi.String("testrg123"),
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
import com.pulumi.azurenative.web.WebAppAzureStorageAccounts;
import com.pulumi.azurenative.web.WebAppAzureStorageAccountsArgs;
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
        var webAppAzureStorageAccounts = new WebAppAzureStorageAccounts("webAppAzureStorageAccounts", WebAppAzureStorageAccountsArgs.builder()        
            .name("sitef6141")
            .properties(Map.of("account1", Map.ofEntries(
                Map.entry("accessKey", "26515^%@#*"),
                Map.entry("accountName", "testsa"),
                Map.entry("mountPath", "/mounts/a/files"),
                Map.entry("shareName", "web"),
                Map.entry("type", "AzureFiles")
            )))
            .resourceGroupName("testrg123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webAppAzureStorageAccounts = new azure_native.web.WebAppAzureStorageAccounts("webAppAzureStorageAccounts", {
    name: "sitef6141",
    properties: {
        account1: {
            accessKey: "26515^%@#*",
            accountName: "testsa",
            mountPath: "/mounts/a/files",
            shareName: "web",
            type: azure_native.web.AzureStorageType.AzureFiles,
        },
    },
    resourceGroupName: "testrg123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_app_azure_storage_accounts = azure_native.web.WebAppAzureStorageAccounts("webAppAzureStorageAccounts",
    name="sitef6141",
    properties={
        "account1": azure_native.web.AzureStorageInfoValueArgs(
            access_key="26515^%@#*",
            account_name="testsa",
            mount_path="/mounts/a/files",
            share_name="web",
            type=azure_native.web.AzureStorageType.AZURE_FILES,
        ),
    },
    resource_group_name="testrg123")

```

```yaml
resources:
  webAppAzureStorageAccounts:
    type: azure-native:web:WebAppAzureStorageAccounts
    properties:
      name: sitef6141
      properties:
        account1:
          accessKey: 26515^%@#*
          accountName: testsa
          mountPath: /mounts/a/files
          shareName: web
          type: AzureFiles
      resourceGroupName: testrg123

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:WebAppAzureStorageAccounts web /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/sites/sitef6141/config/web 
```
