Defines the move resource.
API Version: 2022-08-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### MoveResources_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var moveResource = new AzureNative.Migrate.MoveResource("moveResource", new()
    {
        MoveCollectionName = "movecollection1",
        MoveResourceName = "moveresourcename1",
        Properties = new AzureNative.Migrate.Inputs.MoveResourcePropertiesArgs
        {
            DependsOnOverrides = new[]
            {
                new AzureNative.Migrate.Inputs.MoveResourceDependencyOverrideArgs
                {
                    Id = "/subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/eastusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140",
                    TargetId = "/subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/westusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140",
                },
            },
            ResourceSettings = new AzureNative.Migrate.Inputs.VirtualMachineResourceSettingsArgs
            {
                ResourceType = "Microsoft.Compute/virtualMachines",
                TargetAvailabilitySetId = "/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/availabilitySets/avset1",
                TargetAvailabilityZone = "2",
                TargetResourceName = "westusvm1",
                UserManagedIdentities = new[]
                {
                    "/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.ManagedIdentity/userAssignedIdentities/umi1",
                },
            },
            SourceId = "/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/virtualMachines/eastusvm1",
        },
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	migrate "github.com/pulumi/pulumi-azure-native-sdk/migrate"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := migrate.NewMoveResource(ctx, "moveResource", &migrate.MoveResourceArgs{
			MoveCollectionName: pulumi.String("movecollection1"),
			MoveResourceName:   pulumi.String("moveresourcename1"),
			Properties: migrate.MoveResourcePropertiesResponse{
				DependsOnOverrides: migrate.MoveResourceDependencyOverrideArray{
					&migrate.MoveResourceDependencyOverrideArgs{
						Id:       pulumi.String("/subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/eastusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140"),
						TargetId: pulumi.String("/subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/westusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140"),
					},
				},
				ResourceSettings: migrate.VirtualMachineResourceSettings{
					ResourceType:            "Microsoft.Compute/virtualMachines",
					TargetAvailabilitySetId: "/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/availabilitySets/avset1",
					TargetAvailabilityZone:  "2",
					TargetResourceName:      "westusvm1",
					UserManagedIdentities: []string{
						"/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.ManagedIdentity/userAssignedIdentities/umi1",
					},
				},
				SourceId: pulumi.String("/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/virtualMachines/eastusvm1"),
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
import com.pulumi.azurenative.migrate.MoveResource;
import com.pulumi.azurenative.migrate.MoveResourceArgs;
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
        var moveResource = new MoveResource("moveResource", MoveResourceArgs.builder()        
            .moveCollectionName("movecollection1")
            .moveResourceName("moveresourcename1")
            .properties(Map.ofEntries(
                Map.entry("dependsOnOverrides", Map.ofEntries(
                    Map.entry("id", "/subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/eastusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140"),
                    Map.entry("targetId", "/subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/westusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140")
                )),
                Map.entry("resourceSettings", Map.ofEntries(
                    Map.entry("resourceType", "Microsoft.Compute/virtualMachines"),
                    Map.entry("targetAvailabilitySetId", "/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/availabilitySets/avset1"),
                    Map.entry("targetAvailabilityZone", "2"),
                    Map.entry("targetResourceName", "westusvm1"),
                    Map.entry("userManagedIdentities", "/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.ManagedIdentity/userAssignedIdentities/umi1")
                )),
                Map.entry("sourceId", "/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/virtualMachines/eastusvm1")
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const moveResource = new azure_native.migrate.MoveResource("moveResource", {
    moveCollectionName: "movecollection1",
    moveResourceName: "moveresourcename1",
    properties: {
        dependsOnOverrides: [{
            id: "/subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/eastusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140",
            targetId: "/subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/westusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140",
        }],
        resourceSettings: {
            resourceType: "Microsoft.Compute/virtualMachines",
            targetAvailabilitySetId: "/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/availabilitySets/avset1",
            targetAvailabilityZone: "2",
            targetResourceName: "westusvm1",
            userManagedIdentities: ["/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.ManagedIdentity/userAssignedIdentities/umi1"],
        },
        sourceId: "/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/virtualMachines/eastusvm1",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

move_resource = azure_native.migrate.MoveResource("moveResource",
    move_collection_name="movecollection1",
    move_resource_name="moveresourcename1",
    properties=azure_native.migrate.MoveResourcePropertiesResponseArgs(
        depends_on_overrides=[azure_native.migrate.MoveResourceDependencyOverrideArgs(
            id="/subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/eastusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140",
            target_id="/subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/westusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140",
        )],
        resource_settings=azure_native.migrate.VirtualMachineResourceSettingsArgs(
            resource_type="Microsoft.Compute/virtualMachines",
            target_availability_set_id="/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/availabilitySets/avset1",
            target_availability_zone="2",
            target_resource_name="westusvm1",
            user_managed_identities=["/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.ManagedIdentity/userAssignedIdentities/umi1"],
        ),
        source_id="/subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/virtualMachines/eastusvm1",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  moveResource:
    type: azure-native:migrate:MoveResource
    properties:
      moveCollectionName: movecollection1
      moveResourceName: moveresourcename1
      properties:
        dependsOnOverrides:
          - id: /subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/eastusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140
            targetId: /subscriptions/c4488a3f-a7f7-4ad4-aa72-0e1f4d9c0756/resourceGroups/westusRG/providers/Microsoft.Network/networkInterfaces/eastusvm140
        resourceSettings:
          resourceType: Microsoft.Compute/virtualMachines
          targetAvailabilitySetId: /subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/availabilitySets/avset1
          targetAvailabilityZone: '2'
          targetResourceName: westusvm1
          userManagedIdentities:
            - /subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.ManagedIdentity/userAssignedIdentities/umi1
        sourceId: /subscriptions/subid/resourceGroups/eastusRG/providers/Microsoft.Compute/virtualMachines/eastusvm1
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:MoveResource moveresourcename1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Migrate/MoveCollections/movecollection1/MoveResources/moveresource1 
```
