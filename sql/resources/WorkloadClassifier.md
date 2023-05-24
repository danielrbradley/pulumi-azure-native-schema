Workload classifier operations for a data warehouse
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
    var workloadClassifier = new AzureNative.Sql.WorkloadClassifier("workloadClassifier", new()
    {
        Context = "test_context",
        DatabaseName = "testdb",
        EndTime = "14:00",
        Importance = "high",
        Label = "test_label",
        MemberName = "dbo",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
        StartTime = "12:00",
        WorkloadClassifierName = "wlm_workloadclassifier",
        WorkloadGroupName = "wlm_workloadgroup",
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
		_, err := sql.NewWorkloadClassifier(ctx, "workloadClassifier", &sql.WorkloadClassifierArgs{
			Context:                pulumi.String("test_context"),
			DatabaseName:           pulumi.String("testdb"),
			EndTime:                pulumi.String("14:00"),
			Importance:             pulumi.String("high"),
			Label:                  pulumi.String("test_label"),
			MemberName:             pulumi.String("dbo"),
			ResourceGroupName:      pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:             pulumi.String("testsvr"),
			StartTime:              pulumi.String("12:00"),
			WorkloadClassifierName: pulumi.String("wlm_workloadclassifier"),
			WorkloadGroupName:      pulumi.String("wlm_workloadgroup"),
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
import com.pulumi.azurenative.sql.WorkloadClassifier;
import com.pulumi.azurenative.sql.WorkloadClassifierArgs;
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
        var workloadClassifier = new WorkloadClassifier("workloadClassifier", WorkloadClassifierArgs.builder()        
            .context("test_context")
            .databaseName("testdb")
            .endTime("14:00")
            .importance("high")
            .label("test_label")
            .memberName("dbo")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .startTime("12:00")
            .workloadClassifierName("wlm_workloadclassifier")
            .workloadGroupName("wlm_workloadgroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workloadClassifier = new azure_native.sql.WorkloadClassifier("workloadClassifier", {
    context: "test_context",
    databaseName: "testdb",
    endTime: "14:00",
    importance: "high",
    label: "test_label",
    memberName: "dbo",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
    startTime: "12:00",
    workloadClassifierName: "wlm_workloadclassifier",
    workloadGroupName: "wlm_workloadgroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workload_classifier = azure_native.sql.WorkloadClassifier("workloadClassifier",
    context="test_context",
    database_name="testdb",
    end_time="14:00",
    importance="high",
    label="test_label",
    member_name="dbo",
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr",
    start_time="12:00",
    workload_classifier_name="wlm_workloadclassifier",
    workload_group_name="wlm_workloadgroup")

```

```yaml
resources:
  workloadClassifier:
    type: azure-native:sql:WorkloadClassifier
    properties:
      context: test_context
      databaseName: testdb
      endTime: 14:00
      importance: high
      label: test_label
      memberName: dbo
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr
      startTime: 12:00
      workloadClassifierName: wlm_workloadclassifier
      workloadGroupName: wlm_workloadgroup

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
    var workloadClassifier = new AzureNative.Sql.WorkloadClassifier("workloadClassifier", new()
    {
        DatabaseName = "testdb",
        MemberName = "dbo",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
        WorkloadClassifierName = "wlm_workloadclassifier",
        WorkloadGroupName = "wlm_workloadgroup",
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
		_, err := sql.NewWorkloadClassifier(ctx, "workloadClassifier", &sql.WorkloadClassifierArgs{
			DatabaseName:           pulumi.String("testdb"),
			MemberName:             pulumi.String("dbo"),
			ResourceGroupName:      pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:             pulumi.String("testsvr"),
			WorkloadClassifierName: pulumi.String("wlm_workloadclassifier"),
			WorkloadGroupName:      pulumi.String("wlm_workloadgroup"),
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
import com.pulumi.azurenative.sql.WorkloadClassifier;
import com.pulumi.azurenative.sql.WorkloadClassifierArgs;
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
        var workloadClassifier = new WorkloadClassifier("workloadClassifier", WorkloadClassifierArgs.builder()        
            .databaseName("testdb")
            .memberName("dbo")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .workloadClassifierName("wlm_workloadclassifier")
            .workloadGroupName("wlm_workloadgroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workloadClassifier = new azure_native.sql.WorkloadClassifier("workloadClassifier", {
    databaseName: "testdb",
    memberName: "dbo",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
    workloadClassifierName: "wlm_workloadclassifier",
    workloadGroupName: "wlm_workloadgroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workload_classifier = azure_native.sql.WorkloadClassifier("workloadClassifier",
    database_name="testdb",
    member_name="dbo",
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr",
    workload_classifier_name="wlm_workloadclassifier",
    workload_group_name="wlm_workloadgroup")

```

```yaml
resources:
  workloadClassifier:
    type: azure-native:sql:WorkloadClassifier
    properties:
      databaseName: testdb
      memberName: dbo
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr
      workloadClassifierName: wlm_workloadclassifier
      workloadGroupName: wlm_workloadgroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:WorkloadClassifier wlm_workloadclassifier /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb/workloadGroups/wlm_workloadgroup/workloadClassifiers/wlm_workloadclassifier 
```
