Recovery plan details.
API Version: 2023-02-01.
Previous API Version: 2018-07-10. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates a recovery plan with the given details.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replicationRecoveryPlan = new AzureNative.RecoveryServices.ReplicationRecoveryPlan("replicationRecoveryPlan", new()
    {
        Properties = new AzureNative.RecoveryServices.Inputs.CreateRecoveryPlanInputPropertiesArgs
        {
            FailoverDeploymentModel = "ResourceManager",
            Groups = new[]
            {
                new AzureNative.RecoveryServices.Inputs.RecoveryPlanGroupArgs
                {
                    EndGroupActions = new[] {},
                    GroupType = "Boot",
                    ReplicationProtectedItems = new[]
                    {
                        new AzureNative.RecoveryServices.Inputs.RecoveryPlanProtectedItemArgs
                        {
                            Id = "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectedItems/f8491e4f-817a-40dd-a90c-af773978c75b",
                            VirtualMachineId = "f8491e4f-817a-40dd-a90c-af773978c75b",
                        },
                    },
                    StartGroupActions = new[] {},
                },
            },
            PrimaryFabricId = "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1",
            RecoveryFabricId = "Microsoft Azure",
        },
        RecoveryPlanName = "RPtest1",
        ResourceGroupName = "resourceGroupPS1",
        ResourceName = "vault1",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewReplicationRecoveryPlan(ctx, "replicationRecoveryPlan", &recoveryservices.ReplicationRecoveryPlanArgs{
			Properties: recoveryservices.RecoveryPlanPropertiesResponse{
				FailoverDeploymentModel: pulumi.String("ResourceManager"),
				Groups: []recoveryservices.RecoveryPlanGroupArgs{
					{
						EndGroupActions: recoveryservices.RecoveryPlanActionArray{},
						GroupType:       pulumi.String("Boot"),
						ReplicationProtectedItems: recoveryservices.RecoveryPlanProtectedItemArray{
							{
								Id:               pulumi.String("/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectedItems/f8491e4f-817a-40dd-a90c-af773978c75b"),
								VirtualMachineId: pulumi.String("f8491e4f-817a-40dd-a90c-af773978c75b"),
							},
						},
						StartGroupActions: recoveryservices.RecoveryPlanActionArray{},
					},
				},
				PrimaryFabricId:  pulumi.String("/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1"),
				RecoveryFabricId: pulumi.String("Microsoft Azure"),
			},
			RecoveryPlanName:  pulumi.String("RPtest1"),
			ResourceGroupName: pulumi.String("resourceGroupPS1"),
			ResourceName:      pulumi.String("vault1"),
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
import com.pulumi.azurenative.recoveryservices.ReplicationRecoveryPlan;
import com.pulumi.azurenative.recoveryservices.ReplicationRecoveryPlanArgs;
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
        var replicationRecoveryPlan = new ReplicationRecoveryPlan("replicationRecoveryPlan", ReplicationRecoveryPlanArgs.builder()        
            .properties(Map.ofEntries(
                Map.entry("failoverDeploymentModel", "ResourceManager"),
                Map.entry("groups", Map.ofEntries(
                    Map.entry("endGroupActions", ),
                    Map.entry("groupType", "Boot"),
                    Map.entry("replicationProtectedItems", Map.ofEntries(
                        Map.entry("id", "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectedItems/f8491e4f-817a-40dd-a90c-af773978c75b"),
                        Map.entry("virtualMachineId", "f8491e4f-817a-40dd-a90c-af773978c75b")
                    )),
                    Map.entry("startGroupActions", )
                )),
                Map.entry("primaryFabricId", "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1"),
                Map.entry("recoveryFabricId", "Microsoft Azure")
            ))
            .recoveryPlanName("RPtest1")
            .resourceGroupName("resourceGroupPS1")
            .resourceName("vault1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replicationRecoveryPlan = new azure_native.recoveryservices.ReplicationRecoveryPlan("replicationRecoveryPlan", {
    properties: {
        failoverDeploymentModel: "ResourceManager",
        groups: [{
            endGroupActions: [],
            groupType: "Boot",
            replicationProtectedItems: [{
                id: "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectedItems/f8491e4f-817a-40dd-a90c-af773978c75b",
                virtualMachineId: "f8491e4f-817a-40dd-a90c-af773978c75b",
            }],
            startGroupActions: [],
        }],
        primaryFabricId: "/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1",
        recoveryFabricId: "Microsoft Azure",
    },
    recoveryPlanName: "RPtest1",
    resourceGroupName: "resourceGroupPS1",
    resourceName: "vault1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replication_recovery_plan = azure_native.recoveryservices.ReplicationRecoveryPlan("replicationRecoveryPlan",
    properties=azure_native.recoveryservices.RecoveryPlanPropertiesResponseArgs(
        failover_deployment_model="ResourceManager",
        groups=[{
            "endGroupActions": [],
            "groupType": "Boot",
            "replicationProtectedItems": [azure_native.recoveryservices.RecoveryPlanProtectedItemArgs(
                id="/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectedItems/f8491e4f-817a-40dd-a90c-af773978c75b",
                virtual_machine_id="f8491e4f-817a-40dd-a90c-af773978c75b",
            )],
            "startGroupActions": [],
        }],
        primary_fabric_id="/Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1",
        recovery_fabric_id="Microsoft Azure",
    ),
    recovery_plan_name="RPtest1",
    resource_group_name="resourceGroupPS1",
    resource_name_="vault1")

```

```yaml
resources:
  replicationRecoveryPlan:
    type: azure-native:recoveryservices:ReplicationRecoveryPlan
    properties:
      properties:
        failoverDeploymentModel: ResourceManager
        groups:
          - endGroupActions: []
            groupType: Boot
            replicationProtectedItems:
              - id: /Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1/replicationProtectionContainers/cloud_6d224fc6-f326-5d35-96de-fbf51efb3179/replicationProtectedItems/f8491e4f-817a-40dd-a90c-af773978c75b
                virtualMachineId: f8491e4f-817a-40dd-a90c-af773978c75b
            startGroupActions: []
        primaryFabricId: /Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1
        recoveryFabricId: Microsoft Azure
      recoveryPlanName: RPtest1
      resourceGroupName: resourceGroupPS1
      resourceName: vault1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ReplicationRecoveryPlan RPtest1 /Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationRecoveryPlans/RPtest1 
```
