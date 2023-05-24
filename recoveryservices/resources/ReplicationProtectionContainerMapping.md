Protection container mapping object.
API Version: 2023-02-01.
Previous API Version: 2018-07-10. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create protection container mapping.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replicationProtectionContainerMapping = new AzureNative.RecoveryServices.ReplicationProtectionContainerMapping("replicationProtectionContainerMapping", new()
    {
        FabricName = "cloud1",
        MappingName = "cloud1protectionprofile1",
        Properties = new AzureNative.RecoveryServices.Inputs.CreateProtectionContainerMappingInputPropertiesArgs
        {
            PolicyId = "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationPolicies/protectionprofile1",
            ProviderSpecificInput = 
            {
                { "instanceType", "ReplicationProviderSpecificContainerMappingInput" },
            },
            TargetProtectionContainerId = "Microsoft Azure",
        },
        ProtectionContainerName = "cloud_6d224fc6-f326-5d35-96de-fbf51efb3179",
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
import com.pulumi.azurenative.recoveryservices.ReplicationProtectionContainerMapping;
import com.pulumi.azurenative.recoveryservices.ReplicationProtectionContainerMappingArgs;
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
        var replicationProtectionContainerMapping = new ReplicationProtectionContainerMapping("replicationProtectionContainerMapping", ReplicationProtectionContainerMappingArgs.builder()        
            .fabricName("cloud1")
            .mappingName("cloud1protectionprofile1")
            .properties(Map.ofEntries(
                Map.entry("policyId", "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationPolicies/protectionprofile1"),
                Map.entry("providerSpecificInput", Map.of("instanceType", "ReplicationProviderSpecificContainerMappingInput")),
                Map.entry("targetProtectionContainerId", "Microsoft Azure")
            ))
            .protectionContainerName("cloud_6d224fc6-f326-5d35-96de-fbf51efb3179")
            .resourceGroupName("resourceGroupPS1")
            .resourceName("vault1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replicationProtectionContainerMapping = new azure_native.recoveryservices.ReplicationProtectionContainerMapping("replicationProtectionContainerMapping", {
    fabricName: "cloud1",
    mappingName: "cloud1protectionprofile1",
    properties: {
        policyId: "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationPolicies/protectionprofile1",
        providerSpecificInput: {
            instanceType: "ReplicationProviderSpecificContainerMappingInput",
        },
        targetProtectionContainerId: "Microsoft Azure",
    },
    protectionContainerName: "cloud_6d224fc6-f326-5d35-96de-fbf51efb3179",
    resourceGroupName: "resourceGroupPS1",
    resourceName: "vault1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replication_protection_container_mapping = azure_native.recoveryservices.ReplicationProtectionContainerMapping("replicationProtectionContainerMapping",
    fabric_name="cloud1",
    mapping_name="cloud1protectionprofile1",
    properties=azure_native.recoveryservices.ProtectionContainerMappingPropertiesResponseArgs(
        policy_id="/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationPolicies/protectionprofile1",
        provider_specific_input={
            "instanceType": "ReplicationProviderSpecificContainerMappingInput",
        },
        target_protection_container_id="Microsoft Azure",
    ),
    protection_container_name="cloud_6d224fc6-f326-5d35-96de-fbf51efb3179",
    resource_group_name="resourceGroupPS1",
    resource_name_="vault1")

```

```yaml
resources:
  replicationProtectionContainerMapping:
    type: azure-native:recoveryservices:ReplicationProtectionContainerMapping
    properties:
      fabricName: cloud1
      mappingName: cloud1protectionprofile1
      properties:
        policyId: /Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationPolicies/protectionprofile1
        providerSpecificInput:
          instanceType: ReplicationProviderSpecificContainerMappingInput
        targetProtectionContainerId: Microsoft Azure
      protectionContainerName: cloud_6d224fc6-f326-5d35-96de-fbf51efb3179
      resourceGroupName: resourceGroupPS1
      resourceName: vault1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ReplicationProtectionContainerMapping cloud1protectionprofile1 /Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectionContainerMappings/cloud1protectionprofile1 
```
