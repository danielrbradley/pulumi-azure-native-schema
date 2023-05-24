A SQL Analytics pool
API Version: 2021-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a SQL Analytics pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlPool = new AzureNative.Synapse.SqlPool("sqlPool", new()
    {
        Collation = "",
        CreateMode = "",
        Location = "Southeast Asia",
        MaxSizeBytes = 0,
        RecoverableDatabaseId = "",
        ResourceGroupName = "ExampleResourceGroup",
        Sku = new AzureNative.Synapse.Inputs.SkuArgs
        {
            Name = "",
            Tier = "",
        },
        SourceDatabaseId = "",
        SqlPoolName = "ExampleSqlPool",
        StorageAccountType = "LRS",
        Tags = null,
        WorkspaceName = "ExampleWorkspace",
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
		_, err := synapse.NewSqlPool(ctx, "sqlPool", &synapse.SqlPoolArgs{
			Collation:             pulumi.String(""),
			CreateMode:            pulumi.String(""),
			Location:              pulumi.String("Southeast Asia"),
			MaxSizeBytes:          pulumi.Float64(0),
			RecoverableDatabaseId: pulumi.String(""),
			ResourceGroupName:     pulumi.String("ExampleResourceGroup"),
			Sku: &synapse.SkuArgs{
				Name: pulumi.String(""),
				Tier: pulumi.String(""),
			},
			SourceDatabaseId:   pulumi.String(""),
			SqlPoolName:        pulumi.String("ExampleSqlPool"),
			StorageAccountType: pulumi.String("LRS"),
			Tags:               nil,
			WorkspaceName:      pulumi.String("ExampleWorkspace"),
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
import com.pulumi.azurenative.synapse.SqlPool;
import com.pulumi.azurenative.synapse.SqlPoolArgs;
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
        var sqlPool = new SqlPool("sqlPool", SqlPoolArgs.builder()        
            .collation("")
            .createMode("")
            .location("Southeast Asia")
            .maxSizeBytes(0)
            .recoverableDatabaseId("")
            .resourceGroupName("ExampleResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("name", ""),
                Map.entry("tier", "")
            ))
            .sourceDatabaseId("")
            .sqlPoolName("ExampleSqlPool")
            .storageAccountType("LRS")
            .tags()
            .workspaceName("ExampleWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlPool = new azure_native.synapse.SqlPool("sqlPool", {
    collation: "",
    createMode: "",
    location: "Southeast Asia",
    maxSizeBytes: 0,
    recoverableDatabaseId: "",
    resourceGroupName: "ExampleResourceGroup",
    sku: {
        name: "",
        tier: "",
    },
    sourceDatabaseId: "",
    sqlPoolName: "ExampleSqlPool",
    storageAccountType: "LRS",
    tags: {},
    workspaceName: "ExampleWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_pool = azure_native.synapse.SqlPool("sqlPool",
    collation="",
    create_mode="",
    location="Southeast Asia",
    max_size_bytes=0,
    recoverable_database_id="",
    resource_group_name="ExampleResourceGroup",
    sku=azure_native.synapse.SkuArgs(
        name="",
        tier="",
    ),
    source_database_id="",
    sql_pool_name="ExampleSqlPool",
    storage_account_type="LRS",
    tags={},
    workspace_name="ExampleWorkspace")

```

```yaml
resources:
  sqlPool:
    type: azure-native:synapse:SqlPool
    properties:
      collation:
      createMode:
      location: Southeast Asia
      maxSizeBytes: 0
      recoverableDatabaseId:
      resourceGroupName: ExampleResourceGroup
      sku:
        name:
        tier:
      sourceDatabaseId:
      sqlPoolName: ExampleSqlPool
      storageAccountType: LRS
      tags: {}
      workspaceName: ExampleWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:synapse:SqlPool ExampleSqlPool /subscriptions/01234567-89ab-4def-0123-456789abcdef/resourceGroups/ExampleResourceGroup/providers/Microsoft.Synapse/workspaces/ExampleWorkspaces/sqlPools/ExampleSqlPool 
```
