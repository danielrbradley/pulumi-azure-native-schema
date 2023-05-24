An elastic pool.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update Hyperscale elastic pool with high availability replica count parameter
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var elasticPool = new AzureNative.Sql.ElasticPool("elasticPool", new()
    {
        ElasticPoolName = "sqlcrudtest-8102",
        HighAvailabilityReplicaCount = 2,
        Location = "Japan East",
        ResourceGroupName = "sqlcrudtest-2369",
        ServerName = "sqlcrudtest-8069",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Name = "HS_Gen5_4",
        },
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
		_, err := sql.NewElasticPool(ctx, "elasticPool", &sql.ElasticPoolArgs{
			ElasticPoolName:              pulumi.String("sqlcrudtest-8102"),
			HighAvailabilityReplicaCount: pulumi.Int(2),
			Location:                     pulumi.String("Japan East"),
			ResourceGroupName:            pulumi.String("sqlcrudtest-2369"),
			ServerName:                   pulumi.String("sqlcrudtest-8069"),
			Sku: &sql.SkuArgs{
				Name: pulumi.String("HS_Gen5_4"),
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
import com.pulumi.azurenative.sql.ElasticPool;
import com.pulumi.azurenative.sql.ElasticPoolArgs;
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
        var elasticPool = new ElasticPool("elasticPool", ElasticPoolArgs.builder()        
            .elasticPoolName("sqlcrudtest-8102")
            .highAvailabilityReplicaCount(2)
            .location("Japan East")
            .resourceGroupName("sqlcrudtest-2369")
            .serverName("sqlcrudtest-8069")
            .sku(Map.of("name", "HS_Gen5_4"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const elasticPool = new azure_native.sql.ElasticPool("elasticPool", {
    elasticPoolName: "sqlcrudtest-8102",
    highAvailabilityReplicaCount: 2,
    location: "Japan East",
    resourceGroupName: "sqlcrudtest-2369",
    serverName: "sqlcrudtest-8069",
    sku: {
        name: "HS_Gen5_4",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

elastic_pool = azure_native.sql.ElasticPool("elasticPool",
    elastic_pool_name="sqlcrudtest-8102",
    high_availability_replica_count=2,
    location="Japan East",
    resource_group_name="sqlcrudtest-2369",
    server_name="sqlcrudtest-8069",
    sku=azure_native.sql.SkuArgs(
        name="HS_Gen5_4",
    ))

```

```yaml
resources:
  elasticPool:
    type: azure-native:sql:ElasticPool
    properties:
      elasticPoolName: sqlcrudtest-8102
      highAvailabilityReplicaCount: 2
      location: Japan East
      resourceGroupName: sqlcrudtest-2369
      serverName: sqlcrudtest-8069
      sku:
        name: HS_Gen5_4

```

{{% /example %}}
{{% example %}}
### Create or update elastic pool with all parameter
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var elasticPool = new AzureNative.Sql.ElasticPool("elasticPool", new()
    {
        ElasticPoolName = "sqlcrudtest-8102",
        Location = "Japan East",
        PerDatabaseSettings = new AzureNative.Sql.Inputs.ElasticPoolPerDatabaseSettingsArgs
        {
            MaxCapacity = 2,
            MinCapacity = 0.25,
        },
        ResourceGroupName = "sqlcrudtest-2369",
        ServerName = "sqlcrudtest-8069",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Capacity = 2,
            Name = "GP_Gen4_2",
            Tier = "GeneralPurpose",
        },
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
		_, err := sql.NewElasticPool(ctx, "elasticPool", &sql.ElasticPoolArgs{
			ElasticPoolName: pulumi.String("sqlcrudtest-8102"),
			Location:        pulumi.String("Japan East"),
			PerDatabaseSettings: &sql.ElasticPoolPerDatabaseSettingsArgs{
				MaxCapacity: pulumi.Float64(2),
				MinCapacity: pulumi.Float64(0.25),
			},
			ResourceGroupName: pulumi.String("sqlcrudtest-2369"),
			ServerName:        pulumi.String("sqlcrudtest-8069"),
			Sku: &sql.SkuArgs{
				Capacity: pulumi.Int(2),
				Name:     pulumi.String("GP_Gen4_2"),
				Tier:     pulumi.String("GeneralPurpose"),
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
import com.pulumi.azurenative.sql.ElasticPool;
import com.pulumi.azurenative.sql.ElasticPoolArgs;
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
        var elasticPool = new ElasticPool("elasticPool", ElasticPoolArgs.builder()        
            .elasticPoolName("sqlcrudtest-8102")
            .location("Japan East")
            .perDatabaseSettings(Map.ofEntries(
                Map.entry("maxCapacity", 2),
                Map.entry("minCapacity", 0.25)
            ))
            .resourceGroupName("sqlcrudtest-2369")
            .serverName("sqlcrudtest-8069")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("name", "GP_Gen4_2"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const elasticPool = new azure_native.sql.ElasticPool("elasticPool", {
    elasticPoolName: "sqlcrudtest-8102",
    location: "Japan East",
    perDatabaseSettings: {
        maxCapacity: 2,
        minCapacity: 0.25,
    },
    resourceGroupName: "sqlcrudtest-2369",
    serverName: "sqlcrudtest-8069",
    sku: {
        capacity: 2,
        name: "GP_Gen4_2",
        tier: "GeneralPurpose",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

elastic_pool = azure_native.sql.ElasticPool("elasticPool",
    elastic_pool_name="sqlcrudtest-8102",
    location="Japan East",
    per_database_settings=azure_native.sql.ElasticPoolPerDatabaseSettingsArgs(
        max_capacity=2,
        min_capacity=0.25,
    ),
    resource_group_name="sqlcrudtest-2369",
    server_name="sqlcrudtest-8069",
    sku=azure_native.sql.SkuArgs(
        capacity=2,
        name="GP_Gen4_2",
        tier="GeneralPurpose",
    ))

```

```yaml
resources:
  elasticPool:
    type: azure-native:sql:ElasticPool
    properties:
      elasticPoolName: sqlcrudtest-8102
      location: Japan East
      perDatabaseSettings:
        maxCapacity: 2
        minCapacity: 0.25
      resourceGroupName: sqlcrudtest-2369
      serverName: sqlcrudtest-8069
      sku:
        capacity: 2
        name: GP_Gen4_2
        tier: GeneralPurpose

```

{{% /example %}}
{{% example %}}
### Create or update elastic pool with maintenance configuration parameter
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var elasticPool = new AzureNative.Sql.ElasticPool("elasticPool", new()
    {
        ElasticPoolName = "sqlcrudtest-8102",
        Location = "Japan East",
        MaintenanceConfigurationId = "/subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_1",
        ResourceGroupName = "sqlcrudtest-2369",
        ServerName = "sqlcrudtest-8069",
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
		_, err := sql.NewElasticPool(ctx, "elasticPool", &sql.ElasticPoolArgs{
			ElasticPoolName:            pulumi.String("sqlcrudtest-8102"),
			Location:                   pulumi.String("Japan East"),
			MaintenanceConfigurationId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_1"),
			ResourceGroupName:          pulumi.String("sqlcrudtest-2369"),
			ServerName:                 pulumi.String("sqlcrudtest-8069"),
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
import com.pulumi.azurenative.sql.ElasticPool;
import com.pulumi.azurenative.sql.ElasticPoolArgs;
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
        var elasticPool = new ElasticPool("elasticPool", ElasticPoolArgs.builder()        
            .elasticPoolName("sqlcrudtest-8102")
            .location("Japan East")
            .maintenanceConfigurationId("/subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_1")
            .resourceGroupName("sqlcrudtest-2369")
            .serverName("sqlcrudtest-8069")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const elasticPool = new azure_native.sql.ElasticPool("elasticPool", {
    elasticPoolName: "sqlcrudtest-8102",
    location: "Japan East",
    maintenanceConfigurationId: "/subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_1",
    resourceGroupName: "sqlcrudtest-2369",
    serverName: "sqlcrudtest-8069",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

elastic_pool = azure_native.sql.ElasticPool("elasticPool",
    elastic_pool_name="sqlcrudtest-8102",
    location="Japan East",
    maintenance_configuration_id="/subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_1",
    resource_group_name="sqlcrudtest-2369",
    server_name="sqlcrudtest-8069")

```

```yaml
resources:
  elasticPool:
    type: azure-native:sql:ElasticPool
    properties:
      elasticPoolName: sqlcrudtest-8102
      location: Japan East
      maintenanceConfigurationId: /subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_JapanEast_1
      resourceGroupName: sqlcrudtest-2369
      serverName: sqlcrudtest-8069

```

{{% /example %}}
{{% example %}}
### Create or update elastic pool with minimum parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var elasticPool = new AzureNative.Sql.ElasticPool("elasticPool", new()
    {
        ElasticPoolName = "sqlcrudtest-8102",
        Location = "Japan East",
        ResourceGroupName = "sqlcrudtest-2369",
        ServerName = "sqlcrudtest-8069",
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
		_, err := sql.NewElasticPool(ctx, "elasticPool", &sql.ElasticPoolArgs{
			ElasticPoolName:   pulumi.String("sqlcrudtest-8102"),
			Location:          pulumi.String("Japan East"),
			ResourceGroupName: pulumi.String("sqlcrudtest-2369"),
			ServerName:        pulumi.String("sqlcrudtest-8069"),
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
import com.pulumi.azurenative.sql.ElasticPool;
import com.pulumi.azurenative.sql.ElasticPoolArgs;
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
        var elasticPool = new ElasticPool("elasticPool", ElasticPoolArgs.builder()        
            .elasticPoolName("sqlcrudtest-8102")
            .location("Japan East")
            .resourceGroupName("sqlcrudtest-2369")
            .serverName("sqlcrudtest-8069")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const elasticPool = new azure_native.sql.ElasticPool("elasticPool", {
    elasticPoolName: "sqlcrudtest-8102",
    location: "Japan East",
    resourceGroupName: "sqlcrudtest-2369",
    serverName: "sqlcrudtest-8069",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

elastic_pool = azure_native.sql.ElasticPool("elasticPool",
    elastic_pool_name="sqlcrudtest-8102",
    location="Japan East",
    resource_group_name="sqlcrudtest-2369",
    server_name="sqlcrudtest-8069")

```

```yaml
resources:
  elasticPool:
    type: azure-native:sql:ElasticPool
    properties:
      elasticPoolName: sqlcrudtest-8102
      location: Japan East
      resourceGroupName: sqlcrudtest-2369
      serverName: sqlcrudtest-8069

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ElasticPool sqlcrudtest-8102 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-2369/providers/Microsoft.Sql/servers/sqlcrudtest-8069/elasticPools/sqlcrudtest-8102 
```
