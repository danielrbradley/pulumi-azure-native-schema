Workload group operations for a data warehouse
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var workloadGroup = new AzureNative.Sql.WorkloadGroup("workloadGroup", new()
    {
        DatabaseName = "testdb",
        Importance = "normal",
        MaxResourcePercent = 100,
        MaxResourcePercentPerRequest = 3,
        MinResourcePercent = 0,
        MinResourcePercentPerRequest = 3,
        QueryExecutionTimeout = 0,
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
        WorkloadGroupName = "smallrc",
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
		_, err := sql.NewWorkloadGroup(ctx, "workloadGroup", &sql.WorkloadGroupArgs{
			DatabaseName:                 pulumi.String("testdb"),
			Importance:                   pulumi.String("normal"),
			MaxResourcePercent:           pulumi.Int(100),
			MaxResourcePercentPerRequest: pulumi.Float64(3),
			MinResourcePercent:           pulumi.Int(0),
			MinResourcePercentPerRequest: pulumi.Float64(3),
			QueryExecutionTimeout:        pulumi.Int(0),
			ResourceGroupName:            pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:                   pulumi.String("testsvr"),
			WorkloadGroupName:            pulumi.String("smallrc"),
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
import com.pulumi.azurenative.sql.WorkloadGroup;
import com.pulumi.azurenative.sql.WorkloadGroupArgs;
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
        var workloadGroup = new WorkloadGroup("workloadGroup", WorkloadGroupArgs.builder()        
            .databaseName("testdb")
            .importance("normal")
            .maxResourcePercent(100)
            .maxResourcePercentPerRequest(3)
            .minResourcePercent(0)
            .minResourcePercentPerRequest(3)
            .queryExecutionTimeout(0)
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .workloadGroupName("smallrc")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workloadGroup = new azure_native.sql.WorkloadGroup("workloadGroup", {
    databaseName: "testdb",
    importance: "normal",
    maxResourcePercent: 100,
    maxResourcePercentPerRequest: 3,
    minResourcePercent: 0,
    minResourcePercentPerRequest: 3,
    queryExecutionTimeout: 0,
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
    workloadGroupName: "smallrc",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workload_group = azure_native.sql.WorkloadGroup("workloadGroup",
    database_name="testdb",
    importance="normal",
    max_resource_percent=100,
    max_resource_percent_per_request=3,
    min_resource_percent=0,
    min_resource_percent_per_request=3,
    query_execution_timeout=0,
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr",
    workload_group_name="smallrc")

```

```yaml
resources:
  workloadGroup:
    type: azure-native:sql:WorkloadGroup
    properties:
      databaseName: testdb
      importance: normal
      maxResourcePercent: 100
      maxResourcePercentPerRequest: 3
      minResourcePercent: 0
      minResourcePercentPerRequest: 3
      queryExecutionTimeout: 0
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr
      workloadGroupName: smallrc

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
    var workloadGroup = new AzureNative.Sql.WorkloadGroup("workloadGroup", new()
    {
        DatabaseName = "testdb",
        MaxResourcePercent = 100,
        MinResourcePercent = 0,
        MinResourcePercentPerRequest = 3,
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
        WorkloadGroupName = "smallrc",
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
		_, err := sql.NewWorkloadGroup(ctx, "workloadGroup", &sql.WorkloadGroupArgs{
			DatabaseName:                 pulumi.String("testdb"),
			MaxResourcePercent:           pulumi.Int(100),
			MinResourcePercent:           pulumi.Int(0),
			MinResourcePercentPerRequest: pulumi.Float64(3),
			ResourceGroupName:            pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:                   pulumi.String("testsvr"),
			WorkloadGroupName:            pulumi.String("smallrc"),
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
import com.pulumi.azurenative.sql.WorkloadGroup;
import com.pulumi.azurenative.sql.WorkloadGroupArgs;
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
        var workloadGroup = new WorkloadGroup("workloadGroup", WorkloadGroupArgs.builder()        
            .databaseName("testdb")
            .maxResourcePercent(100)
            .minResourcePercent(0)
            .minResourcePercentPerRequest(3)
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .workloadGroupName("smallrc")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workloadGroup = new azure_native.sql.WorkloadGroup("workloadGroup", {
    databaseName: "testdb",
    maxResourcePercent: 100,
    minResourcePercent: 0,
    minResourcePercentPerRequest: 3,
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
    workloadGroupName: "smallrc",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workload_group = azure_native.sql.WorkloadGroup("workloadGroup",
    database_name="testdb",
    max_resource_percent=100,
    min_resource_percent=0,
    min_resource_percent_per_request=3,
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr",
    workload_group_name="smallrc")

```

```yaml
resources:
  workloadGroup:
    type: azure-native:sql:WorkloadGroup
    properties:
      databaseName: testdb
      maxResourcePercent: 100
      minResourcePercent: 0
      minResourcePercentPerRequest: 3
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr
      workloadGroupName: smallrc

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:WorkloadGroup smallrc /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb/workloadGroups/smallrc 
```
