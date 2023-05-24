Class representing a read only following database.
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
    var readOnlyFollowingDatabase = new AzureNative.Kusto.ReadOnlyFollowingDatabase("readOnlyFollowingDatabase", new()
    {
        ClusterName = "kustoCluster",
        DatabaseName = "kustoReadOnlyDatabase",
        HotCachePeriod = "P1D",
        Kind = "ReadOnlyFollowing",
        Location = "westus",
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
		_, err := kusto.NewReadOnlyFollowingDatabase(ctx, "readOnlyFollowingDatabase", &kusto.ReadOnlyFollowingDatabaseArgs{
			ClusterName:       pulumi.String("kustoCluster"),
			DatabaseName:      pulumi.String("kustoReadOnlyDatabase"),
			HotCachePeriod:    pulumi.String("P1D"),
			Kind:              pulumi.String("ReadOnlyFollowing"),
			Location:          pulumi.String("westus"),
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
import com.pulumi.azurenative.kusto.ReadOnlyFollowingDatabase;
import com.pulumi.azurenative.kusto.ReadOnlyFollowingDatabaseArgs;
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
        var readOnlyFollowingDatabase = new ReadOnlyFollowingDatabase("readOnlyFollowingDatabase", ReadOnlyFollowingDatabaseArgs.builder()        
            .clusterName("kustoCluster")
            .databaseName("kustoReadOnlyDatabase")
            .hotCachePeriod("P1D")
            .kind("ReadOnlyFollowing")
            .location("westus")
            .resourceGroupName("kustorptest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const readOnlyFollowingDatabase = new azure_native.kusto.ReadOnlyFollowingDatabase("readOnlyFollowingDatabase", {
    clusterName: "kustoCluster",
    databaseName: "kustoReadOnlyDatabase",
    hotCachePeriod: "P1D",
    kind: "ReadOnlyFollowing",
    location: "westus",
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

read_only_following_database = azure_native.kusto.ReadOnlyFollowingDatabase("readOnlyFollowingDatabase",
    cluster_name="kustoCluster",
    database_name="kustoReadOnlyDatabase",
    hot_cache_period="P1D",
    kind="ReadOnlyFollowing",
    location="westus",
    resource_group_name="kustorptest")

```

```yaml
resources:
  readOnlyFollowingDatabase:
    type: azure-native:kusto:ReadOnlyFollowingDatabase
    properties:
      clusterName: kustoCluster
      databaseName: kustoReadOnlyDatabase
      hotCachePeriod: P1D
      kind: ReadOnlyFollowing
      location: westus
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
    var readOnlyFollowingDatabase = new AzureNative.Kusto.ReadOnlyFollowingDatabase("readOnlyFollowingDatabase", new()
    {
        CallerRole = "Admin",
        ClusterName = "kustoCluster",
        DatabaseName = "KustoDatabase8",
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
		_, err := kusto.NewReadOnlyFollowingDatabase(ctx, "readOnlyFollowingDatabase", &kusto.ReadOnlyFollowingDatabaseArgs{
			CallerRole:        pulumi.String("Admin"),
			ClusterName:       pulumi.String("kustoCluster"),
			DatabaseName:      pulumi.String("KustoDatabase8"),
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
import com.pulumi.azurenative.kusto.ReadOnlyFollowingDatabase;
import com.pulumi.azurenative.kusto.ReadOnlyFollowingDatabaseArgs;
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
        var readOnlyFollowingDatabase = new ReadOnlyFollowingDatabase("readOnlyFollowingDatabase", ReadOnlyFollowingDatabaseArgs.builder()        
            .callerRole("Admin")
            .clusterName("kustoCluster")
            .databaseName("KustoDatabase8")
            .resourceGroupName("kustorptest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const readOnlyFollowingDatabase = new azure_native.kusto.ReadOnlyFollowingDatabase("readOnlyFollowingDatabase", {
    callerRole: "Admin",
    clusterName: "kustoCluster",
    databaseName: "KustoDatabase8",
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

read_only_following_database = azure_native.kusto.ReadOnlyFollowingDatabase("readOnlyFollowingDatabase",
    caller_role="Admin",
    cluster_name="kustoCluster",
    database_name="KustoDatabase8",
    resource_group_name="kustorptest")

```

```yaml
resources:
  readOnlyFollowingDatabase:
    type: azure-native:kusto:ReadOnlyFollowingDatabase
    properties:
      callerRole: Admin
      clusterName: kustoCluster
      databaseName: KustoDatabase8
      resourceGroupName: kustorptest

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kusto:ReadOnlyFollowingDatabase kustoCluster/KustoDatabase8 /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster/Databases/KustoDatabase8 
```
