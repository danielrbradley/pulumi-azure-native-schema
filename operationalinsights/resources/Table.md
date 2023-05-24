Workspace data table definition.
API Version: 2022-10-01.
Previous API Version: 2021-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### TablesUpsert
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var table = new AzureNative.OperationalInsights.Table("table", new()
    {
        ResourceGroupName = "oiautorest6685",
        RetentionInDays = 45,
        Schema = new AzureNative.OperationalInsights.Inputs.SchemaArgs
        {
            Columns = new[]
            {
                new AzureNative.OperationalInsights.Inputs.ColumnArgs
                {
                    Name = "MyNewColumn",
                    Type = "guid",
                },
            },
            Name = "AzureNetworkFlow",
        },
        TableName = "AzureNetworkFlow",
        TotalRetentionInDays = 70,
        WorkspaceName = "oiautorest6685",
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
		_, err := operationalinsights.NewTable(ctx, "table", &operationalinsights.TableArgs{
			ResourceGroupName: pulumi.String("oiautorest6685"),
			RetentionInDays:   pulumi.Int(45),
			Schema: operationalinsights.SchemaResponse{
				Columns: operationalinsights.ColumnArray{
					&operationalinsights.ColumnArgs{
						Name: pulumi.String("MyNewColumn"),
						Type: pulumi.String("guid"),
					},
				},
				Name: pulumi.String("AzureNetworkFlow"),
			},
			TableName:            pulumi.String("AzureNetworkFlow"),
			TotalRetentionInDays: pulumi.Int(70),
			WorkspaceName:        pulumi.String("oiautorest6685"),
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
import com.pulumi.azurenative.operationalinsights.Table;
import com.pulumi.azurenative.operationalinsights.TableArgs;
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
        var table = new Table("table", TableArgs.builder()        
            .resourceGroupName("oiautorest6685")
            .retentionInDays(45)
            .schema(Map.ofEntries(
                Map.entry("columns", Map.ofEntries(
                    Map.entry("name", "MyNewColumn"),
                    Map.entry("type", "guid")
                )),
                Map.entry("name", "AzureNetworkFlow")
            ))
            .tableName("AzureNetworkFlow")
            .totalRetentionInDays(70)
            .workspaceName("oiautorest6685")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const table = new azure_native.operationalinsights.Table("table", {
    resourceGroupName: "oiautorest6685",
    retentionInDays: 45,
    schema: {
        columns: [{
            name: "MyNewColumn",
            type: "guid",
        }],
        name: "AzureNetworkFlow",
    },
    tableName: "AzureNetworkFlow",
    totalRetentionInDays: 70,
    workspaceName: "oiautorest6685",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

table = azure_native.operationalinsights.Table("table",
    resource_group_name="oiautorest6685",
    retention_in_days=45,
    schema=azure_native.operationalinsights.SchemaResponseArgs(
        columns=[azure_native.operationalinsights.ColumnArgs(
            name="MyNewColumn",
            type="guid",
        )],
        name="AzureNetworkFlow",
    ),
    table_name="AzureNetworkFlow",
    total_retention_in_days=70,
    workspace_name="oiautorest6685")

```

```yaml
resources:
  table:
    type: azure-native:operationalinsights:Table
    properties:
      resourceGroupName: oiautorest6685
      retentionInDays: 45
      schema:
        columns:
          - name: MyNewColumn
            type: guid
        name: AzureNetworkFlow
      tableName: AzureNetworkFlow
      totalRetentionInDays: 70
      workspaceName: oiautorest6685

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationalinsights:Table AzureNetworkFlow /subscriptions/00000000-0000-0000-0000-00000000000/resourcegroups/oiautorest6685/providers/Microsoft.OperationalInsights/workspaces/oiautorest6685/tables/AzureNetworkFlow 
```
