The Get Storage Account ManagementPolicies operation response.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StorageAccountSetManagementPolicies
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementPolicy = new AzureNative.Storage.ManagementPolicy("managementPolicy", new()
    {
        AccountName = "sto9699",
        ManagementPolicyName = "default",
        Policy = new AzureNative.Storage.Inputs.ManagementPolicySchemaArgs
        {
            Rules = new[]
            {
                new AzureNative.Storage.Inputs.ManagementPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.ManagementPolicyDefinitionArgs
                    {
                        Actions = new AzureNative.Storage.Inputs.ManagementPolicyActionArgs
                        {
                            BaseBlob = new AzureNative.Storage.Inputs.ManagementPolicyBaseBlobArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 1000,
                                },
                                TierToArchive = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 90,
                                },
                                TierToCool = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 30,
                                },
                            },
                            Snapshot = new AzureNative.Storage.Inputs.ManagementPolicySnapShotArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                },
                            },
                        },
                        Filters = new AzureNative.Storage.Inputs.ManagementPolicyFilterArgs
                        {
                            BlobTypes = new[]
                            {
                                "blockBlob",
                            },
                            PrefixMatch = new[]
                            {
                                "olcmtestcontainer1",
                            },
                        },
                    },
                    Enabled = true,
                    Name = "olcmtest1",
                    Type = "Lifecycle",
                },
                new AzureNative.Storage.Inputs.ManagementPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.ManagementPolicyDefinitionArgs
                    {
                        Actions = new AzureNative.Storage.Inputs.ManagementPolicyActionArgs
                        {
                            BaseBlob = new AzureNative.Storage.Inputs.ManagementPolicyBaseBlobArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 1000,
                                },
                                TierToArchive = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 90,
                                },
                                TierToCool = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 30,
                                },
                            },
                        },
                        Filters = new AzureNative.Storage.Inputs.ManagementPolicyFilterArgs
                        {
                            BlobIndexMatch = new[]
                            {
                                new AzureNative.Storage.Inputs.TagFilterArgs
                                {
                                    Name = "tag1",
                                    Op = "==",
                                    Value = "val1",
                                },
                                new AzureNative.Storage.Inputs.TagFilterArgs
                                {
                                    Name = "tag2",
                                    Op = "==",
                                    Value = "val2",
                                },
                            },
                            BlobTypes = new[]
                            {
                                "blockBlob",
                            },
                            PrefixMatch = new[]
                            {
                                "olcmtestcontainer2",
                            },
                        },
                    },
                    Enabled = true,
                    Name = "olcmtest2",
                    Type = "Lifecycle",
                },
            },
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
import com.pulumi.azurenative.storage.ManagementPolicy;
import com.pulumi.azurenative.storage.ManagementPolicyArgs;
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
        var managementPolicy = new ManagementPolicy("managementPolicy", ManagementPolicyArgs.builder()        
            .accountName("sto9699")
            .managementPolicyName("default")
            .policy(Map.of("rules",             
                Map.ofEntries(
                    Map.entry("definition", Map.ofEntries(
                        Map.entry("actions", Map.ofEntries(
                            Map.entry("baseBlob", Map.ofEntries(
                                Map.entry("delete", Map.of("daysAfterModificationGreaterThan", 1000)),
                                Map.entry("tierToArchive", Map.of("daysAfterModificationGreaterThan", 90)),
                                Map.entry("tierToCool", Map.of("daysAfterModificationGreaterThan", 30))
                            )),
                            Map.entry("snapshot", Map.of("delete", Map.of("daysAfterCreationGreaterThan", 30)))
                        )),
                        Map.entry("filters", Map.ofEntries(
                            Map.entry("blobTypes", "blockBlob"),
                            Map.entry("prefixMatch", "olcmtestcontainer1")
                        ))
                    )),
                    Map.entry("enabled", true),
                    Map.entry("name", "olcmtest1"),
                    Map.entry("type", "Lifecycle")
                ),
                Map.ofEntries(
                    Map.entry("definition", Map.ofEntries(
                        Map.entry("actions", Map.of("baseBlob", Map.ofEntries(
                            Map.entry("delete", Map.of("daysAfterModificationGreaterThan", 1000)),
                            Map.entry("tierToArchive", Map.of("daysAfterModificationGreaterThan", 90)),
                            Map.entry("tierToCool", Map.of("daysAfterModificationGreaterThan", 30))
                        ))),
                        Map.entry("filters", Map.ofEntries(
                            Map.entry("blobIndexMatch",                             
                                Map.ofEntries(
                                    Map.entry("name", "tag1"),
                                    Map.entry("op", "=="),
                                    Map.entry("value", "val1")
                                ),
                                Map.ofEntries(
                                    Map.entry("name", "tag2"),
                                    Map.entry("op", "=="),
                                    Map.entry("value", "val2")
                                )),
                            Map.entry("blobTypes", "blockBlob"),
                            Map.entry("prefixMatch", "olcmtestcontainer2")
                        ))
                    )),
                    Map.entry("enabled", true),
                    Map.entry("name", "olcmtest2"),
                    Map.entry("type", "Lifecycle")
                )))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementPolicy = new azure_native.storage.ManagementPolicy("managementPolicy", {
    accountName: "sto9699",
    managementPolicyName: "default",
    policy: {
        rules: [
            {
                definition: {
                    actions: {
                        baseBlob: {
                            "delete": {
                                daysAfterModificationGreaterThan: 1000,
                            },
                            tierToArchive: {
                                daysAfterModificationGreaterThan: 90,
                            },
                            tierToCool: {
                                daysAfterModificationGreaterThan: 30,
                            },
                        },
                        snapshot: {
                            "delete": {
                                daysAfterCreationGreaterThan: 30,
                            },
                        },
                    },
                    filters: {
                        blobTypes: ["blockBlob"],
                        prefixMatch: ["olcmtestcontainer1"],
                    },
                },
                enabled: true,
                name: "olcmtest1",
                type: "Lifecycle",
            },
            {
                definition: {
                    actions: {
                        baseBlob: {
                            "delete": {
                                daysAfterModificationGreaterThan: 1000,
                            },
                            tierToArchive: {
                                daysAfterModificationGreaterThan: 90,
                            },
                            tierToCool: {
                                daysAfterModificationGreaterThan: 30,
                            },
                        },
                    },
                    filters: {
                        blobIndexMatch: [
                            {
                                name: "tag1",
                                op: "==",
                                value: "val1",
                            },
                            {
                                name: "tag2",
                                op: "==",
                                value: "val2",
                            },
                        ],
                        blobTypes: ["blockBlob"],
                        prefixMatch: ["olcmtestcontainer2"],
                    },
                },
                enabled: true,
                name: "olcmtest2",
                type: "Lifecycle",
            },
        ],
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_policy = azure_native.storage.ManagementPolicy("managementPolicy",
    account_name="sto9699",
    management_policy_name="default",
    policy=azure_native.storage.ManagementPolicySchemaResponseArgs(
        rules=[
            {
                "definition": {
                    "actions": {
                        "baseBlob": {
                            "delete": azure_native.storage.DateAfterModificationArgs(
                                days_after_modification_greater_than=1000,
                            ),
                            "tierToArchive": azure_native.storage.DateAfterModificationArgs(
                                days_after_modification_greater_than=90,
                            ),
                            "tierToCool": azure_native.storage.DateAfterModificationArgs(
                                days_after_modification_greater_than=30,
                            ),
                        },
                        "snapshot": {
                            "delete": azure_native.storage.DateAfterCreationArgs(
                                days_after_creation_greater_than=30,
                            ),
                        },
                    },
                    "filters": azure_native.storage.ManagementPolicyFilterArgs(
                        blob_types=["blockBlob"],
                        prefix_match=["olcmtestcontainer1"],
                    ),
                },
                "enabled": True,
                "name": "olcmtest1",
                "type": "Lifecycle",
            },
            {
                "definition": {
                    "actions": {
                        "baseBlob": {
                            "delete": azure_native.storage.DateAfterModificationArgs(
                                days_after_modification_greater_than=1000,
                            ),
                            "tierToArchive": azure_native.storage.DateAfterModificationArgs(
                                days_after_modification_greater_than=90,
                            ),
                            "tierToCool": azure_native.storage.DateAfterModificationArgs(
                                days_after_modification_greater_than=30,
                            ),
                        },
                    },
                    "filters": {
                        "blobIndexMatch": [
                            azure_native.storage.TagFilterArgs(
                                name="tag1",
                                op="==",
                                value="val1",
                            ),
                            azure_native.storage.TagFilterArgs(
                                name="tag2",
                                op="==",
                                value="val2",
                            ),
                        ],
                        "blobTypes": ["blockBlob"],
                        "prefixMatch": ["olcmtestcontainer2"],
                    },
                },
                "enabled": True,
                "name": "olcmtest2",
                "type": "Lifecycle",
            },
        ],
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  managementPolicy:
    type: azure-native:storage:ManagementPolicy
    properties:
      accountName: sto9699
      managementPolicyName: default
      policy:
        rules:
          - definition:
              actions:
                baseBlob:
                  delete:
                    daysAfterModificationGreaterThan: 1000
                  tierToArchive:
                    daysAfterModificationGreaterThan: 90
                  tierToCool:
                    daysAfterModificationGreaterThan: 30
                snapshot:
                  delete:
                    daysAfterCreationGreaterThan: 30
              filters:
                blobTypes:
                  - blockBlob
                prefixMatch:
                  - olcmtestcontainer1
            enabled: true
            name: olcmtest1
            type: Lifecycle
          - definition:
              actions:
                baseBlob:
                  delete:
                    daysAfterModificationGreaterThan: 1000
                  tierToArchive:
                    daysAfterModificationGreaterThan: 90
                  tierToCool:
                    daysAfterModificationGreaterThan: 30
              filters:
                blobIndexMatch:
                  - name: tag1
                    op: ==
                    value: val1
                  - name: tag2
                    op: ==
                    value: val2
                blobTypes:
                  - blockBlob
                prefixMatch:
                  - olcmtestcontainer2
            enabled: true
            name: olcmtest2
            type: Lifecycle
      resourceGroupName: res7687

```

{{% /example %}}
{{% example %}}
### StorageAccountSetManagementPolicyColdTierActions
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementPolicy = new AzureNative.Storage.ManagementPolicy("managementPolicy", new()
    {
        AccountName = "sto9699",
        ManagementPolicyName = "default",
        Policy = new AzureNative.Storage.Inputs.ManagementPolicySchemaArgs
        {
            Rules = new[]
            {
                new AzureNative.Storage.Inputs.ManagementPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.ManagementPolicyDefinitionArgs
                    {
                        Actions = new AzureNative.Storage.Inputs.ManagementPolicyActionArgs
                        {
                            BaseBlob = new AzureNative.Storage.Inputs.ManagementPolicyBaseBlobArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 1000,
                                },
                                TierToArchive = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 90,
                                },
                                TierToCold = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 30,
                                },
                                TierToCool = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 30,
                                },
                            },
                            Snapshot = new AzureNative.Storage.Inputs.ManagementPolicySnapShotArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                },
                                TierToCold = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                },
                            },
                            Version = new AzureNative.Storage.Inputs.ManagementPolicyVersionArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                },
                                TierToCold = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                },
                            },
                        },
                        Filters = new AzureNative.Storage.Inputs.ManagementPolicyFilterArgs
                        {
                            BlobTypes = new[]
                            {
                                "blockBlob",
                            },
                            PrefixMatch = new[]
                            {
                                "olcmtestcontainer1",
                            },
                        },
                    },
                    Enabled = true,
                    Name = "olcmtest1",
                    Type = "Lifecycle",
                },
            },
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
import com.pulumi.azurenative.storage.ManagementPolicy;
import com.pulumi.azurenative.storage.ManagementPolicyArgs;
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
        var managementPolicy = new ManagementPolicy("managementPolicy", ManagementPolicyArgs.builder()        
            .accountName("sto9699")
            .managementPolicyName("default")
            .policy(Map.of("rules", Map.ofEntries(
                Map.entry("definition", Map.ofEntries(
                    Map.entry("actions", Map.ofEntries(
                        Map.entry("baseBlob", Map.ofEntries(
                            Map.entry("delete", Map.of("daysAfterModificationGreaterThan", 1000)),
                            Map.entry("tierToArchive", Map.of("daysAfterModificationGreaterThan", 90)),
                            Map.entry("tierToCold", Map.of("daysAfterModificationGreaterThan", 30)),
                            Map.entry("tierToCool", Map.of("daysAfterModificationGreaterThan", 30))
                        )),
                        Map.entry("snapshot", Map.ofEntries(
                            Map.entry("delete", Map.of("daysAfterCreationGreaterThan", 30)),
                            Map.entry("tierToCold", Map.of("daysAfterCreationGreaterThan", 30))
                        )),
                        Map.entry("version", Map.ofEntries(
                            Map.entry("delete", Map.of("daysAfterCreationGreaterThan", 30)),
                            Map.entry("tierToCold", Map.of("daysAfterCreationGreaterThan", 30))
                        ))
                    )),
                    Map.entry("filters", Map.ofEntries(
                        Map.entry("blobTypes", "blockBlob"),
                        Map.entry("prefixMatch", "olcmtestcontainer1")
                    ))
                )),
                Map.entry("enabled", true),
                Map.entry("name", "olcmtest1"),
                Map.entry("type", "Lifecycle")
            )))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementPolicy = new azure_native.storage.ManagementPolicy("managementPolicy", {
    accountName: "sto9699",
    managementPolicyName: "default",
    policy: {
        rules: [{
            definition: {
                actions: {
                    baseBlob: {
                        "delete": {
                            daysAfterModificationGreaterThan: 1000,
                        },
                        tierToArchive: {
                            daysAfterModificationGreaterThan: 90,
                        },
                        tierToCold: {
                            daysAfterModificationGreaterThan: 30,
                        },
                        tierToCool: {
                            daysAfterModificationGreaterThan: 30,
                        },
                    },
                    snapshot: {
                        "delete": {
                            daysAfterCreationGreaterThan: 30,
                        },
                        tierToCold: {
                            daysAfterCreationGreaterThan: 30,
                        },
                    },
                    version: {
                        "delete": {
                            daysAfterCreationGreaterThan: 30,
                        },
                        tierToCold: {
                            daysAfterCreationGreaterThan: 30,
                        },
                    },
                },
                filters: {
                    blobTypes: ["blockBlob"],
                    prefixMatch: ["olcmtestcontainer1"],
                },
            },
            enabled: true,
            name: "olcmtest1",
            type: "Lifecycle",
        }],
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_policy = azure_native.storage.ManagementPolicy("managementPolicy",
    account_name="sto9699",
    management_policy_name="default",
    policy=azure_native.storage.ManagementPolicySchemaResponseArgs(
        rules=[{
            "definition": {
                "actions": {
                    "baseBlob": {
                        "delete": azure_native.storage.DateAfterModificationArgs(
                            days_after_modification_greater_than=1000,
                        ),
                        "tierToArchive": azure_native.storage.DateAfterModificationArgs(
                            days_after_modification_greater_than=90,
                        ),
                        "tierToCold": azure_native.storage.DateAfterModificationArgs(
                            days_after_modification_greater_than=30,
                        ),
                        "tierToCool": azure_native.storage.DateAfterModificationArgs(
                            days_after_modification_greater_than=30,
                        ),
                    },
                    "snapshot": {
                        "delete": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=30,
                        ),
                        "tierToCold": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=30,
                        ),
                    },
                    "version": {
                        "delete": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=30,
                        ),
                        "tierToCold": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=30,
                        ),
                    },
                },
                "filters": azure_native.storage.ManagementPolicyFilterArgs(
                    blob_types=["blockBlob"],
                    prefix_match=["olcmtestcontainer1"],
                ),
            },
            "enabled": True,
            "name": "olcmtest1",
            "type": "Lifecycle",
        }],
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  managementPolicy:
    type: azure-native:storage:ManagementPolicy
    properties:
      accountName: sto9699
      managementPolicyName: default
      policy:
        rules:
          - definition:
              actions:
                baseBlob:
                  delete:
                    daysAfterModificationGreaterThan: 1000
                  tierToArchive:
                    daysAfterModificationGreaterThan: 90
                  tierToCold:
                    daysAfterModificationGreaterThan: 30
                  tierToCool:
                    daysAfterModificationGreaterThan: 30
                snapshot:
                  delete:
                    daysAfterCreationGreaterThan: 30
                  tierToCold:
                    daysAfterCreationGreaterThan: 30
                version:
                  delete:
                    daysAfterCreationGreaterThan: 30
                  tierToCold:
                    daysAfterCreationGreaterThan: 30
              filters:
                blobTypes:
                  - blockBlob
                prefixMatch:
                  - olcmtestcontainer1
            enabled: true
            name: olcmtest1
            type: Lifecycle
      resourceGroupName: res7687

```

{{% /example %}}
{{% example %}}
### StorageAccountSetManagementPolicyForBlockAndAppendBlobs
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementPolicy = new AzureNative.Storage.ManagementPolicy("managementPolicy", new()
    {
        AccountName = "sto9699",
        ManagementPolicyName = "default",
        Policy = new AzureNative.Storage.Inputs.ManagementPolicySchemaArgs
        {
            Rules = new[]
            {
                new AzureNative.Storage.Inputs.ManagementPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.ManagementPolicyDefinitionArgs
                    {
                        Actions = new AzureNative.Storage.Inputs.ManagementPolicyActionArgs
                        {
                            BaseBlob = new AzureNative.Storage.Inputs.ManagementPolicyBaseBlobArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 90,
                                },
                            },
                            Snapshot = new AzureNative.Storage.Inputs.ManagementPolicySnapShotArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 90,
                                },
                            },
                            Version = new AzureNative.Storage.Inputs.ManagementPolicyVersionArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 90,
                                },
                            },
                        },
                        Filters = new AzureNative.Storage.Inputs.ManagementPolicyFilterArgs
                        {
                            BlobTypes = new[]
                            {
                                "blockBlob",
                                "appendBlob",
                            },
                            PrefixMatch = new[]
                            {
                                "olcmtestcontainer1",
                            },
                        },
                    },
                    Enabled = true,
                    Name = "olcmtest1",
                    Type = "Lifecycle",
                },
            },
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
import com.pulumi.azurenative.storage.ManagementPolicy;
import com.pulumi.azurenative.storage.ManagementPolicyArgs;
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
        var managementPolicy = new ManagementPolicy("managementPolicy", ManagementPolicyArgs.builder()        
            .accountName("sto9699")
            .managementPolicyName("default")
            .policy(Map.of("rules", Map.ofEntries(
                Map.entry("definition", Map.ofEntries(
                    Map.entry("actions", Map.ofEntries(
                        Map.entry("baseBlob", Map.of("delete", Map.of("daysAfterModificationGreaterThan", 90))),
                        Map.entry("snapshot", Map.of("delete", Map.of("daysAfterCreationGreaterThan", 90))),
                        Map.entry("version", Map.of("delete", Map.of("daysAfterCreationGreaterThan", 90)))
                    )),
                    Map.entry("filters", Map.ofEntries(
                        Map.entry("blobTypes",                         
                            "blockBlob",
                            "appendBlob"),
                        Map.entry("prefixMatch", "olcmtestcontainer1")
                    ))
                )),
                Map.entry("enabled", true),
                Map.entry("name", "olcmtest1"),
                Map.entry("type", "Lifecycle")
            )))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementPolicy = new azure_native.storage.ManagementPolicy("managementPolicy", {
    accountName: "sto9699",
    managementPolicyName: "default",
    policy: {
        rules: [{
            definition: {
                actions: {
                    baseBlob: {
                        "delete": {
                            daysAfterModificationGreaterThan: 90,
                        },
                    },
                    snapshot: {
                        "delete": {
                            daysAfterCreationGreaterThan: 90,
                        },
                    },
                    version: {
                        "delete": {
                            daysAfterCreationGreaterThan: 90,
                        },
                    },
                },
                filters: {
                    blobTypes: [
                        "blockBlob",
                        "appendBlob",
                    ],
                    prefixMatch: ["olcmtestcontainer1"],
                },
            },
            enabled: true,
            name: "olcmtest1",
            type: "Lifecycle",
        }],
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_policy = azure_native.storage.ManagementPolicy("managementPolicy",
    account_name="sto9699",
    management_policy_name="default",
    policy=azure_native.storage.ManagementPolicySchemaResponseArgs(
        rules=[{
            "definition": {
                "actions": {
                    "baseBlob": {
                        "delete": azure_native.storage.DateAfterModificationArgs(
                            days_after_modification_greater_than=90,
                        ),
                    },
                    "snapshot": {
                        "delete": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=90,
                        ),
                    },
                    "version": {
                        "delete": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=90,
                        ),
                    },
                },
                "filters": azure_native.storage.ManagementPolicyFilterArgs(
                    blob_types=[
                        "blockBlob",
                        "appendBlob",
                    ],
                    prefix_match=["olcmtestcontainer1"],
                ),
            },
            "enabled": True,
            "name": "olcmtest1",
            "type": "Lifecycle",
        }],
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  managementPolicy:
    type: azure-native:storage:ManagementPolicy
    properties:
      accountName: sto9699
      managementPolicyName: default
      policy:
        rules:
          - definition:
              actions:
                baseBlob:
                  delete:
                    daysAfterModificationGreaterThan: 90
                snapshot:
                  delete:
                    daysAfterCreationGreaterThan: 90
                version:
                  delete:
                    daysAfterCreationGreaterThan: 90
              filters:
                blobTypes:
                  - blockBlob
                  - appendBlob
                prefixMatch:
                  - olcmtestcontainer1
            enabled: true
            name: olcmtest1
            type: Lifecycle
      resourceGroupName: res7687

```

{{% /example %}}
{{% example %}}
### StorageAccountSetManagementPolicyHotTierActions
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementPolicy = new AzureNative.Storage.ManagementPolicy("managementPolicy", new()
    {
        AccountName = "sto9699",
        ManagementPolicyName = "default",
        Policy = new AzureNative.Storage.Inputs.ManagementPolicySchemaArgs
        {
            Rules = new[]
            {
                new AzureNative.Storage.Inputs.ManagementPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.ManagementPolicyDefinitionArgs
                    {
                        Actions = new AzureNative.Storage.Inputs.ManagementPolicyActionArgs
                        {
                            BaseBlob = new AzureNative.Storage.Inputs.ManagementPolicyBaseBlobArgs
                            {
                                TierToHot = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 30,
                                },
                            },
                            Snapshot = new AzureNative.Storage.Inputs.ManagementPolicySnapShotArgs
                            {
                                TierToHot = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                },
                            },
                            Version = new AzureNative.Storage.Inputs.ManagementPolicyVersionArgs
                            {
                                TierToHot = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                },
                            },
                        },
                        Filters = new AzureNative.Storage.Inputs.ManagementPolicyFilterArgs
                        {
                            BlobTypes = new[]
                            {
                                "blockBlob",
                            },
                            PrefixMatch = new[]
                            {
                                "olcmtestcontainer1",
                            },
                        },
                    },
                    Enabled = true,
                    Name = "olcmtest1",
                    Type = "Lifecycle",
                },
            },
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
import com.pulumi.azurenative.storage.ManagementPolicy;
import com.pulumi.azurenative.storage.ManagementPolicyArgs;
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
        var managementPolicy = new ManagementPolicy("managementPolicy", ManagementPolicyArgs.builder()        
            .accountName("sto9699")
            .managementPolicyName("default")
            .policy(Map.of("rules", Map.ofEntries(
                Map.entry("definition", Map.ofEntries(
                    Map.entry("actions", Map.ofEntries(
                        Map.entry("baseBlob", Map.of("tierToHot", Map.of("daysAfterModificationGreaterThan", 30))),
                        Map.entry("snapshot", Map.of("tierToHot", Map.of("daysAfterCreationGreaterThan", 30))),
                        Map.entry("version", Map.of("tierToHot", Map.of("daysAfterCreationGreaterThan", 30)))
                    )),
                    Map.entry("filters", Map.ofEntries(
                        Map.entry("blobTypes", "blockBlob"),
                        Map.entry("prefixMatch", "olcmtestcontainer1")
                    ))
                )),
                Map.entry("enabled", true),
                Map.entry("name", "olcmtest1"),
                Map.entry("type", "Lifecycle")
            )))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementPolicy = new azure_native.storage.ManagementPolicy("managementPolicy", {
    accountName: "sto9699",
    managementPolicyName: "default",
    policy: {
        rules: [{
            definition: {
                actions: {
                    baseBlob: {
                        tierToHot: {
                            daysAfterModificationGreaterThan: 30,
                        },
                    },
                    snapshot: {
                        tierToHot: {
                            daysAfterCreationGreaterThan: 30,
                        },
                    },
                    version: {
                        tierToHot: {
                            daysAfterCreationGreaterThan: 30,
                        },
                    },
                },
                filters: {
                    blobTypes: ["blockBlob"],
                    prefixMatch: ["olcmtestcontainer1"],
                },
            },
            enabled: true,
            name: "olcmtest1",
            type: "Lifecycle",
        }],
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_policy = azure_native.storage.ManagementPolicy("managementPolicy",
    account_name="sto9699",
    management_policy_name="default",
    policy=azure_native.storage.ManagementPolicySchemaResponseArgs(
        rules=[{
            "definition": {
                "actions": {
                    "baseBlob": {
                        "tierToHot": azure_native.storage.DateAfterModificationArgs(
                            days_after_modification_greater_than=30,
                        ),
                    },
                    "snapshot": {
                        "tierToHot": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=30,
                        ),
                    },
                    "version": {
                        "tierToHot": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=30,
                        ),
                    },
                },
                "filters": azure_native.storage.ManagementPolicyFilterArgs(
                    blob_types=["blockBlob"],
                    prefix_match=["olcmtestcontainer1"],
                ),
            },
            "enabled": True,
            "name": "olcmtest1",
            "type": "Lifecycle",
        }],
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  managementPolicy:
    type: azure-native:storage:ManagementPolicy
    properties:
      accountName: sto9699
      managementPolicyName: default
      policy:
        rules:
          - definition:
              actions:
                baseBlob:
                  tierToHot:
                    daysAfterModificationGreaterThan: 30
                snapshot:
                  tierToHot:
                    daysAfterCreationGreaterThan: 30
                version:
                  tierToHot:
                    daysAfterCreationGreaterThan: 30
              filters:
                blobTypes:
                  - blockBlob
                prefixMatch:
                  - olcmtestcontainer1
            enabled: true
            name: olcmtest1
            type: Lifecycle
      resourceGroupName: res7687

```

{{% /example %}}
{{% example %}}
### StorageAccountSetManagementPolicyWithSnapshotAndVersion
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementPolicy = new AzureNative.Storage.ManagementPolicy("managementPolicy", new()
    {
        AccountName = "sto9699",
        ManagementPolicyName = "default",
        Policy = new AzureNative.Storage.Inputs.ManagementPolicySchemaArgs
        {
            Rules = new[]
            {
                new AzureNative.Storage.Inputs.ManagementPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.ManagementPolicyDefinitionArgs
                    {
                        Actions = new AzureNative.Storage.Inputs.ManagementPolicyActionArgs
                        {
                            BaseBlob = new AzureNative.Storage.Inputs.ManagementPolicyBaseBlobArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 1000,
                                },
                                TierToArchive = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 90,
                                },
                                TierToCool = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 30,
                                },
                            },
                            Snapshot = new AzureNative.Storage.Inputs.ManagementPolicySnapShotArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 1000,
                                },
                                TierToArchive = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 90,
                                },
                                TierToCool = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                },
                            },
                            Version = new AzureNative.Storage.Inputs.ManagementPolicyVersionArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 1000,
                                },
                                TierToArchive = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 90,
                                },
                                TierToCool = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                },
                            },
                        },
                        Filters = new AzureNative.Storage.Inputs.ManagementPolicyFilterArgs
                        {
                            BlobTypes = new[]
                            {
                                "blockBlob",
                            },
                            PrefixMatch = new[]
                            {
                                "olcmtestcontainer1",
                            },
                        },
                    },
                    Enabled = true,
                    Name = "olcmtest1",
                    Type = "Lifecycle",
                },
            },
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
import com.pulumi.azurenative.storage.ManagementPolicy;
import com.pulumi.azurenative.storage.ManagementPolicyArgs;
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
        var managementPolicy = new ManagementPolicy("managementPolicy", ManagementPolicyArgs.builder()        
            .accountName("sto9699")
            .managementPolicyName("default")
            .policy(Map.of("rules", Map.ofEntries(
                Map.entry("definition", Map.ofEntries(
                    Map.entry("actions", Map.ofEntries(
                        Map.entry("baseBlob", Map.ofEntries(
                            Map.entry("delete", Map.of("daysAfterModificationGreaterThan", 1000)),
                            Map.entry("tierToArchive", Map.of("daysAfterModificationGreaterThan", 90)),
                            Map.entry("tierToCool", Map.of("daysAfterModificationGreaterThan", 30))
                        )),
                        Map.entry("snapshot", Map.ofEntries(
                            Map.entry("delete", Map.of("daysAfterCreationGreaterThan", 1000)),
                            Map.entry("tierToArchive", Map.of("daysAfterCreationGreaterThan", 90)),
                            Map.entry("tierToCool", Map.of("daysAfterCreationGreaterThan", 30))
                        )),
                        Map.entry("version", Map.ofEntries(
                            Map.entry("delete", Map.of("daysAfterCreationGreaterThan", 1000)),
                            Map.entry("tierToArchive", Map.of("daysAfterCreationGreaterThan", 90)),
                            Map.entry("tierToCool", Map.of("daysAfterCreationGreaterThan", 30))
                        ))
                    )),
                    Map.entry("filters", Map.ofEntries(
                        Map.entry("blobTypes", "blockBlob"),
                        Map.entry("prefixMatch", "olcmtestcontainer1")
                    ))
                )),
                Map.entry("enabled", true),
                Map.entry("name", "olcmtest1"),
                Map.entry("type", "Lifecycle")
            )))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementPolicy = new azure_native.storage.ManagementPolicy("managementPolicy", {
    accountName: "sto9699",
    managementPolicyName: "default",
    policy: {
        rules: [{
            definition: {
                actions: {
                    baseBlob: {
                        "delete": {
                            daysAfterModificationGreaterThan: 1000,
                        },
                        tierToArchive: {
                            daysAfterModificationGreaterThan: 90,
                        },
                        tierToCool: {
                            daysAfterModificationGreaterThan: 30,
                        },
                    },
                    snapshot: {
                        "delete": {
                            daysAfterCreationGreaterThan: 1000,
                        },
                        tierToArchive: {
                            daysAfterCreationGreaterThan: 90,
                        },
                        tierToCool: {
                            daysAfterCreationGreaterThan: 30,
                        },
                    },
                    version: {
                        "delete": {
                            daysAfterCreationGreaterThan: 1000,
                        },
                        tierToArchive: {
                            daysAfterCreationGreaterThan: 90,
                        },
                        tierToCool: {
                            daysAfterCreationGreaterThan: 30,
                        },
                    },
                },
                filters: {
                    blobTypes: ["blockBlob"],
                    prefixMatch: ["olcmtestcontainer1"],
                },
            },
            enabled: true,
            name: "olcmtest1",
            type: "Lifecycle",
        }],
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_policy = azure_native.storage.ManagementPolicy("managementPolicy",
    account_name="sto9699",
    management_policy_name="default",
    policy=azure_native.storage.ManagementPolicySchemaResponseArgs(
        rules=[{
            "definition": {
                "actions": {
                    "baseBlob": {
                        "delete": azure_native.storage.DateAfterModificationArgs(
                            days_after_modification_greater_than=1000,
                        ),
                        "tierToArchive": azure_native.storage.DateAfterModificationArgs(
                            days_after_modification_greater_than=90,
                        ),
                        "tierToCool": azure_native.storage.DateAfterModificationArgs(
                            days_after_modification_greater_than=30,
                        ),
                    },
                    "snapshot": {
                        "delete": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=1000,
                        ),
                        "tierToArchive": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=90,
                        ),
                        "tierToCool": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=30,
                        ),
                    },
                    "version": {
                        "delete": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=1000,
                        ),
                        "tierToArchive": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=90,
                        ),
                        "tierToCool": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=30,
                        ),
                    },
                },
                "filters": azure_native.storage.ManagementPolicyFilterArgs(
                    blob_types=["blockBlob"],
                    prefix_match=["olcmtestcontainer1"],
                ),
            },
            "enabled": True,
            "name": "olcmtest1",
            "type": "Lifecycle",
        }],
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  managementPolicy:
    type: azure-native:storage:ManagementPolicy
    properties:
      accountName: sto9699
      managementPolicyName: default
      policy:
        rules:
          - definition:
              actions:
                baseBlob:
                  delete:
                    daysAfterModificationGreaterThan: 1000
                  tierToArchive:
                    daysAfterModificationGreaterThan: 90
                  tierToCool:
                    daysAfterModificationGreaterThan: 30
                snapshot:
                  delete:
                    daysAfterCreationGreaterThan: 1000
                  tierToArchive:
                    daysAfterCreationGreaterThan: 90
                  tierToCool:
                    daysAfterCreationGreaterThan: 30
                version:
                  delete:
                    daysAfterCreationGreaterThan: 1000
                  tierToArchive:
                    daysAfterCreationGreaterThan: 90
                  tierToCool:
                    daysAfterCreationGreaterThan: 30
              filters:
                blobTypes:
                  - blockBlob
                prefixMatch:
                  - olcmtestcontainer1
            enabled: true
            name: olcmtest1
            type: Lifecycle
      resourceGroupName: res7687

```

{{% /example %}}
{{% example %}}
### StorageAccountSetManagementPolicy_BaseBlobDaysAfterCreationActions
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementPolicy = new AzureNative.Storage.ManagementPolicy("managementPolicy", new()
    {
        AccountName = "sto9699",
        ManagementPolicyName = "default",
        Policy = new AzureNative.Storage.Inputs.ManagementPolicySchemaArgs
        {
            Rules = new[]
            {
                new AzureNative.Storage.Inputs.ManagementPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.ManagementPolicyDefinitionArgs
                    {
                        Actions = new AzureNative.Storage.Inputs.ManagementPolicyActionArgs
                        {
                            BaseBlob = new AzureNative.Storage.Inputs.ManagementPolicyBaseBlobArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterCreationGreaterThan = 1000,
                                },
                                TierToArchive = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterCreationGreaterThan = 90,
                                },
                                TierToCool = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                },
                            },
                        },
                        Filters = new AzureNative.Storage.Inputs.ManagementPolicyFilterArgs
                        {
                            BlobTypes = new[]
                            {
                                "blockBlob",
                            },
                            PrefixMatch = new[]
                            {
                                "olcmtestcontainer1",
                            },
                        },
                    },
                    Enabled = true,
                    Name = "olcmtest1",
                    Type = "Lifecycle",
                },
            },
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
import com.pulumi.azurenative.storage.ManagementPolicy;
import com.pulumi.azurenative.storage.ManagementPolicyArgs;
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
        var managementPolicy = new ManagementPolicy("managementPolicy", ManagementPolicyArgs.builder()        
            .accountName("sto9699")
            .managementPolicyName("default")
            .policy(Map.of("rules", Map.ofEntries(
                Map.entry("definition", Map.ofEntries(
                    Map.entry("actions", Map.of("baseBlob", Map.ofEntries(
                        Map.entry("delete", Map.of("daysAfterCreationGreaterThan", 1000)),
                        Map.entry("tierToArchive", Map.of("daysAfterCreationGreaterThan", 90)),
                        Map.entry("tierToCool", Map.of("daysAfterCreationGreaterThan", 30))
                    ))),
                    Map.entry("filters", Map.ofEntries(
                        Map.entry("blobTypes", "blockBlob"),
                        Map.entry("prefixMatch", "olcmtestcontainer1")
                    ))
                )),
                Map.entry("enabled", true),
                Map.entry("name", "olcmtest1"),
                Map.entry("type", "Lifecycle")
            )))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementPolicy = new azure_native.storage.ManagementPolicy("managementPolicy", {
    accountName: "sto9699",
    managementPolicyName: "default",
    policy: {
        rules: [{
            definition: {
                actions: {
                    baseBlob: {
                        "delete": {
                            daysAfterCreationGreaterThan: 1000,
                        },
                        tierToArchive: {
                            daysAfterCreationGreaterThan: 90,
                        },
                        tierToCool: {
                            daysAfterCreationGreaterThan: 30,
                        },
                    },
                },
                filters: {
                    blobTypes: ["blockBlob"],
                    prefixMatch: ["olcmtestcontainer1"],
                },
            },
            enabled: true,
            name: "olcmtest1",
            type: "Lifecycle",
        }],
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_policy = azure_native.storage.ManagementPolicy("managementPolicy",
    account_name="sto9699",
    management_policy_name="default",
    policy=azure_native.storage.ManagementPolicySchemaResponseArgs(
        rules=[{
            "definition": {
                "actions": {
                    "baseBlob": {
                        "delete": azure_native.storage.DateAfterModificationArgs(
                            days_after_creation_greater_than=1000,
                        ),
                        "tierToArchive": azure_native.storage.DateAfterModificationArgs(
                            days_after_creation_greater_than=90,
                        ),
                        "tierToCool": azure_native.storage.DateAfterModificationArgs(
                            days_after_creation_greater_than=30,
                        ),
                    },
                },
                "filters": azure_native.storage.ManagementPolicyFilterArgs(
                    blob_types=["blockBlob"],
                    prefix_match=["olcmtestcontainer1"],
                ),
            },
            "enabled": True,
            "name": "olcmtest1",
            "type": "Lifecycle",
        }],
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  managementPolicy:
    type: azure-native:storage:ManagementPolicy
    properties:
      accountName: sto9699
      managementPolicyName: default
      policy:
        rules:
          - definition:
              actions:
                baseBlob:
                  delete:
                    daysAfterCreationGreaterThan: 1000
                  tierToArchive:
                    daysAfterCreationGreaterThan: 90
                  tierToCool:
                    daysAfterCreationGreaterThan: 30
              filters:
                blobTypes:
                  - blockBlob
                prefixMatch:
                  - olcmtestcontainer1
            enabled: true
            name: olcmtest1
            type: Lifecycle
      resourceGroupName: res7687

```

{{% /example %}}
{{% example %}}
### StorageAccountSetManagementPolicy_LastAccessTimeBasedBlobActions
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementPolicy = new AzureNative.Storage.ManagementPolicy("managementPolicy", new()
    {
        AccountName = "sto9699",
        ManagementPolicyName = "default",
        Policy = new AzureNative.Storage.Inputs.ManagementPolicySchemaArgs
        {
            Rules = new[]
            {
                new AzureNative.Storage.Inputs.ManagementPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.ManagementPolicyDefinitionArgs
                    {
                        Actions = new AzureNative.Storage.Inputs.ManagementPolicyActionArgs
                        {
                            BaseBlob = new AzureNative.Storage.Inputs.ManagementPolicyBaseBlobArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterLastAccessTimeGreaterThan = 1000,
                                },
                                EnableAutoTierToHotFromCool = true,
                                TierToArchive = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterLastAccessTimeGreaterThan = 90,
                                },
                                TierToCool = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterLastAccessTimeGreaterThan = 30,
                                },
                            },
                            Snapshot = new AzureNative.Storage.Inputs.ManagementPolicySnapShotArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                },
                            },
                        },
                        Filters = new AzureNative.Storage.Inputs.ManagementPolicyFilterArgs
                        {
                            BlobTypes = new[]
                            {
                                "blockBlob",
                            },
                            PrefixMatch = new[]
                            {
                                "olcmtestcontainer",
                            },
                        },
                    },
                    Enabled = true,
                    Name = "olcmtest",
                    Type = "Lifecycle",
                },
            },
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
import com.pulumi.azurenative.storage.ManagementPolicy;
import com.pulumi.azurenative.storage.ManagementPolicyArgs;
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
        var managementPolicy = new ManagementPolicy("managementPolicy", ManagementPolicyArgs.builder()        
            .accountName("sto9699")
            .managementPolicyName("default")
            .policy(Map.of("rules", Map.ofEntries(
                Map.entry("definition", Map.ofEntries(
                    Map.entry("actions", Map.ofEntries(
                        Map.entry("baseBlob", Map.ofEntries(
                            Map.entry("delete", Map.of("daysAfterLastAccessTimeGreaterThan", 1000)),
                            Map.entry("enableAutoTierToHotFromCool", true),
                            Map.entry("tierToArchive", Map.of("daysAfterLastAccessTimeGreaterThan", 90)),
                            Map.entry("tierToCool", Map.of("daysAfterLastAccessTimeGreaterThan", 30))
                        )),
                        Map.entry("snapshot", Map.of("delete", Map.of("daysAfterCreationGreaterThan", 30)))
                    )),
                    Map.entry("filters", Map.ofEntries(
                        Map.entry("blobTypes", "blockBlob"),
                        Map.entry("prefixMatch", "olcmtestcontainer")
                    ))
                )),
                Map.entry("enabled", true),
                Map.entry("name", "olcmtest"),
                Map.entry("type", "Lifecycle")
            )))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementPolicy = new azure_native.storage.ManagementPolicy("managementPolicy", {
    accountName: "sto9699",
    managementPolicyName: "default",
    policy: {
        rules: [{
            definition: {
                actions: {
                    baseBlob: {
                        "delete": {
                            daysAfterLastAccessTimeGreaterThan: 1000,
                        },
                        enableAutoTierToHotFromCool: true,
                        tierToArchive: {
                            daysAfterLastAccessTimeGreaterThan: 90,
                        },
                        tierToCool: {
                            daysAfterLastAccessTimeGreaterThan: 30,
                        },
                    },
                    snapshot: {
                        "delete": {
                            daysAfterCreationGreaterThan: 30,
                        },
                    },
                },
                filters: {
                    blobTypes: ["blockBlob"],
                    prefixMatch: ["olcmtestcontainer"],
                },
            },
            enabled: true,
            name: "olcmtest",
            type: "Lifecycle",
        }],
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_policy = azure_native.storage.ManagementPolicy("managementPolicy",
    account_name="sto9699",
    management_policy_name="default",
    policy=azure_native.storage.ManagementPolicySchemaResponseArgs(
        rules=[{
            "definition": {
                "actions": {
                    "baseBlob": {
                        "delete": azure_native.storage.DateAfterModificationArgs(
                            days_after_last_access_time_greater_than=1000,
                        ),
                        "enableAutoTierToHotFromCool": True,
                        "tierToArchive": azure_native.storage.DateAfterModificationArgs(
                            days_after_last_access_time_greater_than=90,
                        ),
                        "tierToCool": azure_native.storage.DateAfterModificationArgs(
                            days_after_last_access_time_greater_than=30,
                        ),
                    },
                    "snapshot": {
                        "delete": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=30,
                        ),
                    },
                },
                "filters": azure_native.storage.ManagementPolicyFilterArgs(
                    blob_types=["blockBlob"],
                    prefix_match=["olcmtestcontainer"],
                ),
            },
            "enabled": True,
            "name": "olcmtest",
            "type": "Lifecycle",
        }],
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  managementPolicy:
    type: azure-native:storage:ManagementPolicy
    properties:
      accountName: sto9699
      managementPolicyName: default
      policy:
        rules:
          - definition:
              actions:
                baseBlob:
                  delete:
                    daysAfterLastAccessTimeGreaterThan: 1000
                  enableAutoTierToHotFromCool: true
                  tierToArchive:
                    daysAfterLastAccessTimeGreaterThan: 90
                  tierToCool:
                    daysAfterLastAccessTimeGreaterThan: 30
                snapshot:
                  delete:
                    daysAfterCreationGreaterThan: 30
              filters:
                blobTypes:
                  - blockBlob
                prefixMatch:
                  - olcmtestcontainer
            enabled: true
            name: olcmtest
            type: Lifecycle
      resourceGroupName: res7687

```

{{% /example %}}
{{% example %}}
### StorageAccountSetManagementPolicy_LastTierChangeTimeActions
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementPolicy = new AzureNative.Storage.ManagementPolicy("managementPolicy", new()
    {
        AccountName = "sto9699",
        ManagementPolicyName = "default",
        Policy = new AzureNative.Storage.Inputs.ManagementPolicySchemaArgs
        {
            Rules = new[]
            {
                new AzureNative.Storage.Inputs.ManagementPolicyRuleArgs
                {
                    Definition = new AzureNative.Storage.Inputs.ManagementPolicyDefinitionArgs
                    {
                        Actions = new AzureNative.Storage.Inputs.ManagementPolicyActionArgs
                        {
                            BaseBlob = new AzureNative.Storage.Inputs.ManagementPolicyBaseBlobArgs
                            {
                                Delete = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 1000,
                                },
                                TierToArchive = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterLastTierChangeGreaterThan = 120,
                                    DaysAfterModificationGreaterThan = 90,
                                },
                                TierToCool = new AzureNative.Storage.Inputs.DateAfterModificationArgs
                                {
                                    DaysAfterModificationGreaterThan = 30,
                                },
                            },
                            Snapshot = new AzureNative.Storage.Inputs.ManagementPolicySnapShotArgs
                            {
                                TierToArchive = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                    DaysAfterLastTierChangeGreaterThan = 90,
                                },
                            },
                            Version = new AzureNative.Storage.Inputs.ManagementPolicyVersionArgs
                            {
                                TierToArchive = new AzureNative.Storage.Inputs.DateAfterCreationArgs
                                {
                                    DaysAfterCreationGreaterThan = 30,
                                    DaysAfterLastTierChangeGreaterThan = 90,
                                },
                            },
                        },
                        Filters = new AzureNative.Storage.Inputs.ManagementPolicyFilterArgs
                        {
                            BlobTypes = new[]
                            {
                                "blockBlob",
                            },
                            PrefixMatch = new[]
                            {
                                "olcmtestcontainer",
                            },
                        },
                    },
                    Enabled = true,
                    Name = "olcmtest",
                    Type = "Lifecycle",
                },
            },
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
import com.pulumi.azurenative.storage.ManagementPolicy;
import com.pulumi.azurenative.storage.ManagementPolicyArgs;
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
        var managementPolicy = new ManagementPolicy("managementPolicy", ManagementPolicyArgs.builder()        
            .accountName("sto9699")
            .managementPolicyName("default")
            .policy(Map.of("rules", Map.ofEntries(
                Map.entry("definition", Map.ofEntries(
                    Map.entry("actions", Map.ofEntries(
                        Map.entry("baseBlob", Map.ofEntries(
                            Map.entry("delete", Map.of("daysAfterModificationGreaterThan", 1000)),
                            Map.entry("tierToArchive", Map.ofEntries(
                                Map.entry("daysAfterLastTierChangeGreaterThan", 120),
                                Map.entry("daysAfterModificationGreaterThan", 90)
                            )),
                            Map.entry("tierToCool", Map.of("daysAfterModificationGreaterThan", 30))
                        )),
                        Map.entry("snapshot", Map.of("tierToArchive", Map.ofEntries(
                            Map.entry("daysAfterCreationGreaterThan", 30),
                            Map.entry("daysAfterLastTierChangeGreaterThan", 90)
                        ))),
                        Map.entry("version", Map.of("tierToArchive", Map.ofEntries(
                            Map.entry("daysAfterCreationGreaterThan", 30),
                            Map.entry("daysAfterLastTierChangeGreaterThan", 90)
                        )))
                    )),
                    Map.entry("filters", Map.ofEntries(
                        Map.entry("blobTypes", "blockBlob"),
                        Map.entry("prefixMatch", "olcmtestcontainer")
                    ))
                )),
                Map.entry("enabled", true),
                Map.entry("name", "olcmtest"),
                Map.entry("type", "Lifecycle")
            )))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementPolicy = new azure_native.storage.ManagementPolicy("managementPolicy", {
    accountName: "sto9699",
    managementPolicyName: "default",
    policy: {
        rules: [{
            definition: {
                actions: {
                    baseBlob: {
                        "delete": {
                            daysAfterModificationGreaterThan: 1000,
                        },
                        tierToArchive: {
                            daysAfterLastTierChangeGreaterThan: 120,
                            daysAfterModificationGreaterThan: 90,
                        },
                        tierToCool: {
                            daysAfterModificationGreaterThan: 30,
                        },
                    },
                    snapshot: {
                        tierToArchive: {
                            daysAfterCreationGreaterThan: 30,
                            daysAfterLastTierChangeGreaterThan: 90,
                        },
                    },
                    version: {
                        tierToArchive: {
                            daysAfterCreationGreaterThan: 30,
                            daysAfterLastTierChangeGreaterThan: 90,
                        },
                    },
                },
                filters: {
                    blobTypes: ["blockBlob"],
                    prefixMatch: ["olcmtestcontainer"],
                },
            },
            enabled: true,
            name: "olcmtest",
            type: "Lifecycle",
        }],
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_policy = azure_native.storage.ManagementPolicy("managementPolicy",
    account_name="sto9699",
    management_policy_name="default",
    policy=azure_native.storage.ManagementPolicySchemaResponseArgs(
        rules=[{
            "definition": {
                "actions": {
                    "baseBlob": {
                        "delete": azure_native.storage.DateAfterModificationArgs(
                            days_after_modification_greater_than=1000,
                        ),
                        "tierToArchive": azure_native.storage.DateAfterModificationArgs(
                            days_after_last_tier_change_greater_than=120,
                            days_after_modification_greater_than=90,
                        ),
                        "tierToCool": azure_native.storage.DateAfterModificationArgs(
                            days_after_modification_greater_than=30,
                        ),
                    },
                    "snapshot": {
                        "tierToArchive": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=30,
                            days_after_last_tier_change_greater_than=90,
                        ),
                    },
                    "version": {
                        "tierToArchive": azure_native.storage.DateAfterCreationArgs(
                            days_after_creation_greater_than=30,
                            days_after_last_tier_change_greater_than=90,
                        ),
                    },
                },
                "filters": azure_native.storage.ManagementPolicyFilterArgs(
                    blob_types=["blockBlob"],
                    prefix_match=["olcmtestcontainer"],
                ),
            },
            "enabled": True,
            "name": "olcmtest",
            "type": "Lifecycle",
        }],
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  managementPolicy:
    type: azure-native:storage:ManagementPolicy
    properties:
      accountName: sto9699
      managementPolicyName: default
      policy:
        rules:
          - definition:
              actions:
                baseBlob:
                  delete:
                    daysAfterModificationGreaterThan: 1000
                  tierToArchive:
                    daysAfterLastTierChangeGreaterThan: 120
                    daysAfterModificationGreaterThan: 90
                  tierToCool:
                    daysAfterModificationGreaterThan: 30
                snapshot:
                  tierToArchive:
                    daysAfterCreationGreaterThan: 30
                    daysAfterLastTierChangeGreaterThan: 90
                version:
                  tierToArchive:
                    daysAfterCreationGreaterThan: 30
                    daysAfterLastTierChangeGreaterThan: 90
              filters:
                blobTypes:
                  - blockBlob
                prefixMatch:
                  - olcmtestcontainer
            enabled: true
            name: olcmtest
            type: Lifecycle
      resourceGroupName: res7687

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:ManagementPolicy DefaultManagementPolicy /subscriptions/{subscription-id}/resourceGroups/res7231/providers/Microsoft.Storage/storageAccounts/sto288/managementPolicies/default 
```
