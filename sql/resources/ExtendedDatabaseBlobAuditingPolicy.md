An extended database blob auditing policy.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an extended database's azure monitor auditing policy with minimal parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var extendedDatabaseBlobAuditingPolicy = new AzureNative.Sql.ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy", new()
    {
        BlobAuditingPolicyName = "default",
        DatabaseName = "testdb",
        IsAzureMonitorTargetEnabled = true,
        ResourceGroupName = "blobauditingtest-4799",
        ServerName = "blobauditingtest-6440",
        State = AzureNative.Sql.BlobAuditingPolicyState.Enabled,
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
		_, err := sql.NewExtendedDatabaseBlobAuditingPolicy(ctx, "extendedDatabaseBlobAuditingPolicy", &sql.ExtendedDatabaseBlobAuditingPolicyArgs{
			BlobAuditingPolicyName:      pulumi.String("default"),
			DatabaseName:                pulumi.String("testdb"),
			IsAzureMonitorTargetEnabled: pulumi.Bool(true),
			ResourceGroupName:           pulumi.String("blobauditingtest-4799"),
			ServerName:                  pulumi.String("blobauditingtest-6440"),
			State:                       sql.BlobAuditingPolicyStateEnabled,
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
import com.pulumi.azurenative.sql.ExtendedDatabaseBlobAuditingPolicy;
import com.pulumi.azurenative.sql.ExtendedDatabaseBlobAuditingPolicyArgs;
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
        var extendedDatabaseBlobAuditingPolicy = new ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy", ExtendedDatabaseBlobAuditingPolicyArgs.builder()        
            .blobAuditingPolicyName("default")
            .databaseName("testdb")
            .isAzureMonitorTargetEnabled(true)
            .resourceGroupName("blobauditingtest-4799")
            .serverName("blobauditingtest-6440")
            .state("Enabled")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const extendedDatabaseBlobAuditingPolicy = new azure_native.sql.ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy", {
    blobAuditingPolicyName: "default",
    databaseName: "testdb",
    isAzureMonitorTargetEnabled: true,
    resourceGroupName: "blobauditingtest-4799",
    serverName: "blobauditingtest-6440",
    state: azure_native.sql.BlobAuditingPolicyState.Enabled,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

extended_database_blob_auditing_policy = azure_native.sql.ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy",
    blob_auditing_policy_name="default",
    database_name="testdb",
    is_azure_monitor_target_enabled=True,
    resource_group_name="blobauditingtest-4799",
    server_name="blobauditingtest-6440",
    state=azure_native.sql.BlobAuditingPolicyState.ENABLED)

```

```yaml
resources:
  extendedDatabaseBlobAuditingPolicy:
    type: azure-native:sql:ExtendedDatabaseBlobAuditingPolicy
    properties:
      blobAuditingPolicyName: default
      databaseName: testdb
      isAzureMonitorTargetEnabled: true
      resourceGroupName: blobauditingtest-4799
      serverName: blobauditingtest-6440
      state: Enabled

```

{{% /example %}}
{{% example %}}
### Create or update an extended database's blob auditing policy with all parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var extendedDatabaseBlobAuditingPolicy = new AzureNative.Sql.ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy", new()
    {
        AuditActionsAndGroups = new[]
        {
            "DATABASE_LOGOUT_GROUP",
            "DATABASE_ROLE_MEMBER_CHANGE_GROUP",
            "UPDATE on database::TestDatabaseName by public",
        },
        BlobAuditingPolicyName = "default",
        DatabaseName = "testdb",
        IsAzureMonitorTargetEnabled = true,
        IsStorageSecondaryKeyInUse = false,
        PredicateExpression = "statement = 'select 1'",
        QueueDelayMs = 4000,
        ResourceGroupName = "blobauditingtest-4799",
        RetentionDays = 6,
        ServerName = "blobauditingtest-6440",
        State = AzureNative.Sql.BlobAuditingPolicyState.Enabled,
        StorageAccountAccessKey = "sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
        StorageAccountSubscriptionId = "00000000-1234-0000-5678-000000000000",
        StorageEndpoint = "https://mystorage.blob.core.windows.net",
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
		_, err := sql.NewExtendedDatabaseBlobAuditingPolicy(ctx, "extendedDatabaseBlobAuditingPolicy", &sql.ExtendedDatabaseBlobAuditingPolicyArgs{
			AuditActionsAndGroups: pulumi.StringArray{
				pulumi.String("DATABASE_LOGOUT_GROUP"),
				pulumi.String("DATABASE_ROLE_MEMBER_CHANGE_GROUP"),
				pulumi.String("UPDATE on database::TestDatabaseName by public"),
			},
			BlobAuditingPolicyName:       pulumi.String("default"),
			DatabaseName:                 pulumi.String("testdb"),
			IsAzureMonitorTargetEnabled:  pulumi.Bool(true),
			IsStorageSecondaryKeyInUse:   pulumi.Bool(false),
			PredicateExpression:          pulumi.String("statement = 'select 1'"),
			QueueDelayMs:                 pulumi.Int(4000),
			ResourceGroupName:            pulumi.String("blobauditingtest-4799"),
			RetentionDays:                pulumi.Int(6),
			ServerName:                   pulumi.String("blobauditingtest-6440"),
			State:                        sql.BlobAuditingPolicyStateEnabled,
			StorageAccountAccessKey:      pulumi.String("sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD=="),
			StorageAccountSubscriptionId: pulumi.String("00000000-1234-0000-5678-000000000000"),
			StorageEndpoint:              pulumi.String("https://mystorage.blob.core.windows.net"),
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
import com.pulumi.azurenative.sql.ExtendedDatabaseBlobAuditingPolicy;
import com.pulumi.azurenative.sql.ExtendedDatabaseBlobAuditingPolicyArgs;
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
        var extendedDatabaseBlobAuditingPolicy = new ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy", ExtendedDatabaseBlobAuditingPolicyArgs.builder()        
            .auditActionsAndGroups(            
                "DATABASE_LOGOUT_GROUP",
                "DATABASE_ROLE_MEMBER_CHANGE_GROUP",
                "UPDATE on database::TestDatabaseName by public")
            .blobAuditingPolicyName("default")
            .databaseName("testdb")
            .isAzureMonitorTargetEnabled(true)
            .isStorageSecondaryKeyInUse(false)
            .predicateExpression("statement = 'select 1'")
            .queueDelayMs(4000)
            .resourceGroupName("blobauditingtest-4799")
            .retentionDays(6)
            .serverName("blobauditingtest-6440")
            .state("Enabled")
            .storageAccountAccessKey("sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==")
            .storageAccountSubscriptionId("00000000-1234-0000-5678-000000000000")
            .storageEndpoint("https://mystorage.blob.core.windows.net")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const extendedDatabaseBlobAuditingPolicy = new azure_native.sql.ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy", {
    auditActionsAndGroups: [
        "DATABASE_LOGOUT_GROUP",
        "DATABASE_ROLE_MEMBER_CHANGE_GROUP",
        "UPDATE on database::TestDatabaseName by public",
    ],
    blobAuditingPolicyName: "default",
    databaseName: "testdb",
    isAzureMonitorTargetEnabled: true,
    isStorageSecondaryKeyInUse: false,
    predicateExpression: "statement = 'select 1'",
    queueDelayMs: 4000,
    resourceGroupName: "blobauditingtest-4799",
    retentionDays: 6,
    serverName: "blobauditingtest-6440",
    state: azure_native.sql.BlobAuditingPolicyState.Enabled,
    storageAccountAccessKey: "sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
    storageAccountSubscriptionId: "00000000-1234-0000-5678-000000000000",
    storageEndpoint: "https://mystorage.blob.core.windows.net",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

extended_database_blob_auditing_policy = azure_native.sql.ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy",
    audit_actions_and_groups=[
        "DATABASE_LOGOUT_GROUP",
        "DATABASE_ROLE_MEMBER_CHANGE_GROUP",
        "UPDATE on database::TestDatabaseName by public",
    ],
    blob_auditing_policy_name="default",
    database_name="testdb",
    is_azure_monitor_target_enabled=True,
    is_storage_secondary_key_in_use=False,
    predicate_expression="statement = 'select 1'",
    queue_delay_ms=4000,
    resource_group_name="blobauditingtest-4799",
    retention_days=6,
    server_name="blobauditingtest-6440",
    state=azure_native.sql.BlobAuditingPolicyState.ENABLED,
    storage_account_access_key="sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
    storage_account_subscription_id="00000000-1234-0000-5678-000000000000",
    storage_endpoint="https://mystorage.blob.core.windows.net")

```

```yaml
resources:
  extendedDatabaseBlobAuditingPolicy:
    type: azure-native:sql:ExtendedDatabaseBlobAuditingPolicy
    properties:
      auditActionsAndGroups:
        - DATABASE_LOGOUT_GROUP
        - DATABASE_ROLE_MEMBER_CHANGE_GROUP
        - UPDATE on database::TestDatabaseName by public
      blobAuditingPolicyName: default
      databaseName: testdb
      isAzureMonitorTargetEnabled: true
      isStorageSecondaryKeyInUse: false
      predicateExpression: statement = 'select 1'
      queueDelayMs: 4000
      resourceGroupName: blobauditingtest-4799
      retentionDays: 6
      serverName: blobauditingtest-6440
      state: Enabled
      storageAccountAccessKey: sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==
      storageAccountSubscriptionId: 00000000-1234-0000-5678-000000000000
      storageEndpoint: https://mystorage.blob.core.windows.net

```

{{% /example %}}
{{% example %}}
### Create or update an extended database's blob auditing policy with minimal parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var extendedDatabaseBlobAuditingPolicy = new AzureNative.Sql.ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy", new()
    {
        BlobAuditingPolicyName = "default",
        DatabaseName = "testdb",
        ResourceGroupName = "blobauditingtest-4799",
        ServerName = "blobauditingtest-6440",
        State = AzureNative.Sql.BlobAuditingPolicyState.Enabled,
        StorageAccountAccessKey = "sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
        StorageEndpoint = "https://mystorage.blob.core.windows.net",
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
		_, err := sql.NewExtendedDatabaseBlobAuditingPolicy(ctx, "extendedDatabaseBlobAuditingPolicy", &sql.ExtendedDatabaseBlobAuditingPolicyArgs{
			BlobAuditingPolicyName:  pulumi.String("default"),
			DatabaseName:            pulumi.String("testdb"),
			ResourceGroupName:       pulumi.String("blobauditingtest-4799"),
			ServerName:              pulumi.String("blobauditingtest-6440"),
			State:                   sql.BlobAuditingPolicyStateEnabled,
			StorageAccountAccessKey: pulumi.String("sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD=="),
			StorageEndpoint:         pulumi.String("https://mystorage.blob.core.windows.net"),
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
import com.pulumi.azurenative.sql.ExtendedDatabaseBlobAuditingPolicy;
import com.pulumi.azurenative.sql.ExtendedDatabaseBlobAuditingPolicyArgs;
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
        var extendedDatabaseBlobAuditingPolicy = new ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy", ExtendedDatabaseBlobAuditingPolicyArgs.builder()        
            .blobAuditingPolicyName("default")
            .databaseName("testdb")
            .resourceGroupName("blobauditingtest-4799")
            .serverName("blobauditingtest-6440")
            .state("Enabled")
            .storageAccountAccessKey("sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==")
            .storageEndpoint("https://mystorage.blob.core.windows.net")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const extendedDatabaseBlobAuditingPolicy = new azure_native.sql.ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy", {
    blobAuditingPolicyName: "default",
    databaseName: "testdb",
    resourceGroupName: "blobauditingtest-4799",
    serverName: "blobauditingtest-6440",
    state: azure_native.sql.BlobAuditingPolicyState.Enabled,
    storageAccountAccessKey: "sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
    storageEndpoint: "https://mystorage.blob.core.windows.net",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

extended_database_blob_auditing_policy = azure_native.sql.ExtendedDatabaseBlobAuditingPolicy("extendedDatabaseBlobAuditingPolicy",
    blob_auditing_policy_name="default",
    database_name="testdb",
    resource_group_name="blobauditingtest-4799",
    server_name="blobauditingtest-6440",
    state=azure_native.sql.BlobAuditingPolicyState.ENABLED,
    storage_account_access_key="sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
    storage_endpoint="https://mystorage.blob.core.windows.net")

```

```yaml
resources:
  extendedDatabaseBlobAuditingPolicy:
    type: azure-native:sql:ExtendedDatabaseBlobAuditingPolicy
    properties:
      blobAuditingPolicyName: default
      databaseName: testdb
      resourceGroupName: blobauditingtest-4799
      serverName: blobauditingtest-6440
      state: Enabled
      storageAccountAccessKey: sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==
      storageEndpoint: https://mystorage.blob.core.windows.net

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ExtendedDatabaseBlobAuditingPolicy default /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/blobauditingtest-4799/providers/Microsoft.Sql/servers/blobauditingtest-6440/databases/testdb 
```
