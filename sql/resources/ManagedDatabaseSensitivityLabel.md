A sensitivity label.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Updates or creates a sensitivity label of a given column with all parameters in a managed database
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedDatabaseSensitivityLabel = new AzureNative.Sql.ManagedDatabaseSensitivityLabel("managedDatabaseSensitivityLabel", new()
    {
        ColumnName = "myColumn",
        DatabaseName = "myDatabase",
        InformationType = "PhoneNumber",
        InformationTypeId = "d22fa6e9-5ee4-3bde-4c2b-a409604c4646",
        LabelId = "bf91e08c-f4f0-478a-b016-25164b2a65ff",
        LabelName = "PII",
        ManagedInstanceName = "myManagedInstanceName",
        Rank = AzureNative.Sql.SensitivityLabelRank.High,
        ResourceGroupName = "myRG",
        SchemaName = "dbo",
        SensitivityLabelSource = "current",
        TableName = "myTable",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewManagedDatabaseSensitivityLabel(ctx, "managedDatabaseSensitivityLabel", &sql.ManagedDatabaseSensitivityLabelArgs{
			ColumnName:             pulumi.String("myColumn"),
			DatabaseName:           pulumi.String("myDatabase"),
			InformationType:        pulumi.String("PhoneNumber"),
			InformationTypeId:      pulumi.String("d22fa6e9-5ee4-3bde-4c2b-a409604c4646"),
			LabelId:                pulumi.String("bf91e08c-f4f0-478a-b016-25164b2a65ff"),
			LabelName:              pulumi.String("PII"),
			ManagedInstanceName:    pulumi.String("myManagedInstanceName"),
			Rank:                   sql.SensitivityLabelRankHigh,
			ResourceGroupName:      pulumi.String("myRG"),
			SchemaName:             pulumi.String("dbo"),
			SensitivityLabelSource: pulumi.String("current"),
			TableName:              pulumi.String("myTable"),
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
import com.pulumi.azurenative.sql.ManagedDatabaseSensitivityLabel;
import com.pulumi.azurenative.sql.ManagedDatabaseSensitivityLabelArgs;
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
        var managedDatabaseSensitivityLabel = new ManagedDatabaseSensitivityLabel("managedDatabaseSensitivityLabel", ManagedDatabaseSensitivityLabelArgs.builder()        
            .columnName("myColumn")
            .databaseName("myDatabase")
            .informationType("PhoneNumber")
            .informationTypeId("d22fa6e9-5ee4-3bde-4c2b-a409604c4646")
            .labelId("bf91e08c-f4f0-478a-b016-25164b2a65ff")
            .labelName("PII")
            .managedInstanceName("myManagedInstanceName")
            .rank("High")
            .resourceGroupName("myRG")
            .schemaName("dbo")
            .sensitivityLabelSource("current")
            .tableName("myTable")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedDatabaseSensitivityLabel = new azure_native.sql.ManagedDatabaseSensitivityLabel("managedDatabaseSensitivityLabel", {
    columnName: "myColumn",
    databaseName: "myDatabase",
    informationType: "PhoneNumber",
    informationTypeId: "d22fa6e9-5ee4-3bde-4c2b-a409604c4646",
    labelId: "bf91e08c-f4f0-478a-b016-25164b2a65ff",
    labelName: "PII",
    managedInstanceName: "myManagedInstanceName",
    rank: azure_native.sql.SensitivityLabelRank.High,
    resourceGroupName: "myRG",
    schemaName: "dbo",
    sensitivityLabelSource: "current",
    tableName: "myTable",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_database_sensitivity_label = azure_native.sql.ManagedDatabaseSensitivityLabel("managedDatabaseSensitivityLabel",
    column_name="myColumn",
    database_name="myDatabase",
    information_type="PhoneNumber",
    information_type_id="d22fa6e9-5ee4-3bde-4c2b-a409604c4646",
    label_id="bf91e08c-f4f0-478a-b016-25164b2a65ff",
    label_name="PII",
    managed_instance_name="myManagedInstanceName",
    rank=azure_native.sql.SensitivityLabelRank.HIGH,
    resource_group_name="myRG",
    schema_name="dbo",
    sensitivity_label_source="current",
    table_name="myTable")

```

```yaml
resources:
  managedDatabaseSensitivityLabel:
    type: azure-native:sql:ManagedDatabaseSensitivityLabel
    properties:
      columnName: myColumn
      databaseName: myDatabase
      informationType: PhoneNumber
      informationTypeId: d22fa6e9-5ee4-3bde-4c2b-a409604c4646
      labelId: bf91e08c-f4f0-478a-b016-25164b2a65ff
      labelName: PII
      managedInstanceName: myManagedInstanceName
      rank: High
      resourceGroupName: myRG
      schemaName: dbo
      sensitivityLabelSource: current
      tableName: myTable

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ManagedDatabaseSensitivityLabel current /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/myRG/providers/Microsoft.Sql/managedInstances/myManagedInstanceName/databases/myDatabase/schemas/dbo/tables/myTable/columns/myColumn/sensitivityLabels/current 
```
