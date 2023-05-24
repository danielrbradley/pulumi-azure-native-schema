The storage account blob inventory policy.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StorageAccountSetBlobInventoryPolicy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blobInventoryPolicy = new AzureNative.Storage.BlobInventoryPolicy("blobInventoryPolicy", new()
    {
        AccountName = "sto9699",
        BlobInventoryPolicyName = "default",
        Policy = new AzureNative.Storage.Inputs.BlobInventoryPolicySchemaArgs
        {
            Enabled = true,
            Rules = new[]
            {
                new AzureNative.Storage.Inputs.BlobInventoryPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.BlobInventoryPolicyDefinitionArgs
                    {
                        Filters = new AzureNative.Storage.Inputs.BlobInventoryPolicyFilterArgs
                        {
                            BlobTypes = new[]
                            {
                                "blockBlob",
                                "appendBlob",
                                "pageBlob",
                            },
                            ExcludePrefix = new[]
                            {
                                "excludeprefix1",
                                "excludeprefix2",
                            },
                            IncludeBlobVersions = true,
                            IncludeSnapshots = true,
                            PrefixMatch = new[]
                            {
                                "inventoryprefix1",
                                "inventoryprefix2",
                            },
                        },
                        Format = "Csv",
                        ObjectType = "Blob",
                        Schedule = "Daily",
                        SchemaFields = new[]
                        {
                            "Name",
                            "Creation-Time",
                            "Last-Modified",
                            "Content-Length",
                            "Content-MD5",
                            "BlobType",
                            "AccessTier",
                            "AccessTierChangeTime",
                            "Snapshot",
                            "VersionId",
                            "IsCurrentVersion",
                            "Metadata",
                        },
                    },
                    Destination = "container1",
                    Enabled = true,
                    Name = "inventoryPolicyRule1",
                },
                new AzureNative.Storage.Inputs.BlobInventoryPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.BlobInventoryPolicyDefinitionArgs
                    {
                        Format = "Parquet",
                        ObjectType = "Container",
                        Schedule = "Weekly",
                        SchemaFields = new[]
                        {
                            "Name",
                            "Last-Modified",
                            "Metadata",
                            "LeaseStatus",
                            "LeaseState",
                            "LeaseDuration",
                            "PublicAccess",
                            "HasImmutabilityPolicy",
                            "HasLegalHold",
                        },
                    },
                    Destination = "container2",
                    Enabled = true,
                    Name = "inventoryPolicyRule2",
                },
            },
            Type = "Inventory",
        },
        ResourceGroupName = "res7687",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storage.BlobInventoryPolicy;
import com.pulumi.azurenative.storage.BlobInventoryPolicyArgs;
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
        var blobInventoryPolicy = new BlobInventoryPolicy("blobInventoryPolicy", BlobInventoryPolicyArgs.builder()        
            .accountName("sto9699")
            .blobInventoryPolicyName("default")
            .policy(Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("definition", Map.ofEntries(
                            Map.entry("filters", Map.ofEntries(
                                Map.entry("blobTypes",                                 
                                    "blockBlob",
                                    "appendBlob",
                                    "pageBlob"),
                                Map.entry("excludePrefix",                                 
                                    "excludeprefix1",
                                    "excludeprefix2"),
                                Map.entry("includeBlobVersions", true),
                                Map.entry("includeSnapshots", true),
                                Map.entry("prefixMatch",                                 
                                    "inventoryprefix1",
                                    "inventoryprefix2")
                            )),
                            Map.entry("format", "Csv"),
                            Map.entry("objectType", "Blob"),
                            Map.entry("schedule", "Daily"),
                            Map.entry("schemaFields",                             
                                "Name",
                                "Creation-Time",
                                "Last-Modified",
                                "Content-Length",
                                "Content-MD5",
                                "BlobType",
                                "AccessTier",
                                "AccessTierChangeTime",
                                "Snapshot",
                                "VersionId",
                                "IsCurrentVersion",
                                "Metadata")
                        )),
                        Map.entry("destination", "container1"),
                        Map.entry("enabled", true),
                        Map.entry("name", "inventoryPolicyRule1")
                    ),
                    Map.ofEntries(
                        Map.entry("definition", Map.ofEntries(
                            Map.entry("format", "Parquet"),
                            Map.entry("objectType", "Container"),
                            Map.entry("schedule", "Weekly"),
                            Map.entry("schemaFields",                             
                                "Name",
                                "Last-Modified",
                                "Metadata",
                                "LeaseStatus",
                                "LeaseState",
                                "LeaseDuration",
                                "PublicAccess",
                                "HasImmutabilityPolicy",
                                "HasLegalHold")
                        )),
                        Map.entry("destination", "container2"),
                        Map.entry("enabled", true),
                        Map.entry("name", "inventoryPolicyRule2")
                    )),
                Map.entry("type", "Inventory")
            ))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blobInventoryPolicy = new azure_native.storage.BlobInventoryPolicy("blobInventoryPolicy", {
    accountName: "sto9699",
    blobInventoryPolicyName: "default",
    policy: {
        enabled: true,
        rules: [
            {
                definition: {
                    filters: {
                        blobTypes: [
                            "blockBlob",
                            "appendBlob",
                            "pageBlob",
                        ],
                        excludePrefix: [
                            "excludeprefix1",
                            "excludeprefix2",
                        ],
                        includeBlobVersions: true,
                        includeSnapshots: true,
                        prefixMatch: [
                            "inventoryprefix1",
                            "inventoryprefix2",
                        ],
                    },
                    format: "Csv",
                    objectType: "Blob",
                    schedule: "Daily",
                    schemaFields: [
                        "Name",
                        "Creation-Time",
                        "Last-Modified",
                        "Content-Length",
                        "Content-MD5",
                        "BlobType",
                        "AccessTier",
                        "AccessTierChangeTime",
                        "Snapshot",
                        "VersionId",
                        "IsCurrentVersion",
                        "Metadata",
                    ],
                },
                destination: "container1",
                enabled: true,
                name: "inventoryPolicyRule1",
            },
            {
                definition: {
                    format: "Parquet",
                    objectType: "Container",
                    schedule: "Weekly",
                    schemaFields: [
                        "Name",
                        "Last-Modified",
                        "Metadata",
                        "LeaseStatus",
                        "LeaseState",
                        "LeaseDuration",
                        "PublicAccess",
                        "HasImmutabilityPolicy",
                        "HasLegalHold",
                    ],
                },
                destination: "container2",
                enabled: true,
                name: "inventoryPolicyRule2",
            },
        ],
        type: "Inventory",
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blob_inventory_policy = azure_native.storage.BlobInventoryPolicy("blobInventoryPolicy",
    account_name="sto9699",
    blob_inventory_policy_name="default",
    policy=azure_native.storage.BlobInventoryPolicySchemaResponseArgs(
        enabled=True,
        rules=[
            {
                "definition": {
                    "filters": azure_native.storage.BlobInventoryPolicyFilterArgs(
                        blob_types=[
                            "blockBlob",
                            "appendBlob",
                            "pageBlob",
                        ],
                        exclude_prefix=[
                            "excludeprefix1",
                            "excludeprefix2",
                        ],
                        include_blob_versions=True,
                        include_snapshots=True,
                        prefix_match=[
                            "inventoryprefix1",
                            "inventoryprefix2",
                        ],
                    ),
                    "format": "Csv",
                    "objectType": "Blob",
                    "schedule": "Daily",
                    "schemaFields": [
                        "Name",
                        "Creation-Time",
                        "Last-Modified",
                        "Content-Length",
                        "Content-MD5",
                        "BlobType",
                        "AccessTier",
                        "AccessTierChangeTime",
                        "Snapshot",
                        "VersionId",
                        "IsCurrentVersion",
                        "Metadata",
                    ],
                },
                "destination": "container1",
                "enabled": True,
                "name": "inventoryPolicyRule1",
            },
            {
                "definition": azure_native.storage.BlobInventoryPolicyDefinitionArgs(
                    format="Parquet",
                    object_type="Container",
                    schedule="Weekly",
                    schema_fields=[
                        "Name",
                        "Last-Modified",
                        "Metadata",
                        "LeaseStatus",
                        "LeaseState",
                        "LeaseDuration",
                        "PublicAccess",
                        "HasImmutabilityPolicy",
                        "HasLegalHold",
                    ],
                ),
                "destination": "container2",
                "enabled": True,
                "name": "inventoryPolicyRule2",
            },
        ],
        type="Inventory",
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  blobInventoryPolicy:
    type: azure-native:storage:BlobInventoryPolicy
    properties:
      accountName: sto9699
      blobInventoryPolicyName: default
      policy:
        enabled: true
        rules:
          - definition:
              filters:
                blobTypes:
                  - blockBlob
                  - appendBlob
                  - pageBlob
                excludePrefix:
                  - excludeprefix1
                  - excludeprefix2
                includeBlobVersions: true
                includeSnapshots: true
                prefixMatch:
                  - inventoryprefix1
                  - inventoryprefix2
              format: Csv
              objectType: Blob
              schedule: Daily
              schemaFields:
                - Name
                - Creation-Time
                - Last-Modified
                - Content-Length
                - Content-MD5
                - BlobType
                - AccessTier
                - AccessTierChangeTime
                - Snapshot
                - VersionId
                - IsCurrentVersion
                - Metadata
            destination: container1
            enabled: true
            name: inventoryPolicyRule1
          - definition:
              format: Parquet
              objectType: Container
              schedule: Weekly
              schemaFields:
                - Name
                - Last-Modified
                - Metadata
                - LeaseStatus
                - LeaseState
                - LeaseDuration
                - PublicAccess
                - HasImmutabilityPolicy
                - HasLegalHold
            destination: container2
            enabled: true
            name: inventoryPolicyRule2
        type: Inventory
      resourceGroupName: res7687

```

{{% /example %}}
{{% example %}}
### StorageAccountSetBlobInventoryPolicyIncludeDeleteAndNewSchemaForHnsAccount
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blobInventoryPolicy = new AzureNative.Storage.BlobInventoryPolicy("blobInventoryPolicy", new()
    {
        AccountName = "sto9699",
        BlobInventoryPolicyName = "default",
        Policy = new AzureNative.Storage.Inputs.BlobInventoryPolicySchemaArgs
        {
            Enabled = true,
            Rules = new[]
            {
                new AzureNative.Storage.Inputs.BlobInventoryPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.BlobInventoryPolicyDefinitionArgs
                    {
                        Filters = new AzureNative.Storage.Inputs.BlobInventoryPolicyFilterArgs
                        {
                            BlobTypes = new[]
                            {
                                "blockBlob",
                                "appendBlob",
                                "pageBlob",
                            },
                            ExcludePrefix = new[]
                            {
                                "excludeprefix1",
                                "excludeprefix2",
                            },
                            IncludeBlobVersions = true,
                            IncludeDeleted = true,
                            IncludeSnapshots = true,
                            PrefixMatch = new[]
                            {
                                "inventoryprefix1",
                                "inventoryprefix2",
                            },
                        },
                        Format = "Csv",
                        ObjectType = "Blob",
                        Schedule = "Daily",
                        SchemaFields = new[]
                        {
                            "Name",
                            "Creation-Time",
                            "Last-Modified",
                            "Content-Length",
                            "Content-MD5",
                            "BlobType",
                            "AccessTier",
                            "AccessTierChangeTime",
                            "Snapshot",
                            "VersionId",
                            "IsCurrentVersion",
                            "ContentType",
                            "ContentEncoding",
                            "ContentLanguage",
                            "ContentCRC64",
                            "CacheControl",
                            "Metadata",
                            "DeletionId",
                            "Deleted",
                            "DeletedTime",
                            "RemainingRetentionDays",
                        },
                    },
                    Destination = "container1",
                    Enabled = true,
                    Name = "inventoryPolicyRule1",
                },
                new AzureNative.Storage.Inputs.BlobInventoryPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.BlobInventoryPolicyDefinitionArgs
                    {
                        Format = "Parquet",
                        ObjectType = "Container",
                        Schedule = "Weekly",
                        SchemaFields = new[]
                        {
                            "Name",
                            "Last-Modified",
                            "Metadata",
                            "LeaseStatus",
                            "LeaseState",
                            "LeaseDuration",
                            "PublicAccess",
                            "HasImmutabilityPolicy",
                            "HasLegalHold",
                            "Etag",
                            "DefaultEncryptionScope",
                            "DenyEncryptionScopeOverride",
                            "ImmutableStorageWithVersioningEnabled",
                            "Deleted",
                            "Version",
                            "DeletedTime",
                            "RemainingRetentionDays",
                        },
                    },
                    Destination = "container2",
                    Enabled = true,
                    Name = "inventoryPolicyRule2",
                },
            },
            Type = "Inventory",
        },
        ResourceGroupName = "res7687",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storage.BlobInventoryPolicy;
import com.pulumi.azurenative.storage.BlobInventoryPolicyArgs;
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
        var blobInventoryPolicy = new BlobInventoryPolicy("blobInventoryPolicy", BlobInventoryPolicyArgs.builder()        
            .accountName("sto9699")
            .blobInventoryPolicyName("default")
            .policy(Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("definition", Map.ofEntries(
                            Map.entry("filters", Map.ofEntries(
                                Map.entry("blobTypes",                                 
                                    "blockBlob",
                                    "appendBlob",
                                    "pageBlob"),
                                Map.entry("excludePrefix",                                 
                                    "excludeprefix1",
                                    "excludeprefix2"),
                                Map.entry("includeBlobVersions", true),
                                Map.entry("includeDeleted", true),
                                Map.entry("includeSnapshots", true),
                                Map.entry("prefixMatch",                                 
                                    "inventoryprefix1",
                                    "inventoryprefix2")
                            )),
                            Map.entry("format", "Csv"),
                            Map.entry("objectType", "Blob"),
                            Map.entry("schedule", "Daily"),
                            Map.entry("schemaFields",                             
                                "Name",
                                "Creation-Time",
                                "Last-Modified",
                                "Content-Length",
                                "Content-MD5",
                                "BlobType",
                                "AccessTier",
                                "AccessTierChangeTime",
                                "Snapshot",
                                "VersionId",
                                "IsCurrentVersion",
                                "ContentType",
                                "ContentEncoding",
                                "ContentLanguage",
                                "ContentCRC64",
                                "CacheControl",
                                "Metadata",
                                "DeletionId",
                                "Deleted",
                                "DeletedTime",
                                "RemainingRetentionDays")
                        )),
                        Map.entry("destination", "container1"),
                        Map.entry("enabled", true),
                        Map.entry("name", "inventoryPolicyRule1")
                    ),
                    Map.ofEntries(
                        Map.entry("definition", Map.ofEntries(
                            Map.entry("format", "Parquet"),
                            Map.entry("objectType", "Container"),
                            Map.entry("schedule", "Weekly"),
                            Map.entry("schemaFields",                             
                                "Name",
                                "Last-Modified",
                                "Metadata",
                                "LeaseStatus",
                                "LeaseState",
                                "LeaseDuration",
                                "PublicAccess",
                                "HasImmutabilityPolicy",
                                "HasLegalHold",
                                "Etag",
                                "DefaultEncryptionScope",
                                "DenyEncryptionScopeOverride",
                                "ImmutableStorageWithVersioningEnabled",
                                "Deleted",
                                "Version",
                                "DeletedTime",
                                "RemainingRetentionDays")
                        )),
                        Map.entry("destination", "container2"),
                        Map.entry("enabled", true),
                        Map.entry("name", "inventoryPolicyRule2")
                    )),
                Map.entry("type", "Inventory")
            ))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blobInventoryPolicy = new azure_native.storage.BlobInventoryPolicy("blobInventoryPolicy", {
    accountName: "sto9699",
    blobInventoryPolicyName: "default",
    policy: {
        enabled: true,
        rules: [
            {
                definition: {
                    filters: {
                        blobTypes: [
                            "blockBlob",
                            "appendBlob",
                            "pageBlob",
                        ],
                        excludePrefix: [
                            "excludeprefix1",
                            "excludeprefix2",
                        ],
                        includeBlobVersions: true,
                        includeDeleted: true,
                        includeSnapshots: true,
                        prefixMatch: [
                            "inventoryprefix1",
                            "inventoryprefix2",
                        ],
                    },
                    format: "Csv",
                    objectType: "Blob",
                    schedule: "Daily",
                    schemaFields: [
                        "Name",
                        "Creation-Time",
                        "Last-Modified",
                        "Content-Length",
                        "Content-MD5",
                        "BlobType",
                        "AccessTier",
                        "AccessTierChangeTime",
                        "Snapshot",
                        "VersionId",
                        "IsCurrentVersion",
                        "ContentType",
                        "ContentEncoding",
                        "ContentLanguage",
                        "ContentCRC64",
                        "CacheControl",
                        "Metadata",
                        "DeletionId",
                        "Deleted",
                        "DeletedTime",
                        "RemainingRetentionDays",
                    ],
                },
                destination: "container1",
                enabled: true,
                name: "inventoryPolicyRule1",
            },
            {
                definition: {
                    format: "Parquet",
                    objectType: "Container",
                    schedule: "Weekly",
                    schemaFields: [
                        "Name",
                        "Last-Modified",
                        "Metadata",
                        "LeaseStatus",
                        "LeaseState",
                        "LeaseDuration",
                        "PublicAccess",
                        "HasImmutabilityPolicy",
                        "HasLegalHold",
                        "Etag",
                        "DefaultEncryptionScope",
                        "DenyEncryptionScopeOverride",
                        "ImmutableStorageWithVersioningEnabled",
                        "Deleted",
                        "Version",
                        "DeletedTime",
                        "RemainingRetentionDays",
                    ],
                },
                destination: "container2",
                enabled: true,
                name: "inventoryPolicyRule2",
            },
        ],
        type: "Inventory",
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blob_inventory_policy = azure_native.storage.BlobInventoryPolicy("blobInventoryPolicy",
    account_name="sto9699",
    blob_inventory_policy_name="default",
    policy=azure_native.storage.BlobInventoryPolicySchemaResponseArgs(
        enabled=True,
        rules=[
            {
                "definition": {
                    "filters": azure_native.storage.BlobInventoryPolicyFilterArgs(
                        blob_types=[
                            "blockBlob",
                            "appendBlob",
                            "pageBlob",
                        ],
                        exclude_prefix=[
                            "excludeprefix1",
                            "excludeprefix2",
                        ],
                        include_blob_versions=True,
                        include_deleted=True,
                        include_snapshots=True,
                        prefix_match=[
                            "inventoryprefix1",
                            "inventoryprefix2",
                        ],
                    ),
                    "format": "Csv",
                    "objectType": "Blob",
                    "schedule": "Daily",
                    "schemaFields": [
                        "Name",
                        "Creation-Time",
                        "Last-Modified",
                        "Content-Length",
                        "Content-MD5",
                        "BlobType",
                        "AccessTier",
                        "AccessTierChangeTime",
                        "Snapshot",
                        "VersionId",
                        "IsCurrentVersion",
                        "ContentType",
                        "ContentEncoding",
                        "ContentLanguage",
                        "ContentCRC64",
                        "CacheControl",
                        "Metadata",
                        "DeletionId",
                        "Deleted",
                        "DeletedTime",
                        "RemainingRetentionDays",
                    ],
                },
                "destination": "container1",
                "enabled": True,
                "name": "inventoryPolicyRule1",
            },
            {
                "definition": azure_native.storage.BlobInventoryPolicyDefinitionArgs(
                    format="Parquet",
                    object_type="Container",
                    schedule="Weekly",
                    schema_fields=[
                        "Name",
                        "Last-Modified",
                        "Metadata",
                        "LeaseStatus",
                        "LeaseState",
                        "LeaseDuration",
                        "PublicAccess",
                        "HasImmutabilityPolicy",
                        "HasLegalHold",
                        "Etag",
                        "DefaultEncryptionScope",
                        "DenyEncryptionScopeOverride",
                        "ImmutableStorageWithVersioningEnabled",
                        "Deleted",
                        "Version",
                        "DeletedTime",
                        "RemainingRetentionDays",
                    ],
                ),
                "destination": "container2",
                "enabled": True,
                "name": "inventoryPolicyRule2",
            },
        ],
        type="Inventory",
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  blobInventoryPolicy:
    type: azure-native:storage:BlobInventoryPolicy
    properties:
      accountName: sto9699
      blobInventoryPolicyName: default
      policy:
        enabled: true
        rules:
          - definition:
              filters:
                blobTypes:
                  - blockBlob
                  - appendBlob
                  - pageBlob
                excludePrefix:
                  - excludeprefix1
                  - excludeprefix2
                includeBlobVersions: true
                includeDeleted: true
                includeSnapshots: true
                prefixMatch:
                  - inventoryprefix1
                  - inventoryprefix2
              format: Csv
              objectType: Blob
              schedule: Daily
              schemaFields:
                - Name
                - Creation-Time
                - Last-Modified
                - Content-Length
                - Content-MD5
                - BlobType
                - AccessTier
                - AccessTierChangeTime
                - Snapshot
                - VersionId
                - IsCurrentVersion
                - ContentType
                - ContentEncoding
                - ContentLanguage
                - ContentCRC64
                - CacheControl
                - Metadata
                - DeletionId
                - Deleted
                - DeletedTime
                - RemainingRetentionDays
            destination: container1
            enabled: true
            name: inventoryPolicyRule1
          - definition:
              format: Parquet
              objectType: Container
              schedule: Weekly
              schemaFields:
                - Name
                - Last-Modified
                - Metadata
                - LeaseStatus
                - LeaseState
                - LeaseDuration
                - PublicAccess
                - HasImmutabilityPolicy
                - HasLegalHold
                - Etag
                - DefaultEncryptionScope
                - DenyEncryptionScopeOverride
                - ImmutableStorageWithVersioningEnabled
                - Deleted
                - Version
                - DeletedTime
                - RemainingRetentionDays
            destination: container2
            enabled: true
            name: inventoryPolicyRule2
        type: Inventory
      resourceGroupName: res7687

```

{{% /example %}}
{{% example %}}
### StorageAccountSetBlobInventoryPolicyIncludeDeleteAndNewSchemaForNonHnsAccount
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blobInventoryPolicy = new AzureNative.Storage.BlobInventoryPolicy("blobInventoryPolicy", new()
    {
        AccountName = "sto9699",
        BlobInventoryPolicyName = "default",
        Policy = new AzureNative.Storage.Inputs.BlobInventoryPolicySchemaArgs
        {
            Enabled = true,
            Rules = new[]
            {
                new AzureNative.Storage.Inputs.BlobInventoryPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.BlobInventoryPolicyDefinitionArgs
                    {
                        Filters = new AzureNative.Storage.Inputs.BlobInventoryPolicyFilterArgs
                        {
                            BlobTypes = new[]
                            {
                                "blockBlob",
                                "appendBlob",
                                "pageBlob",
                            },
                            ExcludePrefix = new[]
                            {
                                "excludeprefix1",
                                "excludeprefix2",
                            },
                            IncludeBlobVersions = true,
                            IncludeDeleted = true,
                            IncludeSnapshots = true,
                            PrefixMatch = new[]
                            {
                                "inventoryprefix1",
                                "inventoryprefix2",
                            },
                        },
                        Format = "Csv",
                        ObjectType = "Blob",
                        Schedule = "Daily",
                        SchemaFields = new[]
                        {
                            "Name",
                            "Creation-Time",
                            "Last-Modified",
                            "Content-Length",
                            "Content-MD5",
                            "BlobType",
                            "AccessTier",
                            "AccessTierChangeTime",
                            "Snapshot",
                            "VersionId",
                            "IsCurrentVersion",
                            "Tags",
                            "ContentType",
                            "ContentEncoding",
                            "ContentLanguage",
                            "ContentCRC64",
                            "CacheControl",
                            "Metadata",
                            "Deleted",
                            "RemainingRetentionDays",
                        },
                    },
                    Destination = "container1",
                    Enabled = true,
                    Name = "inventoryPolicyRule1",
                },
                new AzureNative.Storage.Inputs.BlobInventoryPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.BlobInventoryPolicyDefinitionArgs
                    {
                        Format = "Parquet",
                        ObjectType = "Container",
                        Schedule = "Weekly",
                        SchemaFields = new[]
                        {
                            "Name",
                            "Last-Modified",
                            "Metadata",
                            "LeaseStatus",
                            "LeaseState",
                            "LeaseDuration",
                            "PublicAccess",
                            "HasImmutabilityPolicy",
                            "HasLegalHold",
                            "Etag",
                            "DefaultEncryptionScope",
                            "DenyEncryptionScopeOverride",
                            "ImmutableStorageWithVersioningEnabled",
                            "Deleted",
                            "Version",
                            "DeletedTime",
                            "RemainingRetentionDays",
                        },
                    },
                    Destination = "container2",
                    Enabled = true,
                    Name = "inventoryPolicyRule2",
                },
            },
            Type = "Inventory",
        },
        ResourceGroupName = "res7687",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storage.BlobInventoryPolicy;
import com.pulumi.azurenative.storage.BlobInventoryPolicyArgs;
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
        var blobInventoryPolicy = new BlobInventoryPolicy("blobInventoryPolicy", BlobInventoryPolicyArgs.builder()        
            .accountName("sto9699")
            .blobInventoryPolicyName("default")
            .policy(Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("definition", Map.ofEntries(
                            Map.entry("filters", Map.ofEntries(
                                Map.entry("blobTypes",                                 
                                    "blockBlob",
                                    "appendBlob",
                                    "pageBlob"),
                                Map.entry("excludePrefix",                                 
                                    "excludeprefix1",
                                    "excludeprefix2"),
                                Map.entry("includeBlobVersions", true),
                                Map.entry("includeDeleted", true),
                                Map.entry("includeSnapshots", true),
                                Map.entry("prefixMatch",                                 
                                    "inventoryprefix1",
                                    "inventoryprefix2")
                            )),
                            Map.entry("format", "Csv"),
                            Map.entry("objectType", "Blob"),
                            Map.entry("schedule", "Daily"),
                            Map.entry("schemaFields",                             
                                "Name",
                                "Creation-Time",
                                "Last-Modified",
                                "Content-Length",
                                "Content-MD5",
                                "BlobType",
                                "AccessTier",
                                "AccessTierChangeTime",
                                "Snapshot",
                                "VersionId",
                                "IsCurrentVersion",
                                "Tags",
                                "ContentType",
                                "ContentEncoding",
                                "ContentLanguage",
                                "ContentCRC64",
                                "CacheControl",
                                "Metadata",
                                "Deleted",
                                "RemainingRetentionDays")
                        )),
                        Map.entry("destination", "container1"),
                        Map.entry("enabled", true),
                        Map.entry("name", "inventoryPolicyRule1")
                    ),
                    Map.ofEntries(
                        Map.entry("definition", Map.ofEntries(
                            Map.entry("format", "Parquet"),
                            Map.entry("objectType", "Container"),
                            Map.entry("schedule", "Weekly"),
                            Map.entry("schemaFields",                             
                                "Name",
                                "Last-Modified",
                                "Metadata",
                                "LeaseStatus",
                                "LeaseState",
                                "LeaseDuration",
                                "PublicAccess",
                                "HasImmutabilityPolicy",
                                "HasLegalHold",
                                "Etag",
                                "DefaultEncryptionScope",
                                "DenyEncryptionScopeOverride",
                                "ImmutableStorageWithVersioningEnabled",
                                "Deleted",
                                "Version",
                                "DeletedTime",
                                "RemainingRetentionDays")
                        )),
                        Map.entry("destination", "container2"),
                        Map.entry("enabled", true),
                        Map.entry("name", "inventoryPolicyRule2")
                    )),
                Map.entry("type", "Inventory")
            ))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blobInventoryPolicy = new azure_native.storage.BlobInventoryPolicy("blobInventoryPolicy", {
    accountName: "sto9699",
    blobInventoryPolicyName: "default",
    policy: {
        enabled: true,
        rules: [
            {
                definition: {
                    filters: {
                        blobTypes: [
                            "blockBlob",
                            "appendBlob",
                            "pageBlob",
                        ],
                        excludePrefix: [
                            "excludeprefix1",
                            "excludeprefix2",
                        ],
                        includeBlobVersions: true,
                        includeDeleted: true,
                        includeSnapshots: true,
                        prefixMatch: [
                            "inventoryprefix1",
                            "inventoryprefix2",
                        ],
                    },
                    format: "Csv",
                    objectType: "Blob",
                    schedule: "Daily",
                    schemaFields: [
                        "Name",
                        "Creation-Time",
                        "Last-Modified",
                        "Content-Length",
                        "Content-MD5",
                        "BlobType",
                        "AccessTier",
                        "AccessTierChangeTime",
                        "Snapshot",
                        "VersionId",
                        "IsCurrentVersion",
                        "Tags",
                        "ContentType",
                        "ContentEncoding",
                        "ContentLanguage",
                        "ContentCRC64",
                        "CacheControl",
                        "Metadata",
                        "Deleted",
                        "RemainingRetentionDays",
                    ],
                },
                destination: "container1",
                enabled: true,
                name: "inventoryPolicyRule1",
            },
            {
                definition: {
                    format: "Parquet",
                    objectType: "Container",
                    schedule: "Weekly",
                    schemaFields: [
                        "Name",
                        "Last-Modified",
                        "Metadata",
                        "LeaseStatus",
                        "LeaseState",
                        "LeaseDuration",
                        "PublicAccess",
                        "HasImmutabilityPolicy",
                        "HasLegalHold",
                        "Etag",
                        "DefaultEncryptionScope",
                        "DenyEncryptionScopeOverride",
                        "ImmutableStorageWithVersioningEnabled",
                        "Deleted",
                        "Version",
                        "DeletedTime",
                        "RemainingRetentionDays",
                    ],
                },
                destination: "container2",
                enabled: true,
                name: "inventoryPolicyRule2",
            },
        ],
        type: "Inventory",
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blob_inventory_policy = azure_native.storage.BlobInventoryPolicy("blobInventoryPolicy",
    account_name="sto9699",
    blob_inventory_policy_name="default",
    policy=azure_native.storage.BlobInventoryPolicySchemaResponseArgs(
        enabled=True,
        rules=[
            {
                "definition": {
                    "filters": azure_native.storage.BlobInventoryPolicyFilterArgs(
                        blob_types=[
                            "blockBlob",
                            "appendBlob",
                            "pageBlob",
                        ],
                        exclude_prefix=[
                            "excludeprefix1",
                            "excludeprefix2",
                        ],
                        include_blob_versions=True,
                        include_deleted=True,
                        include_snapshots=True,
                        prefix_match=[
                            "inventoryprefix1",
                            "inventoryprefix2",
                        ],
                    ),
                    "format": "Csv",
                    "objectType": "Blob",
                    "schedule": "Daily",
                    "schemaFields": [
                        "Name",
                        "Creation-Time",
                        "Last-Modified",
                        "Content-Length",
                        "Content-MD5",
                        "BlobType",
                        "AccessTier",
                        "AccessTierChangeTime",
                        "Snapshot",
                        "VersionId",
                        "IsCurrentVersion",
                        "Tags",
                        "ContentType",
                        "ContentEncoding",
                        "ContentLanguage",
                        "ContentCRC64",
                        "CacheControl",
                        "Metadata",
                        "Deleted",
                        "RemainingRetentionDays",
                    ],
                },
                "destination": "container1",
                "enabled": True,
                "name": "inventoryPolicyRule1",
            },
            {
                "definition": azure_native.storage.BlobInventoryPolicyDefinitionArgs(
                    format="Parquet",
                    object_type="Container",
                    schedule="Weekly",
                    schema_fields=[
                        "Name",
                        "Last-Modified",
                        "Metadata",
                        "LeaseStatus",
                        "LeaseState",
                        "LeaseDuration",
                        "PublicAccess",
                        "HasImmutabilityPolicy",
                        "HasLegalHold",
                        "Etag",
                        "DefaultEncryptionScope",
                        "DenyEncryptionScopeOverride",
                        "ImmutableStorageWithVersioningEnabled",
                        "Deleted",
                        "Version",
                        "DeletedTime",
                        "RemainingRetentionDays",
                    ],
                ),
                "destination": "container2",
                "enabled": True,
                "name": "inventoryPolicyRule2",
            },
        ],
        type="Inventory",
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  blobInventoryPolicy:
    type: azure-native:storage:BlobInventoryPolicy
    properties:
      accountName: sto9699
      blobInventoryPolicyName: default
      policy:
        enabled: true
        rules:
          - definition:
              filters:
                blobTypes:
                  - blockBlob
                  - appendBlob
                  - pageBlob
                excludePrefix:
                  - excludeprefix1
                  - excludeprefix2
                includeBlobVersions: true
                includeDeleted: true
                includeSnapshots: true
                prefixMatch:
                  - inventoryprefix1
                  - inventoryprefix2
              format: Csv
              objectType: Blob
              schedule: Daily
              schemaFields:
                - Name
                - Creation-Time
                - Last-Modified
                - Content-Length
                - Content-MD5
                - BlobType
                - AccessTier
                - AccessTierChangeTime
                - Snapshot
                - VersionId
                - IsCurrentVersion
                - Tags
                - ContentType
                - ContentEncoding
                - ContentLanguage
                - ContentCRC64
                - CacheControl
                - Metadata
                - Deleted
                - RemainingRetentionDays
            destination: container1
            enabled: true
            name: inventoryPolicyRule1
          - definition:
              format: Parquet
              objectType: Container
              schedule: Weekly
              schemaFields:
                - Name
                - Last-Modified
                - Metadata
                - LeaseStatus
                - LeaseState
                - LeaseDuration
                - PublicAccess
                - HasImmutabilityPolicy
                - HasLegalHold
                - Etag
                - DefaultEncryptionScope
                - DenyEncryptionScopeOverride
                - ImmutableStorageWithVersioningEnabled
                - Deleted
                - Version
                - DeletedTime
                - RemainingRetentionDays
            destination: container2
            enabled: true
            name: inventoryPolicyRule2
        type: Inventory
      resourceGroupName: res7687

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:BlobInventoryPolicy DefaultInventoryPolicy /subscriptions/{subscription-id}/resourceGroups/res7687/providers/Microsoft.Storage/storageAccounts/sto9699/inventoryPolicies/default 
```
