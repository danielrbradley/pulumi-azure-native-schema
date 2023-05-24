A sensitivity label.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var sensitivityLabel = new AzureNative.Sql.SensitivityLabel("sensitivityLabel", new()
    {
        ColumnName = "myColumn",
        DatabaseName = "myDatabase",
        InformationType = "PhoneNumber",
        InformationTypeId = "d22fa6e9-5ee4-3bde-4c2b-a409604c4646",
        LabelId = "bf91e08c-f4f0-478a-b016-25164b2a65ff",
        LabelName = "PII",
        Rank = AzureNative.Sql.SensitivityLabelRank.Low,
        ResourceGroupName = "myRG",
        SchemaName = "dbo",
        SensitivityLabelSource = "current",
        ServerName = "myServer",
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
		_, err := sql.NewSensitivityLabel(ctx, "sensitivityLabel", &sql.SensitivityLabelArgs{
			ColumnName:             pulumi.String("myColumn"),
			DatabaseName:           pulumi.String("myDatabase"),
			InformationType:        pulumi.String("PhoneNumber"),
			InformationTypeId:      pulumi.String("d22fa6e9-5ee4-3bde-4c2b-a409604c4646"),
			LabelId:                pulumi.String("bf91e08c-f4f0-478a-b016-25164b2a65ff"),
			LabelName:              pulumi.String("PII"),
			Rank:                   sql.SensitivityLabelRankLow,
			ResourceGroupName:      pulumi.String("myRG"),
			SchemaName:             pulumi.String("dbo"),
			SensitivityLabelSource: pulumi.String("current"),
			ServerName:             pulumi.String("myServer"),
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
import com.pulumi.azurenative.sql.SensitivityLabel;
import com.pulumi.azurenative.sql.SensitivityLabelArgs;
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
        var sensitivityLabel = new SensitivityLabel("sensitivityLabel", SensitivityLabelArgs.builder()        
            .columnName("myColumn")
            .databaseName("myDatabase")
            .informationType("PhoneNumber")
            .informationTypeId("d22fa6e9-5ee4-3bde-4c2b-a409604c4646")
            .labelId("bf91e08c-f4f0-478a-b016-25164b2a65ff")
            .labelName("PII")
            .rank("Low")
            .resourceGroupName("myRG")
            .schemaName("dbo")
            .sensitivityLabelSource("current")
            .serverName("myServer")
            .tableName("myTable")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sensitivityLabel = new azure_native.sql.SensitivityLabel("sensitivityLabel", {
    columnName: "myColumn",
    databaseName: "myDatabase",
    informationType: "PhoneNumber",
    informationTypeId: "d22fa6e9-5ee4-3bde-4c2b-a409604c4646",
    labelId: "bf91e08c-f4f0-478a-b016-25164b2a65ff",
    labelName: "PII",
    rank: azure_native.sql.SensitivityLabelRank.Low,
    resourceGroupName: "myRG",
    schemaName: "dbo",
    sensitivityLabelSource: "current",
    serverName: "myServer",
    tableName: "myTable",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sensitivity_label = azure_native.sql.SensitivityLabel("sensitivityLabel",
    column_name="myColumn",
    database_name="myDatabase",
    information_type="PhoneNumber",
    information_type_id="d22fa6e9-5ee4-3bde-4c2b-a409604c4646",
    label_id="bf91e08c-f4f0-478a-b016-25164b2a65ff",
    label_name="PII",
    rank=azure_native.sql.SensitivityLabelRank.LOW,
    resource_group_name="myRG",
    schema_name="dbo",
    sensitivity_label_source="current",
    server_name="myServer",
    table_name="myTable")

```

```yaml
resources:
  sensitivityLabel:
    type: azure-native:sql:SensitivityLabel
    properties:
      columnName: myColumn
      databaseName: myDatabase
      informationType: PhoneNumber
      informationTypeId: d22fa6e9-5ee4-3bde-4c2b-a409604c4646
      labelId: bf91e08c-f4f0-478a-b016-25164b2a65ff
      labelName: PII
      rank: Low
      resourceGroupName: myRG
      schemaName: dbo
      sensitivityLabelSource: current
      serverName: myServer
      tableName: myTable

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:SensitivityLabel current /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/myRG/providers/Microsoft.Sql/servers/myServer/databases/myDatabase/schemas/dbo/tables/myTable/columns/myColumn/sensitivityLabels/current 
```
