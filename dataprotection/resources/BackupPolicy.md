BaseBackupPolicy resource
API Version: 2023-01-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate BackupPolicy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var backupPolicy = new AzureNative.DataProtection.BackupPolicy("backupPolicy", new()
    {
        BackupPolicyName = "OSSDBPolicy",
        Properties = new AzureNative.DataProtection.Inputs.BackupPolicyArgs
        {
            DatasourceTypes = new[]
            {
                "OssDB",
            },
            ObjectType = "BackupPolicy",
            PolicyRules = 
            {
                new AzureNative.DataProtection.Inputs.AzureBackupRuleArgs
                {
                    BackupParameters = new AzureNative.DataProtection.Inputs.AzureBackupParamsArgs
                    {
                        BackupType = "Full",
                        ObjectType = "AzureBackupParams",
                    },
                    DataStore = new AzureNative.DataProtection.Inputs.DataStoreInfoBaseArgs
                    {
                        DataStoreType = "VaultStore",
                        ObjectType = "DataStoreInfoBase",
                    },
                    Name = "BackupWeekly",
                    ObjectType = "AzureBackupRule",
                    Trigger = new AzureNative.DataProtection.Inputs.ScheduleBasedTriggerContextArgs
                    {
                        ObjectType = "ScheduleBasedTriggerContext",
                        Schedule = new AzureNative.DataProtection.Inputs.BackupScheduleArgs
                        {
                            RepeatingTimeIntervals = new[]
                            {
                                "R/2019-11-20T08:00:00-08:00/P1W",
                            },
                        },
                        TaggingCriteria = new[]
                        {
                            new AzureNative.DataProtection.Inputs.TaggingCriteriaArgs
                            {
                                IsDefault = true,
                                TagInfo = new AzureNative.DataProtection.Inputs.RetentionTagArgs
                                {
                                    TagName = "Default",
                                },
                                TaggingPriority = 99,
                            },
                            new AzureNative.DataProtection.Inputs.TaggingCriteriaArgs
                            {
                                Criteria = new[]
                                {
                                    new AzureNative.DataProtection.Inputs.ScheduleBasedBackupCriteriaArgs
                                    {
                                        DaysOfTheWeek = new[]
                                        {
                                            "Sunday",
                                        },
                                        ObjectType = "ScheduleBasedBackupCriteria",
                                        ScheduleTimes = new[]
                                        {
                                            "2019-03-01T13:00:00Z",
                                        },
                                    },
                                },
                                IsDefault = false,
                                TagInfo = new AzureNative.DataProtection.Inputs.RetentionTagArgs
                                {
                                    TagName = "Weekly",
                                },
                                TaggingPriority = 20,
                            },
                        },
                    },
                },
                new AzureNative.DataProtection.Inputs.AzureRetentionRuleArgs
                {
                    IsDefault = true,
                    Lifecycles = new[]
                    {
                        new AzureNative.DataProtection.Inputs.SourceLifeCycleArgs
                        {
                            DeleteAfter = new AzureNative.DataProtection.Inputs.AbsoluteDeleteOptionArgs
                            {
                                Duration = "P1W",
                                ObjectType = "AbsoluteDeleteOption",
                            },
                            SourceDataStore = new AzureNative.DataProtection.Inputs.DataStoreInfoBaseArgs
                            {
                                DataStoreType = "VaultStore",
                                ObjectType = "DataStoreInfoBase",
                            },
                        },
                    },
                    Name = "Default",
                    ObjectType = "AzureRetentionRule",
                },
                new AzureNative.DataProtection.Inputs.AzureRetentionRuleArgs
                {
                    IsDefault = false,
                    Lifecycles = new[]
                    {
                        new AzureNative.DataProtection.Inputs.SourceLifeCycleArgs
                        {
                            DeleteAfter = new AzureNative.DataProtection.Inputs.AbsoluteDeleteOptionArgs
                            {
                                Duration = "P12W",
                                ObjectType = "AbsoluteDeleteOption",
                            },
                            SourceDataStore = new AzureNative.DataProtection.Inputs.DataStoreInfoBaseArgs
                            {
                                DataStoreType = "VaultStore",
                                ObjectType = "DataStoreInfoBase",
                            },
                        },
                    },
                    Name = "Weekly",
                    ObjectType = "AzureRetentionRule",
                },
            },
        },
        ResourceGroupName = "000pikumar",
        VaultName = "PrivatePreviewVault",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.dataprotection.BackupPolicy;
import com.pulumi.azurenative.dataprotection.BackupPolicyArgs;
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
        var backupPolicy = new BackupPolicy("backupPolicy", BackupPolicyArgs.builder()        
            .backupPolicyName("OSSDBPolicy")
            .properties(Map.ofEntries(
                Map.entry("datasourceTypes", "OssDB"),
                Map.entry("objectType", "BackupPolicy"),
                Map.entry("policyRules",                 
                    Map.ofEntries(
                        Map.entry("backupParameters", Map.ofEntries(
                            Map.entry("backupType", "Full"),
                            Map.entry("objectType", "AzureBackupParams")
                        )),
                        Map.entry("dataStore", Map.ofEntries(
                            Map.entry("dataStoreType", "VaultStore"),
                            Map.entry("objectType", "DataStoreInfoBase")
                        )),
                        Map.entry("name", "BackupWeekly"),
                        Map.entry("objectType", "AzureBackupRule"),
                        Map.entry("trigger", Map.ofEntries(
                            Map.entry("objectType", "ScheduleBasedTriggerContext"),
                            Map.entry("schedule", Map.of("repeatingTimeIntervals", "R/2019-11-20T08:00:00-08:00/P1W")),
                            Map.entry("taggingCriteria",                             
                                Map.ofEntries(
                                    Map.entry("isDefault", true),
                                    Map.entry("tagInfo", Map.of("tagName", "Default")),
                                    Map.entry("taggingPriority", 99)
                                ),
                                Map.ofEntries(
                                    Map.entry("criteria", Map.ofEntries(
                                        Map.entry("daysOfTheWeek", "Sunday"),
                                        Map.entry("objectType", "ScheduleBasedBackupCriteria"),
                                        Map.entry("scheduleTimes", "2019-03-01T13:00:00Z")
                                    )),
                                    Map.entry("isDefault", false),
                                    Map.entry("tagInfo", Map.of("tagName", "Weekly")),
                                    Map.entry("taggingPriority", 20)
                                ))
                        ))
                    ),
                    Map.ofEntries(
                        Map.entry("isDefault", true),
                        Map.entry("lifecycles", Map.ofEntries(
                            Map.entry("deleteAfter", Map.ofEntries(
                                Map.entry("duration", "P1W"),
                                Map.entry("objectType", "AbsoluteDeleteOption")
                            )),
                            Map.entry("sourceDataStore", Map.ofEntries(
                                Map.entry("dataStoreType", "VaultStore"),
                                Map.entry("objectType", "DataStoreInfoBase")
                            ))
                        )),
                        Map.entry("name", "Default"),
                        Map.entry("objectType", "AzureRetentionRule")
                    ),
                    Map.ofEntries(
                        Map.entry("isDefault", false),
                        Map.entry("lifecycles", Map.ofEntries(
                            Map.entry("deleteAfter", Map.ofEntries(
                                Map.entry("duration", "P12W"),
                                Map.entry("objectType", "AbsoluteDeleteOption")
                            )),
                            Map.entry("sourceDataStore", Map.ofEntries(
                                Map.entry("dataStoreType", "VaultStore"),
                                Map.entry("objectType", "DataStoreInfoBase")
                            ))
                        )),
                        Map.entry("name", "Weekly"),
                        Map.entry("objectType", "AzureRetentionRule")
                    ))
            ))
            .resourceGroupName("000pikumar")
            .vaultName("PrivatePreviewVault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const backupPolicy = new azure_native.dataprotection.BackupPolicy("backupPolicy", {
    backupPolicyName: "OSSDBPolicy",
    properties: {
        datasourceTypes: ["OssDB"],
        objectType: "BackupPolicy",
        policyRules: [
            {
                backupParameters: {
                    backupType: "Full",
                    objectType: "AzureBackupParams",
                },
                dataStore: {
                    dataStoreType: "VaultStore",
                    objectType: "DataStoreInfoBase",
                },
                name: "BackupWeekly",
                objectType: "AzureBackupRule",
                trigger: {
                    objectType: "ScheduleBasedTriggerContext",
                    schedule: {
                        repeatingTimeIntervals: ["R/2019-11-20T08:00:00-08:00/P1W"],
                    },
                    taggingCriteria: [
                        {
                            isDefault: true,
                            tagInfo: {
                                tagName: "Default",
                            },
                            taggingPriority: 99,
                        },
                        {
                            criteria: [{
                                daysOfTheWeek: ["Sunday"],
                                objectType: "ScheduleBasedBackupCriteria",
                                scheduleTimes: ["2019-03-01T13:00:00Z"],
                            }],
                            isDefault: false,
                            tagInfo: {
                                tagName: "Weekly",
                            },
                            taggingPriority: 20,
                        },
                    ],
                },
            },
            {
                isDefault: true,
                lifecycles: [{
                    deleteAfter: {
                        duration: "P1W",
                        objectType: "AbsoluteDeleteOption",
                    },
                    sourceDataStore: {
                        dataStoreType: "VaultStore",
                        objectType: "DataStoreInfoBase",
                    },
                }],
                name: "Default",
                objectType: "AzureRetentionRule",
            },
            {
                isDefault: false,
                lifecycles: [{
                    deleteAfter: {
                        duration: "P12W",
                        objectType: "AbsoluteDeleteOption",
                    },
                    sourceDataStore: {
                        dataStoreType: "VaultStore",
                        objectType: "DataStoreInfoBase",
                    },
                }],
                name: "Weekly",
                objectType: "AzureRetentionRule",
            },
        ],
    },
    resourceGroupName: "000pikumar",
    vaultName: "PrivatePreviewVault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

backup_policy = azure_native.dataprotection.BackupPolicy("backupPolicy",
    backup_policy_name="OSSDBPolicy",
    properties=azure_native.dataprotection.BackupPolicyResponseArgs(
        datasource_types=["OssDB"],
        object_type="BackupPolicy",
        policy_rules=[
            azure_native.dataprotection.AzureBackupRuleArgs(
                backup_parameters=azure_native.dataprotection.AzureBackupParamsArgs(
                    backup_type="Full",
                    object_type="AzureBackupParams",
                ),
                data_store=azure_native.dataprotection.DataStoreInfoBaseArgs(
                    data_store_type="VaultStore",
                    object_type="DataStoreInfoBase",
                ),
                name="BackupWeekly",
                object_type="AzureBackupRule",
                trigger=azure_native.dataprotection.ScheduleBasedTriggerContextArgs(
                    object_type="ScheduleBasedTriggerContext",
                    schedule=azure_native.dataprotection.BackupScheduleArgs(
                        repeating_time_intervals=["R/2019-11-20T08:00:00-08:00/P1W"],
                    ),
                    tagging_criteria=[
                        azure_native.dataprotection.TaggingCriteriaArgs(
                            is_default=True,
                            tag_info=azure_native.dataprotection.RetentionTagArgs(
                                tag_name="Default",
                            ),
                            tagging_priority=99,
                        ),
                        azure_native.dataprotection.TaggingCriteriaArgs(
                            criteria=[azure_native.dataprotection.ScheduleBasedBackupCriteriaArgs(
                                days_of_the_week=["Sunday"],
                                object_type="ScheduleBasedBackupCriteria",
                                schedule_times=["2019-03-01T13:00:00Z"],
                            )],
                            is_default=False,
                            tag_info=azure_native.dataprotection.RetentionTagArgs(
                                tag_name="Weekly",
                            ),
                            tagging_priority=20,
                        ),
                    ],
                ),
            ),
            azure_native.dataprotection.AzureRetentionRuleArgs(
                is_default=True,
                lifecycles=[azure_native.dataprotection.SourceLifeCycleArgs(
                    delete_after=azure_native.dataprotection.AbsoluteDeleteOptionArgs(
                        duration="P1W",
                        object_type="AbsoluteDeleteOption",
                    ),
                    source_data_store=azure_native.dataprotection.DataStoreInfoBaseArgs(
                        data_store_type="VaultStore",
                        object_type="DataStoreInfoBase",
                    ),
                )],
                name="Default",
                object_type="AzureRetentionRule",
            ),
            azure_native.dataprotection.AzureRetentionRuleArgs(
                is_default=False,
                lifecycles=[azure_native.dataprotection.SourceLifeCycleArgs(
                    delete_after=azure_native.dataprotection.AbsoluteDeleteOptionArgs(
                        duration="P12W",
                        object_type="AbsoluteDeleteOption",
                    ),
                    source_data_store=azure_native.dataprotection.DataStoreInfoBaseArgs(
                        data_store_type="VaultStore",
                        object_type="DataStoreInfoBase",
                    ),
                )],
                name="Weekly",
                object_type="AzureRetentionRule",
            ),
        ],
    ),
    resource_group_name="000pikumar",
    vault_name="PrivatePreviewVault")

```

```yaml
resources:
  backupPolicy:
    type: azure-native:dataprotection:BackupPolicy
    properties:
      backupPolicyName: OSSDBPolicy
      properties:
        datasourceTypes:
          - OssDB
        objectType: BackupPolicy
        policyRules:
          - backupParameters:
              backupType: Full
              objectType: AzureBackupParams
            dataStore:
              dataStoreType: VaultStore
              objectType: DataStoreInfoBase
            name: BackupWeekly
            objectType: AzureBackupRule
            trigger:
              objectType: ScheduleBasedTriggerContext
              schedule:
                repeatingTimeIntervals:
                  - R/2019-11-20T08:00:00-08:00/P1W
              taggingCriteria:
                - isDefault: true
                  tagInfo:
                    tagName: Default
                  taggingPriority: 99
                - criteria:
                    - daysOfTheWeek:
                        - Sunday
                      objectType: ScheduleBasedBackupCriteria
                      scheduleTimes:
                        - 2019-03-01T13:00:00Z
                  isDefault: false
                  tagInfo:
                    tagName: Weekly
                  taggingPriority: 20
          - isDefault: true
            lifecycles:
              - deleteAfter:
                  duration: P1W
                  objectType: AbsoluteDeleteOption
                sourceDataStore:
                  dataStoreType: VaultStore
                  objectType: DataStoreInfoBase
            name: Default
            objectType: AzureRetentionRule
          - isDefault: false
            lifecycles:
              - deleteAfter:
                  duration: P12W
                  objectType: AbsoluteDeleteOption
                sourceDataStore:
                  dataStoreType: VaultStore
                  objectType: DataStoreInfoBase
            name: Weekly
            objectType: AzureRetentionRule
      resourceGroupName: 000pikumar
      vaultName: PrivatePreviewVault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dataprotection:BackupPolicy OSSDBPolicy /subscriptions/04cf684a-d41f-4550-9f70-7708a3a2283b/resourceGroups/000pikumar/providers/Microsoft.DataProtection/backupVaults/PrivatePreviewVault/backupPolicies/OSSDBPolicy 
```
