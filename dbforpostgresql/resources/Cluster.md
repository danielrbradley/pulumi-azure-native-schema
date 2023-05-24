Represents a cluster.
API Version: 2022-11-08.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a new cluster
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.DBforPostgreSQL.Cluster("cluster", new()
    {
        AdministratorLoginPassword = "password",
        CitusVersion = "11.1",
        ClusterName = "testcluster",
        CoordinatorEnablePublicIpAccess = true,
        CoordinatorServerEdition = "GeneralPurpose",
        CoordinatorStorageQuotaInMb = 524288,
        CoordinatorVCores = 4,
        EnableHa = true,
        EnableShardsOnCoordinator = false,
        Location = "westus",
        NodeCount = 3,
        NodeEnablePublicIpAccess = false,
        NodeServerEdition = "MemoryOptimized",
        NodeStorageQuotaInMb = 524288,
        NodeVCores = 8,
        PostgresqlVersion = "15",
        PreferredPrimaryZone = "1",
        ResourceGroupName = "TestGroup",
        Tags = null,
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewCluster(ctx, "cluster", &dbforpostgresql.ClusterArgs{
			AdministratorLoginPassword:      pulumi.String("password"),
			CitusVersion:                    pulumi.String("11.1"),
			ClusterName:                     pulumi.String("testcluster"),
			CoordinatorEnablePublicIpAccess: pulumi.Bool(true),
			CoordinatorServerEdition:        pulumi.String("GeneralPurpose"),
			CoordinatorStorageQuotaInMb:     pulumi.Float64(524288),
			CoordinatorVCores:               pulumi.Float64(4),
			EnableHa:                        pulumi.Bool(true),
			EnableShardsOnCoordinator:       pulumi.Bool(false),
			Location:                        pulumi.String("westus"),
			NodeCount:                       pulumi.Float64(3),
			NodeEnablePublicIpAccess:        pulumi.Bool(false),
			NodeServerEdition:               pulumi.String("MemoryOptimized"),
			NodeStorageQuotaInMb:            pulumi.Float64(524288),
			NodeVCores:                      pulumi.Float64(8),
			PostgresqlVersion:               pulumi.String("15"),
			PreferredPrimaryZone:            pulumi.String("1"),
			ResourceGroupName:               pulumi.String("TestGroup"),
			Tags:                            nil,
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
import com.pulumi.azurenative.dbforpostgresql.Cluster;
import com.pulumi.azurenative.dbforpostgresql.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .administratorLoginPassword("password")
            .citusVersion("11.1")
            .clusterName("testcluster")
            .coordinatorEnablePublicIpAccess(true)
            .coordinatorServerEdition("GeneralPurpose")
            .coordinatorStorageQuotaInMb(524288)
            .coordinatorVCores(4)
            .enableHa(true)
            .enableShardsOnCoordinator(false)
            .location("westus")
            .nodeCount(3)
            .nodeEnablePublicIpAccess(false)
            .nodeServerEdition("MemoryOptimized")
            .nodeStorageQuotaInMb(524288)
            .nodeVCores(8)
            .postgresqlVersion("15")
            .preferredPrimaryZone("1")
            .resourceGroupName("TestGroup")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.dbforpostgresql.Cluster("cluster", {
    administratorLoginPassword: "password",
    citusVersion: "11.1",
    clusterName: "testcluster",
    coordinatorEnablePublicIpAccess: true,
    coordinatorServerEdition: "GeneralPurpose",
    coordinatorStorageQuotaInMb: 524288,
    coordinatorVCores: 4,
    enableHa: true,
    enableShardsOnCoordinator: false,
    location: "westus",
    nodeCount: 3,
    nodeEnablePublicIpAccess: false,
    nodeServerEdition: "MemoryOptimized",
    nodeStorageQuotaInMb: 524288,
    nodeVCores: 8,
    postgresqlVersion: "15",
    preferredPrimaryZone: "1",
    resourceGroupName: "TestGroup",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.dbforpostgresql.Cluster("cluster",
    administrator_login_password="password",
    citus_version="11.1",
    cluster_name="testcluster",
    coordinator_enable_public_ip_access=True,
    coordinator_server_edition="GeneralPurpose",
    coordinator_storage_quota_in_mb=524288,
    coordinator_v_cores=4,
    enable_ha=True,
    enable_shards_on_coordinator=False,
    location="westus",
    node_count=3,
    node_enable_public_ip_access=False,
    node_server_edition="MemoryOptimized",
    node_storage_quota_in_mb=524288,
    node_v_cores=8,
    postgresql_version="15",
    preferred_primary_zone="1",
    resource_group_name="TestGroup",
    tags={})

```

```yaml
resources:
  cluster:
    type: azure-native:dbforpostgresql:Cluster
    properties:
      administratorLoginPassword: password
      citusVersion: '11.1'
      clusterName: testcluster
      coordinatorEnablePublicIpAccess: true
      coordinatorServerEdition: GeneralPurpose
      coordinatorStorageQuotaInMb: 524288
      coordinatorVCores: 4
      enableHa: true
      enableShardsOnCoordinator: false
      location: westus
      nodeCount: 3
      nodeEnablePublicIpAccess: false
      nodeServerEdition: MemoryOptimized
      nodeStorageQuotaInMb: 524288
      nodeVCores: 8
      postgresqlVersion: '15'
      preferredPrimaryZone: '1'
      resourceGroupName: TestGroup
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create a new cluster as a point in time restore
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.DBforPostgreSQL.Cluster("cluster", new()
    {
        ClusterName = "testcluster",
        Location = "westus",
        PointInTimeUTC = "2017-12-14T00:00:37.467Z",
        ResourceGroupName = "TestGroup",
        SourceLocation = "westus",
        SourceResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/source-cluster",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewCluster(ctx, "cluster", &dbforpostgresql.ClusterArgs{
			ClusterName:       pulumi.String("testcluster"),
			Location:          pulumi.String("westus"),
			PointInTimeUTC:    pulumi.String("2017-12-14T00:00:37.467Z"),
			ResourceGroupName: pulumi.String("TestGroup"),
			SourceLocation:    pulumi.String("westus"),
			SourceResourceId:  pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/source-cluster"),
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
import com.pulumi.azurenative.dbforpostgresql.Cluster;
import com.pulumi.azurenative.dbforpostgresql.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("testcluster")
            .location("westus")
            .pointInTimeUTC("2017-12-14T00:00:37.467Z")
            .resourceGroupName("TestGroup")
            .sourceLocation("westus")
            .sourceResourceId("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/source-cluster")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.dbforpostgresql.Cluster("cluster", {
    clusterName: "testcluster",
    location: "westus",
    pointInTimeUTC: "2017-12-14T00:00:37.467Z",
    resourceGroupName: "TestGroup",
    sourceLocation: "westus",
    sourceResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/source-cluster",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.dbforpostgresql.Cluster("cluster",
    cluster_name="testcluster",
    location="westus",
    point_in_time_utc="2017-12-14T00:00:37.467Z",
    resource_group_name="TestGroup",
    source_location="westus",
    source_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/source-cluster")

```

```yaml
resources:
  cluster:
    type: azure-native:dbforpostgresql:Cluster
    properties:
      clusterName: testcluster
      location: westus
      pointInTimeUTC: 2017-12-14T00:00:37.467Z
      resourceGroupName: TestGroup
      sourceLocation: westus
      sourceResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/source-cluster

```

{{% /example %}}
{{% example %}}
### Create a new cluster as a read replica
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.DBforPostgreSQL.Cluster("cluster", new()
    {
        ClusterName = "testcluster",
        Location = "westus",
        ResourceGroupName = "TestGroup",
        SourceLocation = "westus",
        SourceResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/sourcecluster",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewCluster(ctx, "cluster", &dbforpostgresql.ClusterArgs{
			ClusterName:       pulumi.String("testcluster"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("TestGroup"),
			SourceLocation:    pulumi.String("westus"),
			SourceResourceId:  pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/sourcecluster"),
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
import com.pulumi.azurenative.dbforpostgresql.Cluster;
import com.pulumi.azurenative.dbforpostgresql.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("testcluster")
            .location("westus")
            .resourceGroupName("TestGroup")
            .sourceLocation("westus")
            .sourceResourceId("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/sourcecluster")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.dbforpostgresql.Cluster("cluster", {
    clusterName: "testcluster",
    location: "westus",
    resourceGroupName: "TestGroup",
    sourceLocation: "westus",
    sourceResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/sourcecluster",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.dbforpostgresql.Cluster("cluster",
    cluster_name="testcluster",
    location="westus",
    resource_group_name="TestGroup",
    source_location="westus",
    source_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/sourcecluster")

```

```yaml
resources:
  cluster:
    type: azure-native:dbforpostgresql:Cluster
    properties:
      clusterName: testcluster
      location: westus
      resourceGroupName: TestGroup
      sourceLocation: westus
      sourceResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/sourcecluster

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbforpostgresql:Cluster testcluster /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/testcluster 
```
