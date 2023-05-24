A sensitivity label.
API Version: 2021-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Updates the sensitivity label of a given column with all parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlPoolSensitivityLabel = new AzureNative.Synapse.SqlPoolSensitivityLabel("sqlPoolSensitivityLabel", new()
    {
        ColumnName = "myColumn",
        InformationType = "PhoneNumber",
        InformationTypeId = "d22fa6e9-5ee4-3bde-4c2b-a409604c4646",
        LabelId = "bf91e08c-f4f0-478a-b016-25164b2a65ff",
        LabelName = "PII",
        ResourceGroupName = "myRG",
        SchemaName = "dbo",
        SensitivityLabelSource = "current",
        SqlPoolName = "myDatabase",
        TableName = "myTable",
        WorkspaceName = "myServer",
    });

});


```

```go
package main

import (
	synapse "github.com/pulumi/pulumi-azure-native-sdk/synapse"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := synapse.NewSqlPoolSensitivityLabel(ctx, "sqlPoolSensitivityLabel", &synapse.SqlPoolSensitivityLabelArgs{
			ColumnName:             pulumi.String("myColumn"),
			InformationType:        pulumi.String("PhoneNumber"),
			InformationTypeId:      pulumi.String("d22fa6e9-5ee4-3bde-4c2b-a409604c4646"),
			LabelId:                pulumi.String("bf91e08c-f4f0-478a-b016-25164b2a65ff"),
			LabelName:              pulumi.String("PII"),
			ResourceGroupName:      pulumi.String("myRG"),
			SchemaName:             pulumi.String("dbo"),
			SensitivityLabelSource: pulumi.String("current"),
			SqlPoolName:            pulumi.String("myDatabase"),
			TableName:              pulumi.String("myTable"),
			WorkspaceName:          pulumi.String("myServer"),
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
import com.pulumi.azurenative.synapse.SqlPoolSensitivityLabel;
import com.pulumi.azurenative.synapse.SqlPoolSensitivityLabelArgs;
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
        var sqlPoolSensitivityLabel = new SqlPoolSensitivityLabel("sqlPoolSensitivityLabel", SqlPoolSensitivityLabelArgs.builder()        
            .columnName("myColumn")
            .informationType("PhoneNumber")
            .informationTypeId("d22fa6e9-5ee4-3bde-4c2b-a409604c4646")
            .labelId("bf91e08c-f4f0-478a-b016-25164b2a65ff")
            .labelName("PII")
            .resourceGroupName("myRG")
            .schemaName("dbo")
            .sensitivityLabelSource("current")
            .sqlPoolName("myDatabase")
            .tableName("myTable")
            .workspaceName("myServer")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlPoolSensitivityLabel = new azure_native.synapse.SqlPoolSensitivityLabel("sqlPoolSensitivityLabel", {
    columnName: "myColumn",
    informationType: "PhoneNumber",
    informationTypeId: "d22fa6e9-5ee4-3bde-4c2b-a409604c4646",
    labelId: "bf91e08c-f4f0-478a-b016-25164b2a65ff",
    labelName: "PII",
    resourceGroupName: "myRG",
    schemaName: "dbo",
    sensitivityLabelSource: "current",
    sqlPoolName: "myDatabase",
    tableName: "myTable",
    workspaceName: "myServer",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_pool_sensitivity_label = azure_native.synapse.SqlPoolSensitivityLabel("sqlPoolSensitivityLabel",
    column_name="myColumn",
    information_type="PhoneNumber",
    information_type_id="d22fa6e9-5ee4-3bde-4c2b-a409604c4646",
    label_id="bf91e08c-f4f0-478a-b016-25164b2a65ff",
    label_name="PII",
    resource_group_name="myRG",
    schema_name="dbo",
    sensitivity_label_source="current",
    sql_pool_name="myDatabase",
    table_name="myTable",
    workspace_name="myServer")

```

```yaml
resources:
  sqlPoolSensitivityLabel:
    type: azure-native:synapse:SqlPoolSensitivityLabel
    properties:
      columnName: myColumn
      informationType: PhoneNumber
      informationTypeId: d22fa6e9-5ee4-3bde-4c2b-a409604c4646
      labelId: bf91e08c-f4f0-478a-b016-25164b2a65ff
      labelName: PII
      resourceGroupName: myRG
      schemaName: dbo
      sensitivityLabelSource: current
      sqlPoolName: myDatabase
      tableName: myTable
      workspaceName: myServer

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:synapse:SqlPoolSensitivityLabel current /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/myRG/providers/Microsoft.Synapse/workspaces/myServer/sqlPools/myDatabase/schemas/dbo/tables/myTable/columns/myColumn/sensitivityLabels/current 
```
