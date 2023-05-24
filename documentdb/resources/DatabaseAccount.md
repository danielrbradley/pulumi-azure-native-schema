An Azure Cosmos DB database account.
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBDatabaseAccountCreateMin
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var databaseAccount = new AzureNative.DocumentDB.DatabaseAccount("databaseAccount", new()
    {
        AccountName = "ddb1",
        CreateMode = "Default",
        DatabaseAccountOfferType = AzureNative.DocumentDB.DatabaseAccountOfferType.Standard,
        Location = "westus",
        Locations = new[]
        {
            new AzureNative.DocumentDB.Inputs.LocationArgs
            {
                FailoverPriority = 0,
                IsZoneRedundant = false,
                LocationName = "southcentralus",
            },
        },
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	documentdb "github.com/pulumi/pulumi-azure-native-sdk/documentdb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := documentdb.NewDatabaseAccount(ctx, "databaseAccount", &documentdb.DatabaseAccountArgs{
			AccountName:              pulumi.String("ddb1"),
			CreateMode:               pulumi.String("Default"),
			DatabaseAccountOfferType: documentdb.DatabaseAccountOfferTypeStandard,
			Location:                 pulumi.String("westus"),
			Locations: []documentdb.LocationArgs{
				{
					FailoverPriority: pulumi.Int(0),
					IsZoneRedundant:  pulumi.Bool(false),
					LocationName:     pulumi.String("southcentralus"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.documentdb.DatabaseAccount;
import com.pulumi.azurenative.documentdb.DatabaseAccountArgs;
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
        var databaseAccount = new DatabaseAccount("databaseAccount", DatabaseAccountArgs.builder()        
            .accountName("ddb1")
            .createMode("Default")
            .databaseAccountOfferType("Standard")
            .location("westus")
            .locations(Map.ofEntries(
                Map.entry("failoverPriority", 0),
                Map.entry("isZoneRedundant", false),
                Map.entry("locationName", "southcentralus")
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const databaseAccount = new azure_native.documentdb.DatabaseAccount("databaseAccount", {
    accountName: "ddb1",
    createMode: "Default",
    databaseAccountOfferType: azure_native.documentdb.DatabaseAccountOfferType.Standard,
    location: "westus",
    locations: [{
        failoverPriority: 0,
        isZoneRedundant: false,
        locationName: "southcentralus",
    }],
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database_account = azure_native.documentdb.DatabaseAccount("databaseAccount",
    account_name="ddb1",
    create_mode="Default",
    database_account_offer_type=azure_native.documentdb.DatabaseAccountOfferType.STANDARD,
    location="westus",
    locations=[azure_native.documentdb.LocationArgs(
        failover_priority=0,
        is_zone_redundant=False,
        location_name="southcentralus",
    )],
    resource_group_name="rg1")

```

```yaml
resources:
  databaseAccount:
    type: azure-native:documentdb:DatabaseAccount
    properties:
      accountName: ddb1
      createMode: Default
      databaseAccountOfferType: Standard
      location: westus
      locations:
        - failoverPriority: 0
          isZoneRedundant: false
          locationName: southcentralus
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### CosmosDBRestoreDatabaseAccountCreateUpdate.json
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var databaseAccount = new AzureNative.DocumentDB.DatabaseAccount("databaseAccount", new()
    {
        AccountName = "ddb1",
        ApiProperties = new AzureNative.DocumentDB.Inputs.ApiPropertiesArgs
        {
            ServerVersion = "3.2",
        },
        BackupPolicy = new AzureNative.DocumentDB.Inputs.ContinuousModeBackupPolicyArgs
        {
            Type = "Continuous",
        },
        ConsistencyPolicy = new AzureNative.DocumentDB.Inputs.ConsistencyPolicyArgs
        {
            DefaultConsistencyLevel = AzureNative.DocumentDB.DefaultConsistencyLevel.BoundedStaleness,
            MaxIntervalInSeconds = 10,
            MaxStalenessPrefix = 200,
        },
        CreateMode = "Restore",
        DatabaseAccountOfferType = AzureNative.DocumentDB.DatabaseAccountOfferType.Standard,
        EnableAnalyticalStorage = true,
        EnableFreeTier = false,
        KeyVaultKeyUri = "https://myKeyVault.vault.azure.net",
        Kind = "GlobalDocumentDB",
        Location = "westus",
        Locations = new[]
        {
            new AzureNative.DocumentDB.Inputs.LocationArgs
            {
                FailoverPriority = 0,
                IsZoneRedundant = false,
                LocationName = "southcentralus",
            },
        },
        MinimalTlsVersion = "Tls",
        ResourceGroupName = "rg1",
        RestoreParameters = new AzureNative.DocumentDB.Inputs.RestoreParametersArgs
        {
            DatabasesToRestore = new[]
            {
                new AzureNative.DocumentDB.Inputs.DatabaseRestoreResourceArgs
                {
                    CollectionNames = new[]
                    {
                        "collection1",
                        "collection2",
                    },
                    DatabaseName = "db1",
                },
                new AzureNative.DocumentDB.Inputs.DatabaseRestoreResourceArgs
                {
                    CollectionNames = new[]
                    {
                        "collection3",
                        "collection4",
                    },
                    DatabaseName = "db2",
                },
            },
            RestoreMode = "PointInTime",
            RestoreSource = "/subscriptions/subid/providers/Microsoft.DocumentDB/locations/westus/restorableDatabaseAccounts/1a97b4bb-f6a0-430e-ade1-638d781830cc",
            RestoreTimestampInUtc = "2021-03-11T22:05:09Z",
        },
        Tags = null,
    });

});


```

```go
package main

import (
	documentdb "github.com/pulumi/pulumi-azure-native-sdk/documentdb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := documentdb.NewDatabaseAccount(ctx, "databaseAccount", &documentdb.DatabaseAccountArgs{
			AccountName: pulumi.String("ddb1"),
			ApiProperties: &documentdb.ApiPropertiesArgs{
				ServerVersion: pulumi.String("3.2"),
			},
			BackupPolicy: documentdb.ContinuousModeBackupPolicy{
				Type: "Continuous",
			},
			ConsistencyPolicy: &documentdb.ConsistencyPolicyArgs{
				DefaultConsistencyLevel: documentdb.DefaultConsistencyLevelBoundedStaleness,
				MaxIntervalInSeconds:    pulumi.Int(10),
				MaxStalenessPrefix:      pulumi.Float64(200),
			},
			CreateMode:               pulumi.String("Restore"),
			DatabaseAccountOfferType: documentdb.DatabaseAccountOfferTypeStandard,
			EnableAnalyticalStorage:  pulumi.Bool(true),
			EnableFreeTier:           pulumi.Bool(false),
			KeyVaultKeyUri:           pulumi.String("https://myKeyVault.vault.azure.net"),
			Kind:                     pulumi.String("GlobalDocumentDB"),
			Location:                 pulumi.String("westus"),
			Locations: []documentdb.LocationArgs{
				{
					FailoverPriority: pulumi.Int(0),
					IsZoneRedundant:  pulumi.Bool(false),
					LocationName:     pulumi.String("southcentralus"),
				},
			},
			MinimalTlsVersion: pulumi.String("Tls"),
			ResourceGroupName: pulumi.String("rg1"),
			RestoreParameters: documentdb.RestoreParametersResponse{
				DatabasesToRestore: documentdb.DatabaseRestoreResourceArray{
					&documentdb.DatabaseRestoreResourceArgs{
						CollectionNames: pulumi.StringArray{
							pulumi.String("collection1"),
							pulumi.String("collection2"),
						},
						DatabaseName: pulumi.String("db1"),
					},
					&documentdb.DatabaseRestoreResourceArgs{
						CollectionNames: pulumi.StringArray{
							pulumi.String("collection3"),
							pulumi.String("collection4"),
						},
						DatabaseName: pulumi.String("db2"),
					},
				},
				RestoreMode:           pulumi.String("PointInTime"),
				RestoreSource:         pulumi.String("/subscriptions/subid/providers/Microsoft.DocumentDB/locations/westus/restorableDatabaseAccounts/1a97b4bb-f6a0-430e-ade1-638d781830cc"),
				RestoreTimestampInUtc: pulumi.String("2021-03-11T22:05:09Z"),
			},
			Tags: nil,
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
import com.pulumi.azurenative.documentdb.DatabaseAccount;
import com.pulumi.azurenative.documentdb.DatabaseAccountArgs;
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
        var databaseAccount = new DatabaseAccount("databaseAccount", DatabaseAccountArgs.builder()        
            .accountName("ddb1")
            .apiProperties(Map.of("serverVersion", "3.2"))
            .backupPolicy(Map.of("type", "Continuous"))
            .consistencyPolicy(Map.ofEntries(
                Map.entry("defaultConsistencyLevel", "BoundedStaleness"),
                Map.entry("maxIntervalInSeconds", 10),
                Map.entry("maxStalenessPrefix", 200)
            ))
            .createMode("Restore")
            .databaseAccountOfferType("Standard")
            .enableAnalyticalStorage(true)
            .enableFreeTier(false)
            .keyVaultKeyUri("https://myKeyVault.vault.azure.net")
            .kind("GlobalDocumentDB")
            .location("westus")
            .locations(Map.ofEntries(
                Map.entry("failoverPriority", 0),
                Map.entry("isZoneRedundant", false),
                Map.entry("locationName", "southcentralus")
            ))
            .minimalTlsVersion("Tls")
            .resourceGroupName("rg1")
            .restoreParameters(Map.ofEntries(
                Map.entry("databasesToRestore",                 
                    Map.ofEntries(
                        Map.entry("collectionNames",                         
                            "collection1",
                            "collection2"),
                        Map.entry("databaseName", "db1")
                    ),
                    Map.ofEntries(
                        Map.entry("collectionNames",                         
                            "collection3",
                            "collection4"),
                        Map.entry("databaseName", "db2")
                    )),
                Map.entry("restoreMode", "PointInTime"),
                Map.entry("restoreSource", "/subscriptions/subid/providers/Microsoft.DocumentDB/locations/westus/restorableDatabaseAccounts/1a97b4bb-f6a0-430e-ade1-638d781830cc"),
                Map.entry("restoreTimestampInUtc", "2021-03-11T22:05:09Z")
            ))
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const databaseAccount = new azure_native.documentdb.DatabaseAccount("databaseAccount", {
    accountName: "ddb1",
    apiProperties: {
        serverVersion: "3.2",
    },
    backupPolicy: {
        type: "Continuous",
    },
    consistencyPolicy: {
        defaultConsistencyLevel: azure_native.documentdb.DefaultConsistencyLevel.BoundedStaleness,
        maxIntervalInSeconds: 10,
        maxStalenessPrefix: 200,
    },
    createMode: "Restore",
    databaseAccountOfferType: azure_native.documentdb.DatabaseAccountOfferType.Standard,
    enableAnalyticalStorage: true,
    enableFreeTier: false,
    keyVaultKeyUri: "https://myKeyVault.vault.azure.net",
    kind: "GlobalDocumentDB",
    location: "westus",
    locations: [{
        failoverPriority: 0,
        isZoneRedundant: false,
        locationName: "southcentralus",
    }],
    minimalTlsVersion: "Tls",
    resourceGroupName: "rg1",
    restoreParameters: {
        databasesToRestore: [
            {
                collectionNames: [
                    "collection1",
                    "collection2",
                ],
                databaseName: "db1",
            },
            {
                collectionNames: [
                    "collection3",
                    "collection4",
                ],
                databaseName: "db2",
            },
        ],
        restoreMode: "PointInTime",
        restoreSource: "/subscriptions/subid/providers/Microsoft.DocumentDB/locations/westus/restorableDatabaseAccounts/1a97b4bb-f6a0-430e-ade1-638d781830cc",
        restoreTimestampInUtc: "2021-03-11T22:05:09Z",
    },
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database_account = azure_native.documentdb.DatabaseAccount("databaseAccount",
    account_name="ddb1",
    api_properties=azure_native.documentdb.ApiPropertiesArgs(
        server_version="3.2",
    ),
    backup_policy=azure_native.documentdb.ContinuousModeBackupPolicyArgs(
        type="Continuous",
    ),
    consistency_policy=azure_native.documentdb.ConsistencyPolicyArgs(
        default_consistency_level=azure_native.documentdb.DefaultConsistencyLevel.BOUNDED_STALENESS,
        max_interval_in_seconds=10,
        max_staleness_prefix=200,
    ),
    create_mode="Restore",
    database_account_offer_type=azure_native.documentdb.DatabaseAccountOfferType.STANDARD,
    enable_analytical_storage=True,
    enable_free_tier=False,
    key_vault_key_uri="https://myKeyVault.vault.azure.net",
    kind="GlobalDocumentDB",
    location="westus",
    locations=[azure_native.documentdb.LocationArgs(
        failover_priority=0,
        is_zone_redundant=False,
        location_name="southcentralus",
    )],
    minimal_tls_version="Tls",
    resource_group_name="rg1",
    restore_parameters=azure_native.documentdb.RestoreParametersResponseArgs(
        databases_to_restore=[
            azure_native.documentdb.DatabaseRestoreResourceArgs(
                collection_names=[
                    "collection1",
                    "collection2",
                ],
                database_name="db1",
            ),
            azure_native.documentdb.DatabaseRestoreResourceArgs(
                collection_names=[
                    "collection3",
                    "collection4",
                ],
                database_name="db2",
            ),
        ],
        restore_mode="PointInTime",
        restore_source="/subscriptions/subid/providers/Microsoft.DocumentDB/locations/westus/restorableDatabaseAccounts/1a97b4bb-f6a0-430e-ade1-638d781830cc",
        restore_timestamp_in_utc="2021-03-11T22:05:09Z",
    ),
    tags={})

```

```yaml
resources:
  databaseAccount:
    type: azure-native:documentdb:DatabaseAccount
    properties:
      accountName: ddb1
      apiProperties:
        serverVersion: '3.2'
      backupPolicy:
        type: Continuous
      consistencyPolicy:
        defaultConsistencyLevel: BoundedStaleness
        maxIntervalInSeconds: 10
        maxStalenessPrefix: 200
      createMode: Restore
      databaseAccountOfferType: Standard
      enableAnalyticalStorage: true
      enableFreeTier: false
      keyVaultKeyUri: https://myKeyVault.vault.azure.net
      kind: GlobalDocumentDB
      location: westus
      locations:
        - failoverPriority: 0
          isZoneRedundant: false
          locationName: southcentralus
      minimalTlsVersion: Tls
      resourceGroupName: rg1
      restoreParameters:
        databasesToRestore:
          - collectionNames:
              - collection1
              - collection2
            databaseName: db1
          - collectionNames:
              - collection3
              - collection4
            databaseName: db2
        restoreMode: PointInTime
        restoreSource: /subscriptions/subid/providers/Microsoft.DocumentDB/locations/westus/restorableDatabaseAccounts/1a97b4bb-f6a0-430e-ade1-638d781830cc
        restoreTimestampInUtc: 2021-03-11T22:05:09Z
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:DatabaseAccount ddb1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1 
```
