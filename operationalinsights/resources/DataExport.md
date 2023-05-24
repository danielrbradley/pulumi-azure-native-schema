The top level data export resource container.
API Version: 2020-08-01.
Previous API Version: 2020-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DataExportCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataExport = new AzureNative.OperationalInsights.DataExport("dataExport", new()
    {
        DataExportName = "export1",
        ResourceGroupName = "RgTest1",
        ResourceId = "/subscriptions/192b9f85-a39a-4276-b96d-d5cd351703f9/resourceGroups/OIAutoRest1234/providers/Microsoft.EventHub/namespaces/test",
        TableNames = new[]
        {
            "Heartbeat",
        },
        WorkspaceName = "DeWnTest1234",
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
		_, err := operationalinsights.NewDataExport(ctx, "dataExport", &operationalinsights.DataExportArgs{
			DataExportName:    pulumi.String("export1"),
			ResourceGroupName: pulumi.String("RgTest1"),
			ResourceId:        pulumi.String("/subscriptions/192b9f85-a39a-4276-b96d-d5cd351703f9/resourceGroups/OIAutoRest1234/providers/Microsoft.EventHub/namespaces/test"),
			TableNames: pulumi.StringArray{
				pulumi.String("Heartbeat"),
			},
			WorkspaceName: pulumi.String("DeWnTest1234"),
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
import com.pulumi.azurenative.operationalinsights.DataExport;
import com.pulumi.azurenative.operationalinsights.DataExportArgs;
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
        var dataExport = new DataExport("dataExport", DataExportArgs.builder()        
            .dataExportName("export1")
            .resourceGroupName("RgTest1")
            .resourceId("/subscriptions/192b9f85-a39a-4276-b96d-d5cd351703f9/resourceGroups/OIAutoRest1234/providers/Microsoft.EventHub/namespaces/test")
            .tableNames("Heartbeat")
            .workspaceName("DeWnTest1234")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataExport = new azure_native.operationalinsights.DataExport("dataExport", {
    dataExportName: "export1",
    resourceGroupName: "RgTest1",
    resourceId: "/subscriptions/192b9f85-a39a-4276-b96d-d5cd351703f9/resourceGroups/OIAutoRest1234/providers/Microsoft.EventHub/namespaces/test",
    tableNames: ["Heartbeat"],
    workspaceName: "DeWnTest1234",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_export = azure_native.operationalinsights.DataExport("dataExport",
    data_export_name="export1",
    resource_group_name="RgTest1",
    resource_id="/subscriptions/192b9f85-a39a-4276-b96d-d5cd351703f9/resourceGroups/OIAutoRest1234/providers/Microsoft.EventHub/namespaces/test",
    table_names=["Heartbeat"],
    workspace_name="DeWnTest1234")

```

```yaml
resources:
  dataExport:
    type: azure-native:operationalinsights:DataExport
    properties:
      dataExportName: export1
      resourceGroupName: RgTest1
      resourceId: /subscriptions/192b9f85-a39a-4276-b96d-d5cd351703f9/resourceGroups/OIAutoRest1234/providers/Microsoft.EventHub/namespaces/test
      tableNames:
        - Heartbeat
      workspaceName: DeWnTest1234

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationalinsights:DataExport export1 /subscriptions/00000000-0000-0000-0000-00000000000/resourcegroups/RgTest1/providers/microsoft.operationalinsights/workspaces/DeWnTest1234/export/export1 
```
