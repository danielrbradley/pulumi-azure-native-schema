Class representing a read write database.
API Version: 2022-12-29.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Kusto ReadOnly database update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var readWriteDatabase = new AzureNative.Kusto.ReadWriteDatabase("readWriteDatabase", new()
    {
        ClusterName = "kustoCluster",
        DatabaseName = "kustoReadOnlyDatabase",
        ResourceGroupName = "kustorptest",
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
		_, err := kusto.NewReadWriteDatabase(ctx, "readWriteDatabase", &kusto.ReadWriteDatabaseArgs{
			ClusterName:       pulumi.String("kustoCluster"),
			DatabaseName:      pulumi.String("kustoReadOnlyDatabase"),
			ResourceGroupName: pulumi.String("kustorptest"),
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
import com.pulumi.azurenative.kusto.ReadWriteDatabase;
import com.pulumi.azurenative.kusto.ReadWriteDatabaseArgs;
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
        var readWriteDatabase = new ReadWriteDatabase("readWriteDatabase", ReadWriteDatabaseArgs.builder()        
            .clusterName("kustoCluster")
            .databaseName("kustoReadOnlyDatabase")
            .resourceGroupName("kustorptest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const readWriteDatabase = new azure_native.kusto.ReadWriteDatabase("readWriteDatabase", {
    clusterName: "kustoCluster",
    databaseName: "kustoReadOnlyDatabase",
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

read_write_database = azure_native.kusto.ReadWriteDatabase("readWriteDatabase",
    cluster_name="kustoCluster",
    database_name="kustoReadOnlyDatabase",
    resource_group_name="kustorptest")

```

```yaml
resources:
  readWriteDatabase:
    type: azure-native:kusto:ReadWriteDatabase
    properties:
      clusterName: kustoCluster
      databaseName: kustoReadOnlyDatabase
      resourceGroupName: kustorptest

```

{{% /example %}}
{{% example %}}
### Kusto ReadWrite database create or update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var readWriteDatabase = new AzureNative.Kusto.ReadWriteDatabase("readWriteDatabase", new()
    {
        CallerRole = "Admin",
        ClusterName = "kustoCluster",
        DatabaseName = "KustoDatabase8",
        Kind = "ReadWrite",
        Location = "westus",
        ResourceGroupName = "kustorptest",
        SoftDeletePeriod = "P1D",
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
		_, err := kusto.NewReadWriteDatabase(ctx, "readWriteDatabase", &kusto.ReadWriteDatabaseArgs{
			CallerRole:        pulumi.String("Admin"),
			ClusterName:       pulumi.String("kustoCluster"),
			DatabaseName:      pulumi.String("KustoDatabase8"),
			Kind:              pulumi.String("ReadWrite"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("kustorptest"),
			SoftDeletePeriod:  pulumi.String("P1D"),
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
import com.pulumi.azurenative.kusto.ReadWriteDatabase;
import com.pulumi.azurenative.kusto.ReadWriteDatabaseArgs;
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
        var readWriteDatabase = new ReadWriteDatabase("readWriteDatabase", ReadWriteDatabaseArgs.builder()        
            .callerRole("Admin")
            .clusterName("kustoCluster")
            .databaseName("KustoDatabase8")
            .kind("ReadWrite")
            .location("westus")
            .resourceGroupName("kustorptest")
            .softDeletePeriod("P1D")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const readWriteDatabase = new azure_native.kusto.ReadWriteDatabase("readWriteDatabase", {
    callerRole: "Admin",
    clusterName: "kustoCluster",
    databaseName: "KustoDatabase8",
    kind: "ReadWrite",
    location: "westus",
    resourceGroupName: "kustorptest",
    softDeletePeriod: "P1D",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

read_write_database = azure_native.kusto.ReadWriteDatabase("readWriteDatabase",
    caller_role="Admin",
    cluster_name="kustoCluster",
    database_name="KustoDatabase8",
    kind="ReadWrite",
    location="westus",
    resource_group_name="kustorptest",
    soft_delete_period="P1D")

```

```yaml
resources:
  readWriteDatabase:
    type: azure-native:kusto:ReadWriteDatabase
    properties:
      callerRole: Admin
      clusterName: kustoCluster
      databaseName: KustoDatabase8
      kind: ReadWrite
      location: westus
      resourceGroupName: kustorptest
      softDeletePeriod: P1D

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kusto:ReadWriteDatabase kustoCluster/KustoDatabase8 /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster/Databases/KustoDatabase8 
```
