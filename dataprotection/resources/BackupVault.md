Backup Vault Resource
API Version: 2023-01-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create BackupVault
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var backupVault = new AzureNative.DataProtection.BackupVault("backupVault", new()
    {
        Identity = new AzureNative.DataProtection.Inputs.DppIdentityDetailsArgs
        {
            Type = "None",
        },
        Location = "WestUS",
        Properties = new AzureNative.DataProtection.Inputs.BackupVaultArgs
        {
            MonitoringSettings = new AzureNative.DataProtection.Inputs.MonitoringSettingsArgs
            {
                AzureMonitorAlertSettings = new AzureNative.DataProtection.Inputs.AzureMonitorAlertSettingsArgs
                {
                    AlertsForAllJobFailures = "Enabled",
                },
            },
            StorageSettings = new[]
            {
                new AzureNative.DataProtection.Inputs.StorageSettingArgs
                {
                    DatastoreType = "VaultStore",
                    Type = "LocallyRedundant",
                },
            },
        },
        ResourceGroupName = "SampleResourceGroup",
        Tags = 
        {
            { "key1", "val1" },
        },
        VaultName = "swaggerExample",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.dataprotection.BackupVault;
import com.pulumi.azurenative.dataprotection.BackupVaultArgs;
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
        var backupVault = new BackupVault("backupVault", BackupVaultArgs.builder()        
            .identity(Map.of("type", "None"))
            .location("WestUS")
            .properties(Map.ofEntries(
                Map.entry("monitoringSettings", Map.of("azureMonitorAlertSettings", Map.of("alertsForAllJobFailures", "Enabled"))),
                Map.entry("storageSettings", Map.ofEntries(
                    Map.entry("datastoreType", "VaultStore"),
                    Map.entry("type", "LocallyRedundant")
                ))
            ))
            .resourceGroupName("SampleResourceGroup")
            .tags(Map.of("key1", "val1"))
            .vaultName("swaggerExample")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const backupVault = new azure_native.dataprotection.BackupVault("backupVault", {
    identity: {
        type: "None",
    },
    location: "WestUS",
    properties: {
        monitoringSettings: {
            azureMonitorAlertSettings: {
                alertsForAllJobFailures: "Enabled",
            },
        },
        storageSettings: [{
            datastoreType: "VaultStore",
            type: "LocallyRedundant",
        }],
    },
    resourceGroupName: "SampleResourceGroup",
    tags: {
        key1: "val1",
    },
    vaultName: "swaggerExample",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

backup_vault = azure_native.dataprotection.BackupVault("backupVault",
    identity=azure_native.dataprotection.DppIdentityDetailsArgs(
        type="None",
    ),
    location="WestUS",
    properties=azure_native.dataprotection.BackupVaultResponseArgs(
        monitoring_settings={
            "azureMonitorAlertSettings": azure_native.dataprotection.AzureMonitorAlertSettingsArgs(
                alerts_for_all_job_failures="Enabled",
            ),
        },
        storage_settings=[azure_native.dataprotection.StorageSettingArgs(
            datastore_type="VaultStore",
            type="LocallyRedundant",
        )],
    ),
    resource_group_name="SampleResourceGroup",
    tags={
        "key1": "val1",
    },
    vault_name="swaggerExample")

```

```yaml
resources:
  backupVault:
    type: azure-native:dataprotection:BackupVault
    properties:
      identity:
        type: None
      location: WestUS
      properties:
        monitoringSettings:
          azureMonitorAlertSettings:
            alertsForAllJobFailures: Enabled
        storageSettings:
          - datastoreType: VaultStore
            type: LocallyRedundant
      resourceGroupName: SampleResourceGroup
      tags:
        key1: val1
      vaultName: swaggerExample

```

{{% /example %}}
{{% example %}}
### Create BackupVault With MSI
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var backupVault = new AzureNative.DataProtection.BackupVault("backupVault", new()
    {
        Identity = new AzureNative.DataProtection.Inputs.DppIdentityDetailsArgs
        {
            Type = "systemAssigned",
        },
        Location = "WestUS",
        Properties = new AzureNative.DataProtection.Inputs.BackupVaultArgs
        {
            MonitoringSettings = new AzureNative.DataProtection.Inputs.MonitoringSettingsArgs
            {
                AzureMonitorAlertSettings = new AzureNative.DataProtection.Inputs.AzureMonitorAlertSettingsArgs
                {
                    AlertsForAllJobFailures = "Enabled",
                },
            },
            StorageSettings = new[]
            {
                new AzureNative.DataProtection.Inputs.StorageSettingArgs
                {
                    DatastoreType = "VaultStore",
                    Type = "LocallyRedundant",
                },
            },
        },
        ResourceGroupName = "SampleResourceGroup",
        Tags = 
        {
            { "key1", "val1" },
        },
        VaultName = "swaggerExample",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.dataprotection.BackupVault;
import com.pulumi.azurenative.dataprotection.BackupVaultArgs;
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
        var backupVault = new BackupVault("backupVault", BackupVaultArgs.builder()        
            .identity(Map.of("type", "systemAssigned"))
            .location("WestUS")
            .properties(Map.ofEntries(
                Map.entry("monitoringSettings", Map.of("azureMonitorAlertSettings", Map.of("alertsForAllJobFailures", "Enabled"))),
                Map.entry("storageSettings", Map.ofEntries(
                    Map.entry("datastoreType", "VaultStore"),
                    Map.entry("type", "LocallyRedundant")
                ))
            ))
            .resourceGroupName("SampleResourceGroup")
            .tags(Map.of("key1", "val1"))
            .vaultName("swaggerExample")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const backupVault = new azure_native.dataprotection.BackupVault("backupVault", {
    identity: {
        type: "systemAssigned",
    },
    location: "WestUS",
    properties: {
        monitoringSettings: {
            azureMonitorAlertSettings: {
                alertsForAllJobFailures: "Enabled",
            },
        },
        storageSettings: [{
            datastoreType: "VaultStore",
            type: "LocallyRedundant",
        }],
    },
    resourceGroupName: "SampleResourceGroup",
    tags: {
        key1: "val1",
    },
    vaultName: "swaggerExample",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

backup_vault = azure_native.dataprotection.BackupVault("backupVault",
    identity=azure_native.dataprotection.DppIdentityDetailsArgs(
        type="systemAssigned",
    ),
    location="WestUS",
    properties=azure_native.dataprotection.BackupVaultResponseArgs(
        monitoring_settings={
            "azureMonitorAlertSettings": azure_native.dataprotection.AzureMonitorAlertSettingsArgs(
                alerts_for_all_job_failures="Enabled",
            ),
        },
        storage_settings=[azure_native.dataprotection.StorageSettingArgs(
            datastore_type="VaultStore",
            type="LocallyRedundant",
        )],
    ),
    resource_group_name="SampleResourceGroup",
    tags={
        "key1": "val1",
    },
    vault_name="swaggerExample")

```

```yaml
resources:
  backupVault:
    type: azure-native:dataprotection:BackupVault
    properties:
      identity:
        type: systemAssigned
      location: WestUS
      properties:
        monitoringSettings:
          azureMonitorAlertSettings:
            alertsForAllJobFailures: Enabled
        storageSettings:
          - datastoreType: VaultStore
            type: LocallyRedundant
      resourceGroupName: SampleResourceGroup
      tags:
        key1: val1
      vaultName: swaggerExample

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dataprotection:BackupVault swaggerExample /subscriptions/0b352192-dcac-4cc7-992e-a96190ccc68c/resourceGroups/SampleResourceGroup/providers/Microsoft.DataProtection/Backupvaults/swaggerExample 
```
