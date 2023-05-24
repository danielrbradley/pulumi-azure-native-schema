Contains information about an Azure Batch account.
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### BatchAccountCreate_BYOS
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var batchAccount = new AzureNative.Batch.BatchAccount("batchAccount", new()
    {
        AccountName = "sampleacct",
        AutoStorage = new AzureNative.Batch.Inputs.AutoStorageBasePropertiesArgs
        {
            StorageAccountId = "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
        },
        KeyVaultReference = new AzureNative.Batch.Inputs.KeyVaultReferenceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample",
            Url = "http://sample.vault.azure.net/",
        },
        Location = "japaneast",
        PoolAllocationMode = AzureNative.Batch.PoolAllocationMode.UserSubscription,
        ResourceGroupName = "default-azurebatch-japaneast",
    });

});


```

```go
package main

import (
	batch "github.com/pulumi/pulumi-azure-native-sdk/batch"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := batch.NewBatchAccount(ctx, "batchAccount", &batch.BatchAccountArgs{
			AccountName: pulumi.String("sampleacct"),
			AutoStorage: &batch.AutoStorageBasePropertiesArgs{
				StorageAccountId: pulumi.String("/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage"),
			},
			KeyVaultReference: &batch.KeyVaultReferenceArgs{
				Id:  pulumi.String("/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample"),
				Url: pulumi.String("http://sample.vault.azure.net/"),
			},
			Location:           pulumi.String("japaneast"),
			PoolAllocationMode: batch.PoolAllocationModeUserSubscription,
			ResourceGroupName:  pulumi.String("default-azurebatch-japaneast"),
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
import com.pulumi.azurenative.batch.BatchAccount;
import com.pulumi.azurenative.batch.BatchAccountArgs;
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
        var batchAccount = new BatchAccount("batchAccount", BatchAccountArgs.builder()        
            .accountName("sampleacct")
            .autoStorage(Map.of("storageAccountId", "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage"))
            .keyVaultReference(Map.ofEntries(
                Map.entry("id", "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample"),
                Map.entry("url", "http://sample.vault.azure.net/")
            ))
            .location("japaneast")
            .poolAllocationMode("UserSubscription")
            .resourceGroupName("default-azurebatch-japaneast")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const batchAccount = new azure_native.batch.BatchAccount("batchAccount", {
    accountName: "sampleacct",
    autoStorage: {
        storageAccountId: "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
    },
    keyVaultReference: {
        id: "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample",
        url: "http://sample.vault.azure.net/",
    },
    location: "japaneast",
    poolAllocationMode: azure_native.batch.PoolAllocationMode.UserSubscription,
    resourceGroupName: "default-azurebatch-japaneast",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

batch_account = azure_native.batch.BatchAccount("batchAccount",
    account_name="sampleacct",
    auto_storage=azure_native.batch.AutoStorageBasePropertiesArgs(
        storage_account_id="/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
    ),
    key_vault_reference=azure_native.batch.KeyVaultReferenceArgs(
        id="/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample",
        url="http://sample.vault.azure.net/",
    ),
    location="japaneast",
    pool_allocation_mode=azure_native.batch.PoolAllocationMode.USER_SUBSCRIPTION,
    resource_group_name="default-azurebatch-japaneast")

```

```yaml
resources:
  batchAccount:
    type: azure-native:batch:BatchAccount
    properties:
      accountName: sampleacct
      autoStorage:
        storageAccountId: /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage
      keyVaultReference:
        id: /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample
        url: http://sample.vault.azure.net/
      location: japaneast
      poolAllocationMode: UserSubscription
      resourceGroupName: default-azurebatch-japaneast

```

{{% /example %}}
{{% example %}}
### BatchAccountCreate_Default
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var batchAccount = new AzureNative.Batch.BatchAccount("batchAccount", new()
    {
        AccountName = "sampleacct",
        AutoStorage = new AzureNative.Batch.Inputs.AutoStorageBasePropertiesArgs
        {
            StorageAccountId = "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
        },
        Location = "japaneast",
        ResourceGroupName = "default-azurebatch-japaneast",
    });

});


```

```go
package main

import (
	batch "github.com/pulumi/pulumi-azure-native-sdk/batch"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := batch.NewBatchAccount(ctx, "batchAccount", &batch.BatchAccountArgs{
			AccountName: pulumi.String("sampleacct"),
			AutoStorage: &batch.AutoStorageBasePropertiesArgs{
				StorageAccountId: pulumi.String("/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage"),
			},
			Location:          pulumi.String("japaneast"),
			ResourceGroupName: pulumi.String("default-azurebatch-japaneast"),
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
import com.pulumi.azurenative.batch.BatchAccount;
import com.pulumi.azurenative.batch.BatchAccountArgs;
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
        var batchAccount = new BatchAccount("batchAccount", BatchAccountArgs.builder()        
            .accountName("sampleacct")
            .autoStorage(Map.of("storageAccountId", "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage"))
            .location("japaneast")
            .resourceGroupName("default-azurebatch-japaneast")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const batchAccount = new azure_native.batch.BatchAccount("batchAccount", {
    accountName: "sampleacct",
    autoStorage: {
        storageAccountId: "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
    },
    location: "japaneast",
    resourceGroupName: "default-azurebatch-japaneast",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

batch_account = azure_native.batch.BatchAccount("batchAccount",
    account_name="sampleacct",
    auto_storage=azure_native.batch.AutoStorageBasePropertiesArgs(
        storage_account_id="/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
    ),
    location="japaneast",
    resource_group_name="default-azurebatch-japaneast")

```

```yaml
resources:
  batchAccount:
    type: azure-native:batch:BatchAccount
    properties:
      accountName: sampleacct
      autoStorage:
        storageAccountId: /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage
      location: japaneast
      resourceGroupName: default-azurebatch-japaneast

```

{{% /example %}}
{{% example %}}
### BatchAccountCreate_SystemAssignedIdentity
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var batchAccount = new AzureNative.Batch.BatchAccount("batchAccount", new()
    {
        AccountName = "sampleacct",
        AutoStorage = new AzureNative.Batch.Inputs.AutoStorageBasePropertiesArgs
        {
            StorageAccountId = "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
        },
        Identity = new AzureNative.Batch.Inputs.BatchAccountIdentityArgs
        {
            Type = AzureNative.Batch.ResourceIdentityType.SystemAssigned,
        },
        Location = "japaneast",
        ResourceGroupName = "default-azurebatch-japaneast",
    });

});


```

```go
package main

import (
	batch "github.com/pulumi/pulumi-azure-native-sdk/batch"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := batch.NewBatchAccount(ctx, "batchAccount", &batch.BatchAccountArgs{
			AccountName: pulumi.String("sampleacct"),
			AutoStorage: &batch.AutoStorageBasePropertiesArgs{
				StorageAccountId: pulumi.String("/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage"),
			},
			Identity: &batch.BatchAccountIdentityArgs{
				Type: batch.ResourceIdentityTypeSystemAssigned,
			},
			Location:          pulumi.String("japaneast"),
			ResourceGroupName: pulumi.String("default-azurebatch-japaneast"),
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
import com.pulumi.azurenative.batch.BatchAccount;
import com.pulumi.azurenative.batch.BatchAccountArgs;
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
        var batchAccount = new BatchAccount("batchAccount", BatchAccountArgs.builder()        
            .accountName("sampleacct")
            .autoStorage(Map.of("storageAccountId", "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage"))
            .identity(Map.of("type", "SystemAssigned"))
            .location("japaneast")
            .resourceGroupName("default-azurebatch-japaneast")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const batchAccount = new azure_native.batch.BatchAccount("batchAccount", {
    accountName: "sampleacct",
    autoStorage: {
        storageAccountId: "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
    },
    identity: {
        type: azure_native.batch.ResourceIdentityType.SystemAssigned,
    },
    location: "japaneast",
    resourceGroupName: "default-azurebatch-japaneast",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

batch_account = azure_native.batch.BatchAccount("batchAccount",
    account_name="sampleacct",
    auto_storage=azure_native.batch.AutoStorageBasePropertiesArgs(
        storage_account_id="/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
    ),
    identity=azure_native.batch.BatchAccountIdentityArgs(
        type=azure_native.batch.ResourceIdentityType.SYSTEM_ASSIGNED,
    ),
    location="japaneast",
    resource_group_name="default-azurebatch-japaneast")

```

```yaml
resources:
  batchAccount:
    type: azure-native:batch:BatchAccount
    properties:
      accountName: sampleacct
      autoStorage:
        storageAccountId: /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage
      identity:
        type: SystemAssigned
      location: japaneast
      resourceGroupName: default-azurebatch-japaneast

```

{{% /example %}}
{{% example %}}
### PrivateBatchAccountCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var batchAccount = new AzureNative.Batch.BatchAccount("batchAccount", new()
    {
        AccountName = "sampleacct",
        AutoStorage = new AzureNative.Batch.Inputs.AutoStorageBasePropertiesArgs
        {
            StorageAccountId = "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
        },
        KeyVaultReference = new AzureNative.Batch.Inputs.KeyVaultReferenceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample",
            Url = "http://sample.vault.azure.net/",
        },
        Location = "japaneast",
        PublicNetworkAccess = AzureNative.Batch.PublicNetworkAccessType.Disabled,
        ResourceGroupName = "default-azurebatch-japaneast",
    });

});


```

```go
package main

import (
	batch "github.com/pulumi/pulumi-azure-native-sdk/batch"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := batch.NewBatchAccount(ctx, "batchAccount", &batch.BatchAccountArgs{
			AccountName: pulumi.String("sampleacct"),
			AutoStorage: &batch.AutoStorageBasePropertiesArgs{
				StorageAccountId: pulumi.String("/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage"),
			},
			KeyVaultReference: &batch.KeyVaultReferenceArgs{
				Id:  pulumi.String("/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample"),
				Url: pulumi.String("http://sample.vault.azure.net/"),
			},
			Location:            pulumi.String("japaneast"),
			PublicNetworkAccess: batch.PublicNetworkAccessTypeDisabled,
			ResourceGroupName:   pulumi.String("default-azurebatch-japaneast"),
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
import com.pulumi.azurenative.batch.BatchAccount;
import com.pulumi.azurenative.batch.BatchAccountArgs;
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
        var batchAccount = new BatchAccount("batchAccount", BatchAccountArgs.builder()        
            .accountName("sampleacct")
            .autoStorage(Map.of("storageAccountId", "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage"))
            .keyVaultReference(Map.ofEntries(
                Map.entry("id", "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample"),
                Map.entry("url", "http://sample.vault.azure.net/")
            ))
            .location("japaneast")
            .publicNetworkAccess("Disabled")
            .resourceGroupName("default-azurebatch-japaneast")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const batchAccount = new azure_native.batch.BatchAccount("batchAccount", {
    accountName: "sampleacct",
    autoStorage: {
        storageAccountId: "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
    },
    keyVaultReference: {
        id: "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample",
        url: "http://sample.vault.azure.net/",
    },
    location: "japaneast",
    publicNetworkAccess: azure_native.batch.PublicNetworkAccessType.Disabled,
    resourceGroupName: "default-azurebatch-japaneast",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

batch_account = azure_native.batch.BatchAccount("batchAccount",
    account_name="sampleacct",
    auto_storage=azure_native.batch.AutoStorageBasePropertiesArgs(
        storage_account_id="/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage",
    ),
    key_vault_reference=azure_native.batch.KeyVaultReferenceArgs(
        id="/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample",
        url="http://sample.vault.azure.net/",
    ),
    location="japaneast",
    public_network_access=azure_native.batch.PublicNetworkAccessType.DISABLED,
    resource_group_name="default-azurebatch-japaneast")

```

```yaml
resources:
  batchAccount:
    type: azure-native:batch:BatchAccount
    properties:
      accountName: sampleacct
      autoStorage:
        storageAccountId: /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Storage/storageAccounts/samplestorage
      keyVaultReference:
        id: /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.KeyVault/vaults/sample
        url: http://sample.vault.azure.net/
      location: japaneast
      publicNetworkAccess: Disabled
      resourceGroupName: default-azurebatch-japaneast

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:batch:BatchAccount sampleacct /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct 
```
