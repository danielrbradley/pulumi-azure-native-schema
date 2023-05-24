The top level storage insight resource container.
API Version: 2020-08-01.
Previous API Version: 2020-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StorageInsightsCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storageInsightConfig = new AzureNative.OperationalInsights.StorageInsightConfig("storageInsightConfig", new()
    {
        Containers = new[]
        {
            "wad-iis-logfiles",
        },
        ResourceGroupName = "OIAutoRest5123",
        StorageAccount = new AzureNative.OperationalInsights.Inputs.StorageAccountArgs
        {
            Id = "/subscriptions/00000000-0000-0000-0000-000000000005/resourcegroups/OIAutoRest6987/providers/microsoft.storage/storageaccounts/AzTestFakeSA9945",
            Key = "1234",
        },
        StorageInsightName = "AzTestSI1110",
        Tables = new[]
        {
            "WADWindowsEventLogsTable",
            "LinuxSyslogVer2v0",
        },
        WorkspaceName = "aztest5048",
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
		_, err := operationalinsights.NewStorageInsightConfig(ctx, "storageInsightConfig", &operationalinsights.StorageInsightConfigArgs{
			Containers: pulumi.StringArray{
				pulumi.String("wad-iis-logfiles"),
			},
			ResourceGroupName: pulumi.String("OIAutoRest5123"),
			StorageAccount: &operationalinsights.StorageAccountArgs{
				Id:  pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000005/resourcegroups/OIAutoRest6987/providers/microsoft.storage/storageaccounts/AzTestFakeSA9945"),
				Key: pulumi.String("1234"),
			},
			StorageInsightName: pulumi.String("AzTestSI1110"),
			Tables: pulumi.StringArray{
				pulumi.String("WADWindowsEventLogsTable"),
				pulumi.String("LinuxSyslogVer2v0"),
			},
			WorkspaceName: pulumi.String("aztest5048"),
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
import com.pulumi.azurenative.operationalinsights.StorageInsightConfig;
import com.pulumi.azurenative.operationalinsights.StorageInsightConfigArgs;
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
        var storageInsightConfig = new StorageInsightConfig("storageInsightConfig", StorageInsightConfigArgs.builder()        
            .containers("wad-iis-logfiles")
            .resourceGroupName("OIAutoRest5123")
            .storageAccount(Map.ofEntries(
                Map.entry("id", "/subscriptions/00000000-0000-0000-0000-000000000005/resourcegroups/OIAutoRest6987/providers/microsoft.storage/storageaccounts/AzTestFakeSA9945"),
                Map.entry("key", "1234")
            ))
            .storageInsightName("AzTestSI1110")
            .tables(            
                "WADWindowsEventLogsTable",
                "LinuxSyslogVer2v0")
            .workspaceName("aztest5048")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storageInsightConfig = new azure_native.operationalinsights.StorageInsightConfig("storageInsightConfig", {
    containers: ["wad-iis-logfiles"],
    resourceGroupName: "OIAutoRest5123",
    storageAccount: {
        id: "/subscriptions/00000000-0000-0000-0000-000000000005/resourcegroups/OIAutoRest6987/providers/microsoft.storage/storageaccounts/AzTestFakeSA9945",
        key: "1234",
    },
    storageInsightName: "AzTestSI1110",
    tables: [
        "WADWindowsEventLogsTable",
        "LinuxSyslogVer2v0",
    ],
    workspaceName: "aztest5048",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage_insight_config = azure_native.operationalinsights.StorageInsightConfig("storageInsightConfig",
    containers=["wad-iis-logfiles"],
    resource_group_name="OIAutoRest5123",
    storage_account=azure_native.operationalinsights.StorageAccountArgs(
        id="/subscriptions/00000000-0000-0000-0000-000000000005/resourcegroups/OIAutoRest6987/providers/microsoft.storage/storageaccounts/AzTestFakeSA9945",
        key="1234",
    ),
    storage_insight_name="AzTestSI1110",
    tables=[
        "WADWindowsEventLogsTable",
        "LinuxSyslogVer2v0",
    ],
    workspace_name="aztest5048")

```

```yaml
resources:
  storageInsightConfig:
    type: azure-native:operationalinsights:StorageInsightConfig
    properties:
      containers:
        - wad-iis-logfiles
      resourceGroupName: OIAutoRest5123
      storageAccount:
        id: /subscriptions/00000000-0000-0000-0000-000000000005/resourcegroups/OIAutoRest6987/providers/microsoft.storage/storageaccounts/AzTestFakeSA9945
        key: '1234'
      storageInsightName: AzTestSI1110
      tables:
        - WADWindowsEventLogsTable
        - LinuxSyslogVer2v0
      workspaceName: aztest5048

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationalinsights:StorageInsightConfig AzTestSI1110 /subscriptions/00000000-0000-0000-0000-000000000005/resourcegroups/oiautorest6987/providers/microsoft.operationalinsights/workspaces/aztest5048/storageinsightconfigs/AzTestSI1110 
```
