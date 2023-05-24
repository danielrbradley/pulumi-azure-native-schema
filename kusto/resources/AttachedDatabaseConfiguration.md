Class representing an attached database configuration.
API Version: 2022-12-29.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AttachedDatabaseConfigurationsCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var attachedDatabaseConfiguration = new AzureNative.Kusto.AttachedDatabaseConfiguration("attachedDatabaseConfiguration", new()
    {
        AttachedDatabaseConfigurationName = "attachedDatabaseConfigurationsTest",
        ClusterName = "kustoCluster2",
        ClusterResourceId = "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster2",
        DatabaseName = "kustodatabase",
        DatabaseNameOverride = "overridekustodatabase",
        DefaultPrincipalsModificationKind = "Union",
        Location = "westus",
        ResourceGroupName = "kustorptest",
        TableLevelSharingProperties = new AzureNative.Kusto.Inputs.TableLevelSharingPropertiesArgs
        {
            ExternalTablesToExclude = new[]
            {
                "ExternalTable2",
            },
            ExternalTablesToInclude = new[]
            {
                "ExternalTable1",
            },
            MaterializedViewsToExclude = new[]
            {
                "MaterializedViewTable2",
            },
            MaterializedViewsToInclude = new[]
            {
                "MaterializedViewTable1",
            },
            TablesToExclude = new[]
            {
                "Table2",
            },
            TablesToInclude = new[]
            {
                "Table1",
            },
        },
    });

});


```

```go
package main

import (
	kusto "github.com/pulumi/pulumi-azure-native-sdk/kusto"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := kusto.NewAttachedDatabaseConfiguration(ctx, "attachedDatabaseConfiguration", &kusto.AttachedDatabaseConfigurationArgs{
			AttachedDatabaseConfigurationName: pulumi.String("attachedDatabaseConfigurationsTest"),
			ClusterName:                       pulumi.String("kustoCluster2"),
			ClusterResourceId:                 pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster2"),
			DatabaseName:                      pulumi.String("kustodatabase"),
			DatabaseNameOverride:              pulumi.String("overridekustodatabase"),
			DefaultPrincipalsModificationKind: pulumi.String("Union"),
			Location:                          pulumi.String("westus"),
			ResourceGroupName:                 pulumi.String("kustorptest"),
			TableLevelSharingProperties: &kusto.TableLevelSharingPropertiesArgs{
				ExternalTablesToExclude: pulumi.StringArray{
					pulumi.String("ExternalTable2"),
				},
				ExternalTablesToInclude: pulumi.StringArray{
					pulumi.String("ExternalTable1"),
				},
				MaterializedViewsToExclude: pulumi.StringArray{
					pulumi.String("MaterializedViewTable2"),
				},
				MaterializedViewsToInclude: pulumi.StringArray{
					pulumi.String("MaterializedViewTable1"),
				},
				TablesToExclude: pulumi.StringArray{
					pulumi.String("Table2"),
				},
				TablesToInclude: pulumi.StringArray{
					pulumi.String("Table1"),
				},
			},
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
import com.pulumi.azurenative.kusto.AttachedDatabaseConfiguration;
import com.pulumi.azurenative.kusto.AttachedDatabaseConfigurationArgs;
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
        var attachedDatabaseConfiguration = new AttachedDatabaseConfiguration("attachedDatabaseConfiguration", AttachedDatabaseConfigurationArgs.builder()        
            .attachedDatabaseConfigurationName("attachedDatabaseConfigurationsTest")
            .clusterName("kustoCluster2")
            .clusterResourceId("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster2")
            .databaseName("kustodatabase")
            .databaseNameOverride("overridekustodatabase")
            .defaultPrincipalsModificationKind("Union")
            .location("westus")
            .resourceGroupName("kustorptest")
            .tableLevelSharingProperties(Map.ofEntries(
                Map.entry("externalTablesToExclude", "ExternalTable2"),
                Map.entry("externalTablesToInclude", "ExternalTable1"),
                Map.entry("materializedViewsToExclude", "MaterializedViewTable2"),
                Map.entry("materializedViewsToInclude", "MaterializedViewTable1"),
                Map.entry("tablesToExclude", "Table2"),
                Map.entry("tablesToInclude", "Table1")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const attachedDatabaseConfiguration = new azure_native.kusto.AttachedDatabaseConfiguration("attachedDatabaseConfiguration", {
    attachedDatabaseConfigurationName: "attachedDatabaseConfigurationsTest",
    clusterName: "kustoCluster2",
    clusterResourceId: "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster2",
    databaseName: "kustodatabase",
    databaseNameOverride: "overridekustodatabase",
    defaultPrincipalsModificationKind: "Union",
    location: "westus",
    resourceGroupName: "kustorptest",
    tableLevelSharingProperties: {
        externalTablesToExclude: ["ExternalTable2"],
        externalTablesToInclude: ["ExternalTable1"],
        materializedViewsToExclude: ["MaterializedViewTable2"],
        materializedViewsToInclude: ["MaterializedViewTable1"],
        tablesToExclude: ["Table2"],
        tablesToInclude: ["Table1"],
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

attached_database_configuration = azure_native.kusto.AttachedDatabaseConfiguration("attachedDatabaseConfiguration",
    attached_database_configuration_name="attachedDatabaseConfigurationsTest",
    cluster_name="kustoCluster2",
    cluster_resource_id="/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster2",
    database_name="kustodatabase",
    database_name_override="overridekustodatabase",
    default_principals_modification_kind="Union",
    location="westus",
    resource_group_name="kustorptest",
    table_level_sharing_properties=azure_native.kusto.TableLevelSharingPropertiesArgs(
        external_tables_to_exclude=["ExternalTable2"],
        external_tables_to_include=["ExternalTable1"],
        materialized_views_to_exclude=["MaterializedViewTable2"],
        materialized_views_to_include=["MaterializedViewTable1"],
        tables_to_exclude=["Table2"],
        tables_to_include=["Table1"],
    ))

```

```yaml
resources:
  attachedDatabaseConfiguration:
    type: azure-native:kusto:AttachedDatabaseConfiguration
    properties:
      attachedDatabaseConfigurationName: attachedDatabaseConfigurationsTest
      clusterName: kustoCluster2
      clusterResourceId: /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster2
      databaseName: kustodatabase
      databaseNameOverride: overridekustodatabase
      defaultPrincipalsModificationKind: Union
      location: westus
      resourceGroupName: kustorptest
      tableLevelSharingProperties:
        externalTablesToExclude:
          - ExternalTable2
        externalTablesToInclude:
          - ExternalTable1
        materializedViewsToExclude:
          - MaterializedViewTable2
        materializedViewsToInclude:
          - MaterializedViewTable1
        tablesToExclude:
          - Table2
        tablesToInclude:
          - Table1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kusto:AttachedDatabaseConfiguration kustoCluster2/attachedDatabaseConfigurationsTest /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster2/attachedDatabaseConfigurations/attachedDatabaseConfigurationsTest 
```
