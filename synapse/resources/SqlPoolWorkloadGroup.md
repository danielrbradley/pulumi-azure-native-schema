Workload group operations for a sql pool
API Version: 2021-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a workload group with all properties specified.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlPoolWorkloadGroup = new AzureNative.Synapse.SqlPoolWorkloadGroup("sqlPoolWorkloadGroup", new()
    {
        Importance = "normal",
        MaxResourcePercent = 100,
        MaxResourcePercentPerRequest = 3,
        MinResourcePercent = 0,
        MinResourcePercentPerRequest = 3,
        QueryExecutionTimeout = 0,
        ResourceGroupName = "sqlcrudtest-6852",
        SqlPoolName = "sqlcrudtest-9187",
        WorkloadGroupName = "smallrc",
        WorkspaceName = "sqlcrudtest-2080",
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
		_, err := synapse.NewSqlPoolWorkloadGroup(ctx, "sqlPoolWorkloadGroup", &synapse.SqlPoolWorkloadGroupArgs{
			Importance:                   pulumi.String("normal"),
			MaxResourcePercent:           pulumi.Int(100),
			MaxResourcePercentPerRequest: pulumi.Float64(3),
			MinResourcePercent:           pulumi.Int(0),
			MinResourcePercentPerRequest: pulumi.Float64(3),
			QueryExecutionTimeout:        pulumi.Int(0),
			ResourceGroupName:            pulumi.String("sqlcrudtest-6852"),
			SqlPoolName:                  pulumi.String("sqlcrudtest-9187"),
			WorkloadGroupName:            pulumi.String("smallrc"),
			WorkspaceName:                pulumi.String("sqlcrudtest-2080"),
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
import com.pulumi.azurenative.synapse.SqlPoolWorkloadGroup;
import com.pulumi.azurenative.synapse.SqlPoolWorkloadGroupArgs;
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
        var sqlPoolWorkloadGroup = new SqlPoolWorkloadGroup("sqlPoolWorkloadGroup", SqlPoolWorkloadGroupArgs.builder()        
            .importance("normal")
            .maxResourcePercent(100)
            .maxResourcePercentPerRequest(3)
            .minResourcePercent(0)
            .minResourcePercentPerRequest(3)
            .queryExecutionTimeout(0)
            .resourceGroupName("sqlcrudtest-6852")
            .sqlPoolName("sqlcrudtest-9187")
            .workloadGroupName("smallrc")
            .workspaceName("sqlcrudtest-2080")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlPoolWorkloadGroup = new azure_native.synapse.SqlPoolWorkloadGroup("sqlPoolWorkloadGroup", {
    importance: "normal",
    maxResourcePercent: 100,
    maxResourcePercentPerRequest: 3,
    minResourcePercent: 0,
    minResourcePercentPerRequest: 3,
    queryExecutionTimeout: 0,
    resourceGroupName: "sqlcrudtest-6852",
    sqlPoolName: "sqlcrudtest-9187",
    workloadGroupName: "smallrc",
    workspaceName: "sqlcrudtest-2080",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_pool_workload_group = azure_native.synapse.SqlPoolWorkloadGroup("sqlPoolWorkloadGroup",
    importance="normal",
    max_resource_percent=100,
    max_resource_percent_per_request=3,
    min_resource_percent=0,
    min_resource_percent_per_request=3,
    query_execution_timeout=0,
    resource_group_name="sqlcrudtest-6852",
    sql_pool_name="sqlcrudtest-9187",
    workload_group_name="smallrc",
    workspace_name="sqlcrudtest-2080")

```

```yaml
resources:
  sqlPoolWorkloadGroup:
    type: azure-native:synapse:SqlPoolWorkloadGroup
    properties:
      importance: normal
      maxResourcePercent: 100
      maxResourcePercentPerRequest: 3
      minResourcePercent: 0
      minResourcePercentPerRequest: 3
      queryExecutionTimeout: 0
      resourceGroupName: sqlcrudtest-6852
      sqlPoolName: sqlcrudtest-9187
      workloadGroupName: smallrc
      workspaceName: sqlcrudtest-2080

```

{{% /example %}}
{{% example %}}
### Create a workload group with the required properties specified.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlPoolWorkloadGroup = new AzureNative.Synapse.SqlPoolWorkloadGroup("sqlPoolWorkloadGroup", new()
    {
        MaxResourcePercent = 100,
        MinResourcePercent = 0,
        MinResourcePercentPerRequest = 3,
        ResourceGroupName = "sqlcrudtest-6852",
        SqlPoolName = "sqlcrudtest-9187",
        WorkloadGroupName = "smallrc",
        WorkspaceName = "sqlcrudtest-2080",
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
		_, err := synapse.NewSqlPoolWorkloadGroup(ctx, "sqlPoolWorkloadGroup", &synapse.SqlPoolWorkloadGroupArgs{
			MaxResourcePercent:           pulumi.Int(100),
			MinResourcePercent:           pulumi.Int(0),
			MinResourcePercentPerRequest: pulumi.Float64(3),
			ResourceGroupName:            pulumi.String("sqlcrudtest-6852"),
			SqlPoolName:                  pulumi.String("sqlcrudtest-9187"),
			WorkloadGroupName:            pulumi.String("smallrc"),
			WorkspaceName:                pulumi.String("sqlcrudtest-2080"),
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
import com.pulumi.azurenative.synapse.SqlPoolWorkloadGroup;
import com.pulumi.azurenative.synapse.SqlPoolWorkloadGroupArgs;
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
        var sqlPoolWorkloadGroup = new SqlPoolWorkloadGroup("sqlPoolWorkloadGroup", SqlPoolWorkloadGroupArgs.builder()        
            .maxResourcePercent(100)
            .minResourcePercent(0)
            .minResourcePercentPerRequest(3)
            .resourceGroupName("sqlcrudtest-6852")
            .sqlPoolName("sqlcrudtest-9187")
            .workloadGroupName("smallrc")
            .workspaceName("sqlcrudtest-2080")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlPoolWorkloadGroup = new azure_native.synapse.SqlPoolWorkloadGroup("sqlPoolWorkloadGroup", {
    maxResourcePercent: 100,
    minResourcePercent: 0,
    minResourcePercentPerRequest: 3,
    resourceGroupName: "sqlcrudtest-6852",
    sqlPoolName: "sqlcrudtest-9187",
    workloadGroupName: "smallrc",
    workspaceName: "sqlcrudtest-2080",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_pool_workload_group = azure_native.synapse.SqlPoolWorkloadGroup("sqlPoolWorkloadGroup",
    max_resource_percent=100,
    min_resource_percent=0,
    min_resource_percent_per_request=3,
    resource_group_name="sqlcrudtest-6852",
    sql_pool_name="sqlcrudtest-9187",
    workload_group_name="smallrc",
    workspace_name="sqlcrudtest-2080")

```

```yaml
resources:
  sqlPoolWorkloadGroup:
    type: azure-native:synapse:SqlPoolWorkloadGroup
    properties:
      maxResourcePercent: 100
      minResourcePercent: 0
      minResourcePercentPerRequest: 3
      resourceGroupName: sqlcrudtest-6852
      sqlPoolName: sqlcrudtest-9187
      workloadGroupName: smallrc
      workspaceName: sqlcrudtest-2080

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:synapse:SqlPoolWorkloadGroup smallrc /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-6852/providers/Microsoft.Synapse/workspaces/sqlcrudtest-2080/sqlPools/workloadGroups/smallrc 
```
