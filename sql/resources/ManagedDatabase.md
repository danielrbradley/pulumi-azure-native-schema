A managed database resource.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates a new managed database by restoring from an external backup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedDatabase = new AzureNative.Sql.ManagedDatabase("managedDatabase", new()
    {
        AutoCompleteRestore = true,
        Collation = "SQL_Latin1_General_CP1_CI_AS",
        CreateMode = "RestoreExternalBackup",
        DatabaseName = "managedDatabase",
        LastBackupName = "last_backup_name",
        Location = "southeastasia",
        ManagedInstanceName = "managedInstance",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        StorageContainerSasToken = "sv=2015-12-11&sr=c&sp=rl&sig=1234",
        StorageContainerUri = "https://myaccountname.blob.core.windows.net/backups",
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
		_, err := sql.NewManagedDatabase(ctx, "managedDatabase", &sql.ManagedDatabaseArgs{
			AutoCompleteRestore:      pulumi.Bool(true),
			Collation:                pulumi.String("SQL_Latin1_General_CP1_CI_AS"),
			CreateMode:               pulumi.String("RestoreExternalBackup"),
			DatabaseName:             pulumi.String("managedDatabase"),
			LastBackupName:           pulumi.String("last_backup_name"),
			Location:                 pulumi.String("southeastasia"),
			ManagedInstanceName:      pulumi.String("managedInstance"),
			ResourceGroupName:        pulumi.String("Default-SQL-SouthEastAsia"),
			StorageContainerSasToken: pulumi.String("sv=2015-12-11&sr=c&sp=rl&sig=1234"),
			StorageContainerUri:      pulumi.String("https://myaccountname.blob.core.windows.net/backups"),
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
import com.pulumi.azurenative.sql.ManagedDatabase;
import com.pulumi.azurenative.sql.ManagedDatabaseArgs;
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
        var managedDatabase = new ManagedDatabase("managedDatabase", ManagedDatabaseArgs.builder()        
            .autoCompleteRestore(true)
            .collation("SQL_Latin1_General_CP1_CI_AS")
            .createMode("RestoreExternalBackup")
            .databaseName("managedDatabase")
            .lastBackupName("last_backup_name")
            .location("southeastasia")
            .managedInstanceName("managedInstance")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .storageContainerSasToken("sv=2015-12-11&sr=c&sp=rl&sig=1234")
            .storageContainerUri("https://myaccountname.blob.core.windows.net/backups")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedDatabase = new azure_native.sql.ManagedDatabase("managedDatabase", {
    autoCompleteRestore: true,
    collation: "SQL_Latin1_General_CP1_CI_AS",
    createMode: "RestoreExternalBackup",
    databaseName: "managedDatabase",
    lastBackupName: "last_backup_name",
    location: "southeastasia",
    managedInstanceName: "managedInstance",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    storageContainerSasToken: "sv=2015-12-11&sr=c&sp=rl&sig=1234",
    storageContainerUri: "https://myaccountname.blob.core.windows.net/backups",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_database = azure_native.sql.ManagedDatabase("managedDatabase",
    auto_complete_restore=True,
    collation="SQL_Latin1_General_CP1_CI_AS",
    create_mode="RestoreExternalBackup",
    database_name="managedDatabase",
    last_backup_name="last_backup_name",
    location="southeastasia",
    managed_instance_name="managedInstance",
    resource_group_name="Default-SQL-SouthEastAsia",
    storage_container_sas_token="sv=2015-12-11&sr=c&sp=rl&sig=1234",
    storage_container_uri="https://myaccountname.blob.core.windows.net/backups")

```

```yaml
resources:
  managedDatabase:
    type: azure-native:sql:ManagedDatabase
    properties:
      autoCompleteRestore: true
      collation: SQL_Latin1_General_CP1_CI_AS
      createMode: RestoreExternalBackup
      databaseName: managedDatabase
      lastBackupName: last_backup_name
      location: southeastasia
      managedInstanceName: managedInstance
      resourceGroupName: Default-SQL-SouthEastAsia
      storageContainerSasToken: sv=2015-12-11&sr=c&sp=rl&sig=1234
      storageContainerUri: https://myaccountname.blob.core.windows.net/backups

```

{{% /example %}}
{{% example %}}
### Creates a new managed database from restoring a geo-replicated backup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedDatabase = new AzureNative.Sql.ManagedDatabase("managedDatabase", new()
    {
        CreateMode = "Recovery",
        DatabaseName = "testdb_recovered",
        Location = "southeastasia",
        ManagedInstanceName = "server1",
        RecoverableDatabaseId = "/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/Default-SQL-WestEurope/providers/Microsoft.Sql/managedInstances/testsvr/recoverableDatabases/testdb",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
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
		_, err := sql.NewManagedDatabase(ctx, "managedDatabase", &sql.ManagedDatabaseArgs{
			CreateMode:            pulumi.String("Recovery"),
			DatabaseName:          pulumi.String("testdb_recovered"),
			Location:              pulumi.String("southeastasia"),
			ManagedInstanceName:   pulumi.String("server1"),
			RecoverableDatabaseId: pulumi.String("/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/Default-SQL-WestEurope/providers/Microsoft.Sql/managedInstances/testsvr/recoverableDatabases/testdb"),
			ResourceGroupName:     pulumi.String("Default-SQL-SouthEastAsia"),
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
import com.pulumi.azurenative.sql.ManagedDatabase;
import com.pulumi.azurenative.sql.ManagedDatabaseArgs;
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
        var managedDatabase = new ManagedDatabase("managedDatabase", ManagedDatabaseArgs.builder()        
            .createMode("Recovery")
            .databaseName("testdb_recovered")
            .location("southeastasia")
            .managedInstanceName("server1")
            .recoverableDatabaseId("/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/Default-SQL-WestEurope/providers/Microsoft.Sql/managedInstances/testsvr/recoverableDatabases/testdb")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedDatabase = new azure_native.sql.ManagedDatabase("managedDatabase", {
    createMode: "Recovery",
    databaseName: "testdb_recovered",
    location: "southeastasia",
    managedInstanceName: "server1",
    recoverableDatabaseId: "/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/Default-SQL-WestEurope/providers/Microsoft.Sql/managedInstances/testsvr/recoverableDatabases/testdb",
    resourceGroupName: "Default-SQL-SouthEastAsia",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_database = azure_native.sql.ManagedDatabase("managedDatabase",
    create_mode="Recovery",
    database_name="testdb_recovered",
    location="southeastasia",
    managed_instance_name="server1",
    recoverable_database_id="/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/Default-SQL-WestEurope/providers/Microsoft.Sql/managedInstances/testsvr/recoverableDatabases/testdb",
    resource_group_name="Default-SQL-SouthEastAsia")

```

```yaml
resources:
  managedDatabase:
    type: azure-native:sql:ManagedDatabase
    properties:
      createMode: Recovery
      databaseName: testdb_recovered
      location: southeastasia
      managedInstanceName: server1
      recoverableDatabaseId: /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/Default-SQL-WestEurope/providers/Microsoft.Sql/managedInstances/testsvr/recoverableDatabases/testdb
      resourceGroupName: Default-SQL-SouthEastAsia

```

{{% /example %}}
{{% example %}}
### Creates a new managed database from restoring a long term retention backup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedDatabase = new AzureNative.Sql.ManagedDatabase("managedDatabase", new()
    {
        Collation = "SQL_Latin1_General_CP1_CI_AS",
        CreateMode = "RestoreExternalBackup",
        DatabaseName = "managedDatabase",
        Location = "southeastasia",
        ManagedInstanceName = "managedInstance",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        StorageContainerSasToken = "sv=2015-12-11&sr=c&sp=rl&sig=1234",
        StorageContainerUri = "https://myaccountname.blob.core.windows.net/backups",
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
		_, err := sql.NewManagedDatabase(ctx, "managedDatabase", &sql.ManagedDatabaseArgs{
			Collation:                pulumi.String("SQL_Latin1_General_CP1_CI_AS"),
			CreateMode:               pulumi.String("RestoreExternalBackup"),
			DatabaseName:             pulumi.String("managedDatabase"),
			Location:                 pulumi.String("southeastasia"),
			ManagedInstanceName:      pulumi.String("managedInstance"),
			ResourceGroupName:        pulumi.String("Default-SQL-SouthEastAsia"),
			StorageContainerSasToken: pulumi.String("sv=2015-12-11&sr=c&sp=rl&sig=1234"),
			StorageContainerUri:      pulumi.String("https://myaccountname.blob.core.windows.net/backups"),
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
import com.pulumi.azurenative.sql.ManagedDatabase;
import com.pulumi.azurenative.sql.ManagedDatabaseArgs;
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
        var managedDatabase = new ManagedDatabase("managedDatabase", ManagedDatabaseArgs.builder()        
            .collation("SQL_Latin1_General_CP1_CI_AS")
            .createMode("RestoreExternalBackup")
            .databaseName("managedDatabase")
            .location("southeastasia")
            .managedInstanceName("managedInstance")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .storageContainerSasToken("sv=2015-12-11&sr=c&sp=rl&sig=1234")
            .storageContainerUri("https://myaccountname.blob.core.windows.net/backups")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedDatabase = new azure_native.sql.ManagedDatabase("managedDatabase", {
    collation: "SQL_Latin1_General_CP1_CI_AS",
    createMode: "RestoreExternalBackup",
    databaseName: "managedDatabase",
    location: "southeastasia",
    managedInstanceName: "managedInstance",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    storageContainerSasToken: "sv=2015-12-11&sr=c&sp=rl&sig=1234",
    storageContainerUri: "https://myaccountname.blob.core.windows.net/backups",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_database = azure_native.sql.ManagedDatabase("managedDatabase",
    collation="SQL_Latin1_General_CP1_CI_AS",
    create_mode="RestoreExternalBackup",
    database_name="managedDatabase",
    location="southeastasia",
    managed_instance_name="managedInstance",
    resource_group_name="Default-SQL-SouthEastAsia",
    storage_container_sas_token="sv=2015-12-11&sr=c&sp=rl&sig=1234",
    storage_container_uri="https://myaccountname.blob.core.windows.net/backups")

```

```yaml
resources:
  managedDatabase:
    type: azure-native:sql:ManagedDatabase
    properties:
      collation: SQL_Latin1_General_CP1_CI_AS
      createMode: RestoreExternalBackup
      databaseName: managedDatabase
      location: southeastasia
      managedInstanceName: managedInstance
      resourceGroupName: Default-SQL-SouthEastAsia
      storageContainerSasToken: sv=2015-12-11&sr=c&sp=rl&sig=1234
      storageContainerUri: https://myaccountname.blob.core.windows.net/backups

```

{{% /example %}}
{{% example %}}
### Creates a new managed database using point in time restore
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedDatabase = new AzureNative.Sql.ManagedDatabase("managedDatabase", new()
    {
        CreateMode = "PointInTimeRestore",
        DatabaseName = "managedDatabase",
        Location = "southeastasia",
        ManagedInstanceName = "managedInstance",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        RestorePointInTime = "2017-07-14T05:35:31.503Z",
        SourceDatabaseId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/managedInstances/testsvr/databases/testdb",
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
		_, err := sql.NewManagedDatabase(ctx, "managedDatabase", &sql.ManagedDatabaseArgs{
			CreateMode:          pulumi.String("PointInTimeRestore"),
			DatabaseName:        pulumi.String("managedDatabase"),
			Location:            pulumi.String("southeastasia"),
			ManagedInstanceName: pulumi.String("managedInstance"),
			ResourceGroupName:   pulumi.String("Default-SQL-SouthEastAsia"),
			RestorePointInTime:  pulumi.String("2017-07-14T05:35:31.503Z"),
			SourceDatabaseId:    pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/managedInstances/testsvr/databases/testdb"),
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
import com.pulumi.azurenative.sql.ManagedDatabase;
import com.pulumi.azurenative.sql.ManagedDatabaseArgs;
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
        var managedDatabase = new ManagedDatabase("managedDatabase", ManagedDatabaseArgs.builder()        
            .createMode("PointInTimeRestore")
            .databaseName("managedDatabase")
            .location("southeastasia")
            .managedInstanceName("managedInstance")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .restorePointInTime("2017-07-14T05:35:31.503Z")
            .sourceDatabaseId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/managedInstances/testsvr/databases/testdb")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedDatabase = new azure_native.sql.ManagedDatabase("managedDatabase", {
    createMode: "PointInTimeRestore",
    databaseName: "managedDatabase",
    location: "southeastasia",
    managedInstanceName: "managedInstance",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    restorePointInTime: "2017-07-14T05:35:31.503Z",
    sourceDatabaseId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/managedInstances/testsvr/databases/testdb",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_database = azure_native.sql.ManagedDatabase("managedDatabase",
    create_mode="PointInTimeRestore",
    database_name="managedDatabase",
    location="southeastasia",
    managed_instance_name="managedInstance",
    resource_group_name="Default-SQL-SouthEastAsia",
    restore_point_in_time="2017-07-14T05:35:31.503Z",
    source_database_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/managedInstances/testsvr/databases/testdb")

```

```yaml
resources:
  managedDatabase:
    type: azure-native:sql:ManagedDatabase
    properties:
      createMode: PointInTimeRestore
      databaseName: managedDatabase
      location: southeastasia
      managedInstanceName: managedInstance
      resourceGroupName: Default-SQL-SouthEastAsia
      restorePointInTime: 2017-07-14T05:35:31.503Z
      sourceDatabaseId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/managedInstances/testsvr/databases/testdb

```

{{% /example %}}
{{% example %}}
### Creates a new managed database with maximal properties
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedDatabase = new AzureNative.Sql.ManagedDatabase("managedDatabase", new()
    {
        DatabaseName = "managedDatabase",
        Location = "southeastasia",
        ManagedInstanceName = "managedInstance",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        Tags = 
        {
            { "tagKey1", "TagValue1" },
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
		_, err := sql.NewManagedDatabase(ctx, "managedDatabase", &sql.ManagedDatabaseArgs{
			DatabaseName:        pulumi.String("managedDatabase"),
			Location:            pulumi.String("southeastasia"),
			ManagedInstanceName: pulumi.String("managedInstance"),
			ResourceGroupName:   pulumi.String("Default-SQL-SouthEastAsia"),
			Tags: pulumi.StringMap{
				"tagKey1": pulumi.String("TagValue1"),
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
import com.pulumi.azurenative.sql.ManagedDatabase;
import com.pulumi.azurenative.sql.ManagedDatabaseArgs;
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
        var managedDatabase = new ManagedDatabase("managedDatabase", ManagedDatabaseArgs.builder()        
            .databaseName("managedDatabase")
            .location("southeastasia")
            .managedInstanceName("managedInstance")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .tags(Map.of("tagKey1", "TagValue1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedDatabase = new azure_native.sql.ManagedDatabase("managedDatabase", {
    databaseName: "managedDatabase",
    location: "southeastasia",
    managedInstanceName: "managedInstance",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    tags: {
        tagKey1: "TagValue1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_database = azure_native.sql.ManagedDatabase("managedDatabase",
    database_name="managedDatabase",
    location="southeastasia",
    managed_instance_name="managedInstance",
    resource_group_name="Default-SQL-SouthEastAsia",
    tags={
        "tagKey1": "TagValue1",
    })

```

```yaml
resources:
  managedDatabase:
    type: azure-native:sql:ManagedDatabase
    properties:
      databaseName: managedDatabase
      location: southeastasia
      managedInstanceName: managedInstance
      resourceGroupName: Default-SQL-SouthEastAsia
      tags:
        tagKey1: TagValue1

```

{{% /example %}}
{{% example %}}
### Creates a new managed database with minimal properties
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedDatabase = new AzureNative.Sql.ManagedDatabase("managedDatabase", new()
    {
        DatabaseName = "managedDatabase",
        Location = "southeastasia",
        ManagedInstanceName = "managedInstance",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
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
		_, err := sql.NewManagedDatabase(ctx, "managedDatabase", &sql.ManagedDatabaseArgs{
			DatabaseName:        pulumi.String("managedDatabase"),
			Location:            pulumi.String("southeastasia"),
			ManagedInstanceName: pulumi.String("managedInstance"),
			ResourceGroupName:   pulumi.String("Default-SQL-SouthEastAsia"),
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
import com.pulumi.azurenative.sql.ManagedDatabase;
import com.pulumi.azurenative.sql.ManagedDatabaseArgs;
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
        var managedDatabase = new ManagedDatabase("managedDatabase", ManagedDatabaseArgs.builder()        
            .databaseName("managedDatabase")
            .location("southeastasia")
            .managedInstanceName("managedInstance")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedDatabase = new azure_native.sql.ManagedDatabase("managedDatabase", {
    databaseName: "managedDatabase",
    location: "southeastasia",
    managedInstanceName: "managedInstance",
    resourceGroupName: "Default-SQL-SouthEastAsia",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_database = azure_native.sql.ManagedDatabase("managedDatabase",
    database_name="managedDatabase",
    location="southeastasia",
    managed_instance_name="managedInstance",
    resource_group_name="Default-SQL-SouthEastAsia")

```

```yaml
resources:
  managedDatabase:
    type: azure-native:sql:ManagedDatabase
    properties:
      databaseName: managedDatabase
      location: southeastasia
      managedInstanceName: managedInstance
      resourceGroupName: Default-SQL-SouthEastAsia

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ManagedDatabase testdb1 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/managedInstances/testsvr/databases/testdb1 
```
