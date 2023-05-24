An extended server blob auditing policy.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update a server's extended blob auditing policy with all parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var extendedServerBlobAuditingPolicy = new AzureNative.Sql.ExtendedServerBlobAuditingPolicy("extendedServerBlobAuditingPolicy", new()
    {
        AuditActionsAndGroups = new[]
        {
            "SUCCESSFUL_DATABASE_AUTHENTICATION_GROUP",
            "FAILED_DATABASE_AUTHENTICATION_GROUP",
            "BATCH_COMPLETED_GROUP",
        },
        BlobAuditingPolicyName = "default",
        IsAzureMonitorTargetEnabled = true,
        IsStorageSecondaryKeyInUse = false,
        PredicateExpression = "object_name = 'SensitiveData'",
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
		_, err := sql.NewExtendedServerBlobAuditingPolicy(ctx, "extendedServerBlobAuditingPolicy", &sql.ExtendedServerBlobAuditingPolicyArgs{
			AuditActionsAndGroups: pulumi.StringArray{
				pulumi.String("SUCCESSFUL_DATABASE_AUTHENTICATION_GROUP"),
				pulumi.String("FAILED_DATABASE_AUTHENTICATION_GROUP"),
				pulumi.String("BATCH_COMPLETED_GROUP"),
			},
			BlobAuditingPolicyName:       pulumi.String("default"),
			IsAzureMonitorTargetEnabled:  pulumi.Bool(true),
			IsStorageSecondaryKeyInUse:   pulumi.Bool(false),
			PredicateExpression:          pulumi.String("object_name = 'SensitiveData'"),
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
import com.pulumi.azurenative.sql.ExtendedServerBlobAuditingPolicy;
import com.pulumi.azurenative.sql.ExtendedServerBlobAuditingPolicyArgs;
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
        var extendedServerBlobAuditingPolicy = new ExtendedServerBlobAuditingPolicy("extendedServerBlobAuditingPolicy", ExtendedServerBlobAuditingPolicyArgs.builder()        
            .auditActionsAndGroups(            
                "SUCCESSFUL_DATABASE_AUTHENTICATION_GROUP",
                "FAILED_DATABASE_AUTHENTICATION_GROUP",
                "BATCH_COMPLETED_GROUP")
            .blobAuditingPolicyName("default")
            .isAzureMonitorTargetEnabled(true)
            .isStorageSecondaryKeyInUse(false)
            .predicateExpression("object_name = 'SensitiveData'")
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

const extendedServerBlobAuditingPolicy = new azure_native.sql.ExtendedServerBlobAuditingPolicy("extendedServerBlobAuditingPolicy", {
    auditActionsAndGroups: [
        "SUCCESSFUL_DATABASE_AUTHENTICATION_GROUP",
        "FAILED_DATABASE_AUTHENTICATION_GROUP",
        "BATCH_COMPLETED_GROUP",
    ],
    blobAuditingPolicyName: "default",
    isAzureMonitorTargetEnabled: true,
    isStorageSecondaryKeyInUse: false,
    predicateExpression: "object_name = 'SensitiveData'",
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

extended_server_blob_auditing_policy = azure_native.sql.ExtendedServerBlobAuditingPolicy("extendedServerBlobAuditingPolicy",
    audit_actions_and_groups=[
        "SUCCESSFUL_DATABASE_AUTHENTICATION_GROUP",
        "FAILED_DATABASE_AUTHENTICATION_GROUP",
        "BATCH_COMPLETED_GROUP",
    ],
    blob_auditing_policy_name="default",
    is_azure_monitor_target_enabled=True,
    is_storage_secondary_key_in_use=False,
    predicate_expression="object_name = 'SensitiveData'",
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
  extendedServerBlobAuditingPolicy:
    type: azure-native:sql:ExtendedServerBlobAuditingPolicy
    properties:
      auditActionsAndGroups:
        - SUCCESSFUL_DATABASE_AUTHENTICATION_GROUP
        - FAILED_DATABASE_AUTHENTICATION_GROUP
        - BATCH_COMPLETED_GROUP
      blobAuditingPolicyName: default
      isAzureMonitorTargetEnabled: true
      isStorageSecondaryKeyInUse: false
      predicateExpression: object_name = 'SensitiveData'
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
### Update a server's extended blob auditing policy with minimal parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var extendedServerBlobAuditingPolicy = new AzureNative.Sql.ExtendedServerBlobAuditingPolicy("extendedServerBlobAuditingPolicy", new()
    {
        BlobAuditingPolicyName = "default",
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
		_, err := sql.NewExtendedServerBlobAuditingPolicy(ctx, "extendedServerBlobAuditingPolicy", &sql.ExtendedServerBlobAuditingPolicyArgs{
			BlobAuditingPolicyName:  pulumi.String("default"),
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
import com.pulumi.azurenative.sql.ExtendedServerBlobAuditingPolicy;
import com.pulumi.azurenative.sql.ExtendedServerBlobAuditingPolicyArgs;
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
        var extendedServerBlobAuditingPolicy = new ExtendedServerBlobAuditingPolicy("extendedServerBlobAuditingPolicy", ExtendedServerBlobAuditingPolicyArgs.builder()        
            .blobAuditingPolicyName("default")
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

const extendedServerBlobAuditingPolicy = new azure_native.sql.ExtendedServerBlobAuditingPolicy("extendedServerBlobAuditingPolicy", {
    blobAuditingPolicyName: "default",
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

extended_server_blob_auditing_policy = azure_native.sql.ExtendedServerBlobAuditingPolicy("extendedServerBlobAuditingPolicy",
    blob_auditing_policy_name="default",
    resource_group_name="blobauditingtest-4799",
    server_name="blobauditingtest-6440",
    state=azure_native.sql.BlobAuditingPolicyState.ENABLED,
    storage_account_access_key="sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
    storage_endpoint="https://mystorage.blob.core.windows.net")

```

```yaml
resources:
  extendedServerBlobAuditingPolicy:
    type: azure-native:sql:ExtendedServerBlobAuditingPolicy
    properties:
      blobAuditingPolicyName: default
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
$ pulumi import azure-native:sql:ExtendedServerBlobAuditingPolicy default /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/blobauditingtest-4799/providers/Microsoft.Sql/servers/blobauditingtest-6440/extendedAuditingSettings/default 
```
