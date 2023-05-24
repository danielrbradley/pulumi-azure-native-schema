Migration item.
API Version: 2023-02-01.
Previous API Version: 2018-07-10. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Enables migration.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replicationMigrationItem = new AzureNative.RecoveryServices.ReplicationMigrationItem("replicationMigrationItem", new()
    {
        FabricName = "vmwarefabric1",
        MigrationItemName = "virtualmachine1",
        Properties = new AzureNative.RecoveryServices.Inputs.EnableMigrationInputPropertiesArgs
        {
            PolicyId = "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.RecoveryServices/vaults/migrationvault/replicationPolicies/vmwarepolicy1",
            ProviderSpecificDetails = 
            {
                { "dataMoverRunAsAccountId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/runasaccounts/dataMoverRunAsAccount1" },
                { "disksToInclude", new[]
                {
                    new AzureNative.RecoveryServices.Inputs.VMwareCbtDiskInputArgs
                    {
                        DiskId = "disk1",
                        IsOSDisk = "true",
                        LogStorageAccountId = "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.Storage/storageAccounts/logStorageAccount1",
                        LogStorageAccountSasSecretName = "logStorageSas",
                    },
                } },
                { "instanceType", "VMwareCbt" },
                { "snapshotRunAsAccountId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/runasaccounts/snapshotRunAsAccount1" },
                { "targetNetworkId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.Network/virtualNetworks/virtualNetwork1" },
                { "targetResourceGroupId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1" },
                { "vmwareMachineId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/machines/virtualmachine1" },
            },
        },
        ProtectionContainerName = "vmwareContainer1",
        ResourceGroupName = "resourcegroup1",
        ResourceName = "migrationvault",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.recoveryservices.ReplicationMigrationItem;
import com.pulumi.azurenative.recoveryservices.ReplicationMigrationItemArgs;
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
        var replicationMigrationItem = new ReplicationMigrationItem("replicationMigrationItem", ReplicationMigrationItemArgs.builder()        
            .fabricName("vmwarefabric1")
            .migrationItemName("virtualmachine1")
            .properties(Map.ofEntries(
                Map.entry("policyId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.RecoveryServices/vaults/migrationvault/replicationPolicies/vmwarepolicy1"),
                Map.entry("providerSpecificDetails", Map.ofEntries(
                    Map.entry("dataMoverRunAsAccountId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/runasaccounts/dataMoverRunAsAccount1"),
                    Map.entry("disksToInclude", Map.ofEntries(
                        Map.entry("diskId", "disk1"),
                        Map.entry("isOSDisk", "true"),
                        Map.entry("logStorageAccountId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.Storage/storageAccounts/logStorageAccount1"),
                        Map.entry("logStorageAccountSasSecretName", "logStorageSas")
                    )),
                    Map.entry("instanceType", "VMwareCbt"),
                    Map.entry("snapshotRunAsAccountId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/runasaccounts/snapshotRunAsAccount1"),
                    Map.entry("targetNetworkId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.Network/virtualNetworks/virtualNetwork1"),
                    Map.entry("targetResourceGroupId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1"),
                    Map.entry("vmwareMachineId", "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/machines/virtualmachine1")
                ))
            ))
            .protectionContainerName("vmwareContainer1")
            .resourceGroupName("resourcegroup1")
            .resourceName("migrationvault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replicationMigrationItem = new azure_native.recoveryservices.ReplicationMigrationItem("replicationMigrationItem", {
    fabricName: "vmwarefabric1",
    migrationItemName: "virtualmachine1",
    properties: {
        policyId: "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.RecoveryServices/vaults/migrationvault/replicationPolicies/vmwarepolicy1",
        providerSpecificDetails: {
            dataMoverRunAsAccountId: "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/runasaccounts/dataMoverRunAsAccount1",
            disksToInclude: [{
                diskId: "disk1",
                isOSDisk: "true",
                logStorageAccountId: "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.Storage/storageAccounts/logStorageAccount1",
                logStorageAccountSasSecretName: "logStorageSas",
            }],
            instanceType: "VMwareCbt",
            snapshotRunAsAccountId: "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/runasaccounts/snapshotRunAsAccount1",
            targetNetworkId: "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.Network/virtualNetworks/virtualNetwork1",
            targetResourceGroupId: "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1",
            vmwareMachineId: "/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/machines/virtualmachine1",
        },
    },
    protectionContainerName: "vmwareContainer1",
    resourceGroupName: "resourcegroup1",
    resourceName: "migrationvault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replication_migration_item = azure_native.recoveryservices.ReplicationMigrationItem("replicationMigrationItem",
    fabric_name="vmwarefabric1",
    migration_item_name="virtualmachine1",
    properties=azure_native.recoveryservices.MigrationItemPropertiesResponseArgs(
        policy_id="/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.RecoveryServices/vaults/migrationvault/replicationPolicies/vmwarepolicy1",
        provider_specific_details=azure_native.recoveryservices.VMwareCbtMigrationDetailsResponseArgs(
            data_mover_run_as_account_id="/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/runasaccounts/dataMoverRunAsAccount1",
            disks_to_include=[azure_native.recoveryservices.VMwareCbtDiskInputArgs(
                disk_id="disk1",
                is_os_disk="true",
                log_storage_account_id="/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.Storage/storageAccounts/logStorageAccount1",
                log_storage_account_sas_secret_name="logStorageSas",
            )],
            instance_type="VMwareCbt",
            snapshot_run_as_account_id="/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/runasaccounts/snapshotRunAsAccount1",
            target_network_id="/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.Network/virtualNetworks/virtualNetwork1",
            target_resource_group_id="/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1",
            vmware_machine_id="/Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/machines/virtualmachine1",
        ),
    ),
    protection_container_name="vmwareContainer1",
    resource_group_name="resourcegroup1",
    resource_name_="migrationvault")

```

```yaml
resources:
  replicationMigrationItem:
    type: azure-native:recoveryservices:ReplicationMigrationItem
    properties:
      fabricName: vmwarefabric1
      migrationItemName: virtualmachine1
      properties:
        policyId: /Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.RecoveryServices/vaults/migrationvault/replicationPolicies/vmwarepolicy1
        providerSpecificDetails:
          dataMoverRunAsAccountId: /Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/runasaccounts/dataMoverRunAsAccount1
          disksToInclude:
            - diskId: disk1
              isOSDisk: 'true'
              logStorageAccountId: /Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.Storage/storageAccounts/logStorageAccount1
              logStorageAccountSasSecretName: logStorageSas
          instanceType: VMwareCbt
          snapshotRunAsAccountId: /Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/runasaccounts/snapshotRunAsAccount1
          targetNetworkId: /Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.Network/virtualNetworks/virtualNetwork1
          targetResourceGroupId: /Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1
          vmwareMachineId: /Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.OffAzure/VMwareSites/vmwaresite1/machines/virtualmachine1
      protectionContainerName: vmwareContainer1
      resourceGroupName: resourcegroup1
      resourceName: migrationvault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ReplicationMigrationItem virtualmachine1 /Subscriptions/cb53d0c3-bd59-4721-89bc-06916a9147ef/resourceGroups/resourcegroup1/providers/Microsoft.RecoveryServices/vaults/migrationvault/replicationFabrics/vmwarefabric1/replicationProtectionContainers/vmwareContainer1/replicationMigrationItems/virtualmachine1 
```
