Replication protected item.
API Version: 2023-02-01.
Previous API Version: 2018-07-10. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Enables protection.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replicationProtectedItem = new AzureNative.RecoveryServices.ReplicationProtectedItem("replicationProtectedItem", new()
    {
        FabricName = "cloud1",
        Properties = new AzureNative.RecoveryServices.Inputs.EnableProtectionInputPropertiesArgs
        {
            PolicyId = "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationPolicies/protectionprofile1",
            ProtectableItemId = "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectableItems/f8491e4f-817a-40dd-a90c-af773978c75b",
            ProviderSpecificDetails = new AzureNative.RecoveryServices.Inputs.HyperVReplicaAzureEnableProtectionInputArgs
            {
                InstanceType = "HyperVReplicaAzure",
            },
        },
        ProtectionContainerName = "cloud_6d224fc6-f326-5d35-96de-fbf51efb3179",
        ReplicatedProtectedItemName = "f8491e4f-817a-40dd-a90c-af773978c75b",
        ResourceGroupName = "resourceGroupPS1",
        ResourceName = "vault1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.recoveryservices.ReplicationProtectedItem;
import com.pulumi.azurenative.recoveryservices.ReplicationProtectedItemArgs;
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
        var replicationProtectedItem = new ReplicationProtectedItem("replicationProtectedItem", ReplicationProtectedItemArgs.builder()        
            .fabricName("cloud1")
            .properties(Map.ofEntries(
                Map.entry("policyId", "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationPolicies/protectionprofile1"),
                Map.entry("protectableItemId", "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectableItems/f8491e4f-817a-40dd-a90c-af773978c75b"),
                Map.entry("providerSpecificDetails", Map.of("instanceType", "HyperVReplicaAzure"))
            ))
            .protectionContainerName("cloud_6d224fc6-f326-5d35-96de-fbf51efb3179")
            .replicatedProtectedItemName("f8491e4f-817a-40dd-a90c-af773978c75b")
            .resourceGroupName("resourceGroupPS1")
            .resourceName("vault1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replicationProtectedItem = new azure_native.recoveryservices.ReplicationProtectedItem("replicationProtectedItem", {
    fabricName: "cloud1",
    properties: {
        policyId: "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationPolicies/protectionprofile1",
        protectableItemId: "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectableItems/f8491e4f-817a-40dd-a90c-af773978c75b",
        providerSpecificDetails: {
            instanceType: "HyperVReplicaAzure",
        },
    },
    protectionContainerName: "cloud_6d224fc6-f326-5d35-96de-fbf51efb3179",
    replicatedProtectedItemName: "f8491e4f-817a-40dd-a90c-af773978c75b",
    resourceGroupName: "resourceGroupPS1",
    resourceName: "vault1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replication_protected_item = azure_native.recoveryservices.ReplicationProtectedItem("replicationProtectedItem",
    fabric_name="cloud1",
    properties=azure_native.recoveryservices.ReplicationProtectedItemPropertiesResponseArgs(
        policy_id="/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationPolicies/protectionprofile1",
        protectable_item_id="/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectableItems/f8491e4f-817a-40dd-a90c-af773978c75b",
        provider_specific_details=azure_native.recoveryservices.HyperVReplicaAzureEnableProtectionInputArgs(
            instance_type="HyperVReplicaAzure",
        ),
    ),
    protection_container_name="cloud_6d224fc6-f326-5d35-96de-fbf51efb3179",
    replicated_protected_item_name="f8491e4f-817a-40dd-a90c-af773978c75b",
    resource_group_name="resourceGroupPS1",
    resource_name_="vault1")

```

```yaml
resources:
  replicationProtectedItem:
    type: azure-native:recoveryservices:ReplicationProtectedItem
    properties:
      fabricName: cloud1
      properties:
        policyId: /Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationPolicies/protectionprofile1
        protectableItemId: /Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectableItems/f8491e4f-817a-40dd-a90c-af773978c75b
        providerSpecificDetails:
          instanceType: HyperVReplicaAzure
      protectionContainerName: cloud_6d224fc6-f326-5d35-96de-fbf51efb3179
      replicatedProtectedItemName: f8491e4f-817a-40dd-a90c-af773978c75b
      resourceGroupName: resourceGroupPS1
      resourceName: vault1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ReplicationProtectedItem f8491e4f-817a-40dd-a90c-af773978c75b /Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectedItems/f8491e4f-817a-40dd-a90c-af773978c75b 
```
