A database resource.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates a VCore database by specifying service objective name.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        DatabaseName = "testdb",
        Location = "southeastasia",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Capacity = 2,
            Family = "Gen4",
            Name = "BC",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			DatabaseName:      pulumi.String("testdb"),
			Location:          pulumi.String("southeastasia"),
			ResourceGroupName: pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:        pulumi.String("testsvr"),
			Sku: &sql.SkuArgs{
				Capacity: pulumi.Int(2),
				Family:   pulumi.String("Gen4"),
				Name:     pulumi.String("BC"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .databaseName("testdb")
            .location("southeastasia")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("family", "Gen4"),
                Map.entry("name", "BC")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    databaseName: "testdb",
    location: "southeastasia",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
    sku: {
        capacity: 2,
        family: "Gen4",
        name: "BC",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    database_name="testdb",
    location="southeastasia",
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr",
    sku=azure_native.sql.SkuArgs(
        capacity=2,
        family="Gen4",
        name="BC",
    ))

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      databaseName: testdb
      location: southeastasia
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr
      sku:
        capacity: 2
        family: Gen4
        name: BC

```

{{% /example %}}
{{% example %}}
### Creates a VCore database by specifying sku name and capacity.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        DatabaseName = "testdb",
        Location = "southeastasia",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Capacity = 2,
            Name = "BC_Gen4",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			DatabaseName:      pulumi.String("testdb"),
			Location:          pulumi.String("southeastasia"),
			ResourceGroupName: pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:        pulumi.String("testsvr"),
			Sku: &sql.SkuArgs{
				Capacity: pulumi.Int(2),
				Name:     pulumi.String("BC_Gen4"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .databaseName("testdb")
            .location("southeastasia")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("name", "BC_Gen4")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    databaseName: "testdb",
    location: "southeastasia",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
    sku: {
        capacity: 2,
        name: "BC_Gen4",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    database_name="testdb",
    location="southeastasia",
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr",
    sku=azure_native.sql.SkuArgs(
        capacity=2,
        name="BC_Gen4",
    ))

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      databaseName: testdb
      location: southeastasia
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr
      sku:
        capacity: 2
        name: BC_Gen4

```

{{% /example %}}
{{% example %}}
### Creates a data warehouse database as a cross-subscription restore from a backup of a dropped database.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        CreateMode = "Restore",
        DatabaseName = "testdw",
        Location = "southeastasia",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
        SourceResourceId = "/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/restorableDroppedDatabases/srcdw,131403269876900000",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			CreateMode:        pulumi.String("Restore"),
			DatabaseName:      pulumi.String("testdw"),
			Location:          pulumi.String("southeastasia"),
			ResourceGroupName: pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:        pulumi.String("testsvr"),
			SourceResourceId:  pulumi.String("/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/restorableDroppedDatabases/srcdw,131403269876900000"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .createMode("Restore")
            .databaseName("testdw")
            .location("southeastasia")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .sourceResourceId("/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/restorableDroppedDatabases/srcdw,131403269876900000")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    createMode: "Restore",
    databaseName: "testdw",
    location: "southeastasia",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
    sourceResourceId: "/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/restorableDroppedDatabases/srcdw,131403269876900000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    create_mode="Restore",
    database_name="testdw",
    location="southeastasia",
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr",
    source_resource_id="/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/restorableDroppedDatabases/srcdw,131403269876900000")

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      createMode: Restore
      databaseName: testdw
      location: southeastasia
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr
      sourceResourceId: /subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/restorableDroppedDatabases/srcdw,131403269876900000

```

{{% /example %}}
{{% example %}}
### Creates a data warehouse database as a cross-subscription restore from a geo-backup.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        CreateMode = "Recovery",
        DatabaseName = "testdw",
        Location = "westus",
        ResourceGroupName = "Default-SQL-WestUS",
        ServerName = "testsvr",
        SourceResourceId = "/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-EastUS/providers/Microsoft.Sql/servers/srcsvr/recoverabledatabases/srcdw",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			CreateMode:        pulumi.String("Recovery"),
			DatabaseName:      pulumi.String("testdw"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("Default-SQL-WestUS"),
			ServerName:        pulumi.String("testsvr"),
			SourceResourceId:  pulumi.String("/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-EastUS/providers/Microsoft.Sql/servers/srcsvr/recoverabledatabases/srcdw"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .createMode("Recovery")
            .databaseName("testdw")
            .location("westus")
            .resourceGroupName("Default-SQL-WestUS")
            .serverName("testsvr")
            .sourceResourceId("/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-EastUS/providers/Microsoft.Sql/servers/srcsvr/recoverabledatabases/srcdw")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    createMode: "Recovery",
    databaseName: "testdw",
    location: "westus",
    resourceGroupName: "Default-SQL-WestUS",
    serverName: "testsvr",
    sourceResourceId: "/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-EastUS/providers/Microsoft.Sql/servers/srcsvr/recoverabledatabases/srcdw",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    create_mode="Recovery",
    database_name="testdw",
    location="westus",
    resource_group_name="Default-SQL-WestUS",
    server_name="testsvr",
    source_resource_id="/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-EastUS/providers/Microsoft.Sql/servers/srcsvr/recoverabledatabases/srcdw")

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      createMode: Recovery
      databaseName: testdw
      location: westus
      resourceGroupName: Default-SQL-WestUS
      serverName: testsvr
      sourceResourceId: /subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-EastUS/providers/Microsoft.Sql/servers/srcsvr/recoverabledatabases/srcdw

```

{{% /example %}}
{{% example %}}
### Creates a data warehouse database as a cross-subscription restore from a restore point of an existing database.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        CreateMode = "PointInTimeRestore",
        DatabaseName = "testdw",
        Location = "southeastasia",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        RestorePointInTime = "2022-01-22T05:35:31.503Z",
        ServerName = "testsvr",
        SourceResourceId = "/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/databases/srcdw",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			CreateMode:         pulumi.String("PointInTimeRestore"),
			DatabaseName:       pulumi.String("testdw"),
			Location:           pulumi.String("southeastasia"),
			ResourceGroupName:  pulumi.String("Default-SQL-SouthEastAsia"),
			RestorePointInTime: pulumi.String("2022-01-22T05:35:31.503Z"),
			ServerName:         pulumi.String("testsvr"),
			SourceResourceId:   pulumi.String("/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/databases/srcdw"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .createMode("PointInTimeRestore")
            .databaseName("testdw")
            .location("southeastasia")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .restorePointInTime("2022-01-22T05:35:31.503Z")
            .serverName("testsvr")
            .sourceResourceId("/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/databases/srcdw")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    createMode: "PointInTimeRestore",
    databaseName: "testdw",
    location: "southeastasia",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    restorePointInTime: "2022-01-22T05:35:31.503Z",
    serverName: "testsvr",
    sourceResourceId: "/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/databases/srcdw",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    create_mode="PointInTimeRestore",
    database_name="testdw",
    location="southeastasia",
    resource_group_name="Default-SQL-SouthEastAsia",
    restore_point_in_time="2022-01-22T05:35:31.503Z",
    server_name="testsvr",
    source_resource_id="/subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/databases/srcdw")

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      createMode: PointInTimeRestore
      databaseName: testdw
      location: southeastasia
      resourceGroupName: Default-SQL-SouthEastAsia
      restorePointInTime: 2022-01-22T05:35:31.503Z
      serverName: testsvr
      sourceResourceId: /subscriptions/55555555-6666-7777-8888-999999999999/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/srcsvr/databases/srcdw

```

{{% /example %}}
{{% example %}}
### Creates a database as a copy.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        CreateMode = "Copy",
        DatabaseName = "dbcopy",
        Location = "southeastasia",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Name = "S0",
            Tier = "Standard",
        },
        SourceDatabaseId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			CreateMode:        pulumi.String("Copy"),
			DatabaseName:      pulumi.String("dbcopy"),
			Location:          pulumi.String("southeastasia"),
			ResourceGroupName: pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:        pulumi.String("testsvr"),
			Sku: &sql.SkuArgs{
				Name: pulumi.String("S0"),
				Tier: pulumi.String("Standard"),
			},
			SourceDatabaseId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .createMode("Copy")
            .databaseName("dbcopy")
            .location("southeastasia")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .sku(Map.ofEntries(
                Map.entry("name", "S0"),
                Map.entry("tier", "Standard")
            ))
            .sourceDatabaseId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    createMode: "Copy",
    databaseName: "dbcopy",
    location: "southeastasia",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
    sku: {
        name: "S0",
        tier: "Standard",
    },
    sourceDatabaseId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    create_mode="Copy",
    database_name="dbcopy",
    location="southeastasia",
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr",
    sku=azure_native.sql.SkuArgs(
        name="S0",
        tier="Standard",
    ),
    source_database_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb")

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      createMode: Copy
      databaseName: dbcopy
      location: southeastasia
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr
      sku:
        name: S0
        tier: Standard
      sourceDatabaseId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb

```

{{% /example %}}
{{% example %}}
### Creates a database as an on-line secondary.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        CreateMode = "Secondary",
        DatabaseName = "testdb",
        Location = "southeastasia",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        SecondaryType = "Geo",
        ServerName = "testsvr",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Name = "S0",
            Tier = "Standard",
        },
        SourceDatabaseId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/testdb",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			CreateMode:        pulumi.String("Secondary"),
			DatabaseName:      pulumi.String("testdb"),
			Location:          pulumi.String("southeastasia"),
			ResourceGroupName: pulumi.String("Default-SQL-SouthEastAsia"),
			SecondaryType:     pulumi.String("Geo"),
			ServerName:        pulumi.String("testsvr"),
			Sku: &sql.SkuArgs{
				Name: pulumi.String("S0"),
				Tier: pulumi.String("Standard"),
			},
			SourceDatabaseId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/testdb"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .createMode("Secondary")
            .databaseName("testdb")
            .location("southeastasia")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .secondaryType("Geo")
            .serverName("testsvr")
            .sku(Map.ofEntries(
                Map.entry("name", "S0"),
                Map.entry("tier", "Standard")
            ))
            .sourceDatabaseId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/testdb")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    createMode: "Secondary",
    databaseName: "testdb",
    location: "southeastasia",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    secondaryType: "Geo",
    serverName: "testsvr",
    sku: {
        name: "S0",
        tier: "Standard",
    },
    sourceDatabaseId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/testdb",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    create_mode="Secondary",
    database_name="testdb",
    location="southeastasia",
    resource_group_name="Default-SQL-SouthEastAsia",
    secondary_type="Geo",
    server_name="testsvr",
    sku=azure_native.sql.SkuArgs(
        name="S0",
        tier="Standard",
    ),
    source_database_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/testdb")

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      createMode: Secondary
      databaseName: testdb
      location: southeastasia
      resourceGroupName: Default-SQL-SouthEastAsia
      secondaryType: Geo
      serverName: testsvr
      sku:
        name: S0
        tier: Standard
      sourceDatabaseId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/testdb

```

{{% /example %}}
{{% example %}}
### Creates a database as named replica secondary.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        CreateMode = "Secondary",
        DatabaseName = "testdb",
        Location = "southeastasia",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        SecondaryType = "Named",
        ServerName = "testsvr",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Capacity = 2,
            Name = "HS_Gen4",
            Tier = "Hyperscale",
        },
        SourceDatabaseId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/primarydb",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			CreateMode:        pulumi.String("Secondary"),
			DatabaseName:      pulumi.String("testdb"),
			Location:          pulumi.String("southeastasia"),
			ResourceGroupName: pulumi.String("Default-SQL-SouthEastAsia"),
			SecondaryType:     pulumi.String("Named"),
			ServerName:        pulumi.String("testsvr"),
			Sku: &sql.SkuArgs{
				Capacity: pulumi.Int(2),
				Name:     pulumi.String("HS_Gen4"),
				Tier:     pulumi.String("Hyperscale"),
			},
			SourceDatabaseId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/primarydb"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .createMode("Secondary")
            .databaseName("testdb")
            .location("southeastasia")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .secondaryType("Named")
            .serverName("testsvr")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("name", "HS_Gen4"),
                Map.entry("tier", "Hyperscale")
            ))
            .sourceDatabaseId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/primarydb")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    createMode: "Secondary",
    databaseName: "testdb",
    location: "southeastasia",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    secondaryType: "Named",
    serverName: "testsvr",
    sku: {
        capacity: 2,
        name: "HS_Gen4",
        tier: "Hyperscale",
    },
    sourceDatabaseId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/primarydb",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    create_mode="Secondary",
    database_name="testdb",
    location="southeastasia",
    resource_group_name="Default-SQL-SouthEastAsia",
    secondary_type="Named",
    server_name="testsvr",
    sku=azure_native.sql.SkuArgs(
        capacity=2,
        name="HS_Gen4",
        tier="Hyperscale",
    ),
    source_database_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/primarydb")

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      createMode: Secondary
      databaseName: testdb
      location: southeastasia
      resourceGroupName: Default-SQL-SouthEastAsia
      secondaryType: Named
      serverName: testsvr
      sku:
        capacity: 2
        name: HS_Gen4
        tier: Hyperscale
      sourceDatabaseId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-NorthEurope/providers/Microsoft.Sql/servers/testsvr1/databases/primarydb

```

{{% /example %}}
{{% example %}}
### Creates a database from PointInTimeRestore.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        CreateMode = "PointInTimeRestore",
        DatabaseName = "dbpitr",
        Location = "southeastasia",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        RestorePointInTime = "2020-10-22T05:35:31.503Z",
        ServerName = "testsvr",
        SourceDatabaseId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SoutheastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			CreateMode:         pulumi.String("PointInTimeRestore"),
			DatabaseName:       pulumi.String("dbpitr"),
			Location:           pulumi.String("southeastasia"),
			ResourceGroupName:  pulumi.String("Default-SQL-SouthEastAsia"),
			RestorePointInTime: pulumi.String("2020-10-22T05:35:31.503Z"),
			ServerName:         pulumi.String("testsvr"),
			SourceDatabaseId:   pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SoutheastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .createMode("PointInTimeRestore")
            .databaseName("dbpitr")
            .location("southeastasia")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .restorePointInTime("2020-10-22T05:35:31.503Z")
            .serverName("testsvr")
            .sourceDatabaseId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SoutheastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    createMode: "PointInTimeRestore",
    databaseName: "dbpitr",
    location: "southeastasia",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    restorePointInTime: "2020-10-22T05:35:31.503Z",
    serverName: "testsvr",
    sourceDatabaseId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SoutheastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    create_mode="PointInTimeRestore",
    database_name="dbpitr",
    location="southeastasia",
    resource_group_name="Default-SQL-SouthEastAsia",
    restore_point_in_time="2020-10-22T05:35:31.503Z",
    server_name="testsvr",
    source_database_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SoutheastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb")

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      createMode: PointInTimeRestore
      databaseName: dbpitr
      location: southeastasia
      resourceGroupName: Default-SQL-SouthEastAsia
      restorePointInTime: 2020-10-22T05:35:31.503Z
      serverName: testsvr
      sourceDatabaseId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SoutheastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb

```

{{% /example %}}
{{% example %}}
### Creates a database with default mode.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        Collation = "SQL_Latin1_General_CP1_CI_AS",
        CreateMode = "Default",
        DatabaseName = "testdb",
        Location = "southeastasia",
        MaxSizeBytes = 1073741824,
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Name = "S0",
            Tier = "Standard",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			Collation:         pulumi.String("SQL_Latin1_General_CP1_CI_AS"),
			CreateMode:        pulumi.String("Default"),
			DatabaseName:      pulumi.String("testdb"),
			Location:          pulumi.String("southeastasia"),
			MaxSizeBytes:      pulumi.Float64(1073741824),
			ResourceGroupName: pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:        pulumi.String("testsvr"),
			Sku: &sql.SkuArgs{
				Name: pulumi.String("S0"),
				Tier: pulumi.String("Standard"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .collation("SQL_Latin1_General_CP1_CI_AS")
            .createMode("Default")
            .databaseName("testdb")
            .location("southeastasia")
            .maxSizeBytes(1073741824)
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .sku(Map.ofEntries(
                Map.entry("name", "S0"),
                Map.entry("tier", "Standard")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    collation: "SQL_Latin1_General_CP1_CI_AS",
    createMode: "Default",
    databaseName: "testdb",
    location: "southeastasia",
    maxSizeBytes: 1073741824,
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
    sku: {
        name: "S0",
        tier: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    collation="SQL_Latin1_General_CP1_CI_AS",
    create_mode="Default",
    database_name="testdb",
    location="southeastasia",
    max_size_bytes=1073741824,
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr",
    sku=azure_native.sql.SkuArgs(
        name="S0",
        tier="Standard",
    ))

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      collation: SQL_Latin1_General_CP1_CI_AS
      createMode: Default
      databaseName: testdb
      location: southeastasia
      maxSizeBytes: 1.073741824e+09
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr
      sku:
        name: S0
        tier: Standard

```

{{% /example %}}
{{% example %}}
### Creates a database with ledger on.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        DatabaseName = "testdb",
        IsLedgerOn = true,
        Location = "southeastasia",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			DatabaseName:      pulumi.String("testdb"),
			IsLedgerOn:        pulumi.Bool(true),
			Location:          pulumi.String("southeastasia"),
			ResourceGroupName: pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:        pulumi.String("testsvr"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .databaseName("testdb")
            .isLedgerOn(true)
            .location("southeastasia")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    databaseName: "testdb",
    isLedgerOn: true,
    location: "southeastasia",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    database_name="testdb",
    is_ledger_on=True,
    location="southeastasia",
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr")

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      databaseName: testdb
      isLedgerOn: true
      location: southeastasia
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr

```

{{% /example %}}
{{% example %}}
### Creates a database with minimum number of parameters.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        DatabaseName = "testdb",
        Location = "southeastasia",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			DatabaseName:      pulumi.String("testdb"),
			Location:          pulumi.String("southeastasia"),
			ResourceGroupName: pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:        pulumi.String("testsvr"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .databaseName("testdb")
            .location("southeastasia")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    databaseName: "testdb",
    location: "southeastasia",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    database_name="testdb",
    location="southeastasia",
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr")

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      databaseName: testdb
      location: southeastasia
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr

```

{{% /example %}}
{{% example %}}
### Creates a database with preferred maintenance window.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        Collation = "SQL_Latin1_General_CP1_CI_AS",
        CreateMode = "Default",
        DatabaseName = "testdb",
        Location = "southeastasia",
        MaintenanceConfigurationId = "/subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_SouthEastAsia_1",
        MaxSizeBytes = 1073741824,
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
        Sku = new AzureNative.Sql.Inputs.SkuArgs
        {
            Name = "S2",
            Tier = "Standard",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			Collation:                  pulumi.String("SQL_Latin1_General_CP1_CI_AS"),
			CreateMode:                 pulumi.String("Default"),
			DatabaseName:               pulumi.String("testdb"),
			Location:                   pulumi.String("southeastasia"),
			MaintenanceConfigurationId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_SouthEastAsia_1"),
			MaxSizeBytes:               pulumi.Float64(1073741824),
			ResourceGroupName:          pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:                 pulumi.String("testsvr"),
			Sku: &sql.SkuArgs{
				Name: pulumi.String("S2"),
				Tier: pulumi.String("Standard"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .collation("SQL_Latin1_General_CP1_CI_AS")
            .createMode("Default")
            .databaseName("testdb")
            .location("southeastasia")
            .maintenanceConfigurationId("/subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_SouthEastAsia_1")
            .maxSizeBytes(1073741824)
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .sku(Map.ofEntries(
                Map.entry("name", "S2"),
                Map.entry("tier", "Standard")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    collation: "SQL_Latin1_General_CP1_CI_AS",
    createMode: "Default",
    databaseName: "testdb",
    location: "southeastasia",
    maintenanceConfigurationId: "/subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_SouthEastAsia_1",
    maxSizeBytes: 1073741824,
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
    sku: {
        name: "S2",
        tier: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    collation="SQL_Latin1_General_CP1_CI_AS",
    create_mode="Default",
    database_name="testdb",
    location="southeastasia",
    maintenance_configuration_id="/subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_SouthEastAsia_1",
    max_size_bytes=1073741824,
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr",
    sku=azure_native.sql.SkuArgs(
        name="S2",
        tier="Standard",
    ))

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      collation: SQL_Latin1_General_CP1_CI_AS
      createMode: Default
      databaseName: testdb
      location: southeastasia
      maintenanceConfigurationId: /subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Maintenance/publicMaintenanceConfigurations/SQL_SouthEastAsia_1
      maxSizeBytes: 1.073741824e+09
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr
      sku:
        name: S2
        tier: Standard

```

{{% /example %}}
{{% example %}}
### Creates a database with specified backup storage redundancy.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Sql.Database("database", new()
    {
        DatabaseName = "testdb",
        Location = "southeastasia",
        RequestedBackupStorageRedundancy = "Zone",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        ServerName = "testsvr",
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
		_, err := sql.NewDatabase(ctx, "database", &sql.DatabaseArgs{
			DatabaseName:                     pulumi.String("testdb"),
			Location:                         pulumi.String("southeastasia"),
			RequestedBackupStorageRedundancy: pulumi.String("Zone"),
			ResourceGroupName:                pulumi.String("Default-SQL-SouthEastAsia"),
			ServerName:                       pulumi.String("testsvr"),
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
import com.pulumi.azurenative.sql.Database;
import com.pulumi.azurenative.sql.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .databaseName("testdb")
            .location("southeastasia")
            .requestedBackupStorageRedundancy("Zone")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .serverName("testsvr")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.sql.Database("database", {
    databaseName: "testdb",
    location: "southeastasia",
    requestedBackupStorageRedundancy: "Zone",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    serverName: "testsvr",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.sql.Database("database",
    database_name="testdb",
    location="southeastasia",
    requested_backup_storage_redundancy="Zone",
    resource_group_name="Default-SQL-SouthEastAsia",
    server_name="testsvr")

```

```yaml
resources:
  database:
    type: azure-native:sql:Database
    properties:
      databaseName: testdb
      location: southeastasia
      requestedBackupStorageRedundancy: Zone
      resourceGroupName: Default-SQL-SouthEastAsia
      serverName: testsvr

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:Database testdb /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/servers/testsvr/databases/testdb 
```
