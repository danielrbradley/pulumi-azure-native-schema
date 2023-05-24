Protection profile details.
API Version: 2023-02-01.
Previous API Version: 2018-07-10. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates the policy.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replicationPolicy = new AzureNative.RecoveryServices.ReplicationPolicy("replicationPolicy", new()
    {
        PolicyName = "protectionprofile1",
        Properties = new AzureNative.RecoveryServices.Inputs.CreatePolicyInputPropertiesArgs
        {
            ProviderSpecificInput = new AzureNative.RecoveryServices.Inputs.HyperVReplicaAzurePolicyInputArgs
            {
                InstanceType = "HyperVReplicaAzure",
            },
        },
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
import com.pulumi.azurenative.recoveryservices.ReplicationPolicy;
import com.pulumi.azurenative.recoveryservices.ReplicationPolicyArgs;
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
        var replicationPolicy = new ReplicationPolicy("replicationPolicy", ReplicationPolicyArgs.builder()        
            .policyName("protectionprofile1")
            .properties(Map.of("providerSpecificInput", Map.of("instanceType", "HyperVReplicaAzure")))
            .resourceGroupName("resourceGroupPS1")
            .resourceName("vault1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replicationPolicy = new azure_native.recoveryservices.ReplicationPolicy("replicationPolicy", {
    policyName: "protectionprofile1",
    properties: {
        providerSpecificInput: {
            instanceType: "HyperVReplicaAzure",
        },
    },
    resourceGroupName: "resourceGroupPS1",
    resourceName: "vault1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replication_policy = azure_native.recoveryservices.ReplicationPolicy("replicationPolicy",
    policy_name="protectionprofile1",
    properties=azure_native.recoveryservices.PolicyPropertiesResponseArgs(
        provider_specific_input=azure_native.recoveryservices.HyperVReplicaAzurePolicyInputArgs(
            instance_type="HyperVReplicaAzure",
        ),
    ),
    resource_group_name="resourceGroupPS1",
    resource_name_="vault1")

```

```yaml
resources:
  replicationPolicy:
    type: azure-native:recoveryservices:ReplicationPolicy
    properties:
      policyName: protectionprofile1
      properties:
        providerSpecificInput:
          instanceType: HyperVReplicaAzure
      resourceGroupName: resourceGroupPS1
      resourceName: vault1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ReplicationPolicy protectionprofile1 /Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationPolicies/protectionprofile1 
```
