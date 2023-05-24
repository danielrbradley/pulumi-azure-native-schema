Linked storage accounts top level resource container.
API Version: 2020-08-01.
Previous API Version: 2020-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### LinkedStorageAccountsCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var linkedStorageAccount = new AzureNative.OperationalInsights.LinkedStorageAccount("linkedStorageAccount", new()
    {
        DataSourceType = "CustomLogs",
        ResourceGroupName = "mms-eus",
        StorageAccountIds = new[]
        {
            "/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageA",
            "/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageB",
        },
        WorkspaceName = "testLinkStorageAccountsWS",
    });

});


```

```go
package main

import (
	operationalinsights "github.com/pulumi/pulumi-azure-native-sdk/operationalinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := operationalinsights.NewLinkedStorageAccount(ctx, "linkedStorageAccount", &operationalinsights.LinkedStorageAccountArgs{
			DataSourceType:    pulumi.String("CustomLogs"),
			ResourceGroupName: pulumi.String("mms-eus"),
			StorageAccountIds: pulumi.StringArray{
				pulumi.String("/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageA"),
				pulumi.String("/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageB"),
			},
			WorkspaceName: pulumi.String("testLinkStorageAccountsWS"),
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
import com.pulumi.azurenative.operationalinsights.LinkedStorageAccount;
import com.pulumi.azurenative.operationalinsights.LinkedStorageAccountArgs;
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
        var linkedStorageAccount = new LinkedStorageAccount("linkedStorageAccount", LinkedStorageAccountArgs.builder()        
            .dataSourceType("CustomLogs")
            .resourceGroupName("mms-eus")
            .storageAccountIds(            
                "/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageA",
                "/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageB")
            .workspaceName("testLinkStorageAccountsWS")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const linkedStorageAccount = new azure_native.operationalinsights.LinkedStorageAccount("linkedStorageAccount", {
    dataSourceType: "CustomLogs",
    resourceGroupName: "mms-eus",
    storageAccountIds: [
        "/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageA",
        "/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageB",
    ],
    workspaceName: "testLinkStorageAccountsWS",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

linked_storage_account = azure_native.operationalinsights.LinkedStorageAccount("linkedStorageAccount",
    data_source_type="CustomLogs",
    resource_group_name="mms-eus",
    storage_account_ids=[
        "/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageA",
        "/subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageB",
    ],
    workspace_name="testLinkStorageAccountsWS")

```

```yaml
resources:
  linkedStorageAccount:
    type: azure-native:operationalinsights:LinkedStorageAccount
    properties:
      dataSourceType: CustomLogs
      resourceGroupName: mms-eus
      storageAccountIds:
        - /subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageA
        - /subscriptions/00000000-0000-0000-0000-00000000000/resourceGroups/mms-eus/providers/Microsoft.Storage/storageAccounts/testStorageB
      workspaceName: testLinkStorageAccountsWS

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationalinsights:LinkedStorageAccount CustomLogs /subscriptions/00000000-0000-0000-0000-00000000000/resourcegroups/mms-eus/providers/microsoft.operationalinsights/workspaces/testLinkStorageAccountsWS/linkedStorageAccounts/CustomLogs 
```
