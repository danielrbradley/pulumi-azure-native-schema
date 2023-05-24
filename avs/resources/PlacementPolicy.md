A vSphere Distributed Resource Scheduler (DRS) placement policy
API Version: 2022-05-01.
Previous API Version: 2021-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PlacementPolicies_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var placementPolicy = new AzureNative.AVS.PlacementPolicy("placementPolicy", new()
    {
        ClusterName = "cluster1",
        PlacementPolicyName = "policy1",
        PrivateCloudName = "cloud1",
        Properties = new AzureNative.AVS.Inputs.VmHostPlacementPolicyPropertiesArgs
        {
            AffinityStrength = "Must",
            AffinityType = "AntiAffinity",
            AzureHybridBenefitType = "SqlHost",
            HostMembers = new[]
            {
                "fakehost22.nyc1.kubernetes.center",
                "fakehost23.nyc1.kubernetes.center",
                "fakehost24.nyc1.kubernetes.center",
            },
            Type = "VmHost",
            VmMembers = new[]
            {
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-128",
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-256",
            },
        },
        ResourceGroupName = "group1",
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewPlacementPolicy(ctx, "placementPolicy", &avs.PlacementPolicyArgs{
			ClusterName:         pulumi.String("cluster1"),
			PlacementPolicyName: pulumi.String("policy1"),
			PrivateCloudName:    pulumi.String("cloud1"),
			Properties: avs.VmHostPlacementPolicyProperties{
				AffinityStrength:       "Must",
				AffinityType:           "AntiAffinity",
				AzureHybridBenefitType: "SqlHost",
				HostMembers: []string{
					"fakehost22.nyc1.kubernetes.center",
					"fakehost23.nyc1.kubernetes.center",
					"fakehost24.nyc1.kubernetes.center",
				},
				Type: "VmHost",
				VmMembers: []string{
					"/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-128",
					"/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-256",
				},
			},
			ResourceGroupName: pulumi.String("group1"),
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
import com.pulumi.azurenative.avs.PlacementPolicy;
import com.pulumi.azurenative.avs.PlacementPolicyArgs;
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
        var placementPolicy = new PlacementPolicy("placementPolicy", PlacementPolicyArgs.builder()        
            .clusterName("cluster1")
            .placementPolicyName("policy1")
            .privateCloudName("cloud1")
            .properties(Map.ofEntries(
                Map.entry("affinityStrength", "Must"),
                Map.entry("affinityType", "AntiAffinity"),
                Map.entry("azureHybridBenefitType", "SqlHost"),
                Map.entry("hostMembers",                 
                    "fakehost22.nyc1.kubernetes.center",
                    "fakehost23.nyc1.kubernetes.center",
                    "fakehost24.nyc1.kubernetes.center"),
                Map.entry("type", "VmHost"),
                Map.entry("vmMembers",                 
                    "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-128",
                    "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-256")
            ))
            .resourceGroupName("group1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const placementPolicy = new azure_native.avs.PlacementPolicy("placementPolicy", {
    clusterName: "cluster1",
    placementPolicyName: "policy1",
    privateCloudName: "cloud1",
    properties: {
        affinityStrength: "Must",
        affinityType: "AntiAffinity",
        azureHybridBenefitType: "SqlHost",
        hostMembers: [
            "fakehost22.nyc1.kubernetes.center",
            "fakehost23.nyc1.kubernetes.center",
            "fakehost24.nyc1.kubernetes.center",
        ],
        type: "VmHost",
        vmMembers: [
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-128",
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-256",
        ],
    },
    resourceGroupName: "group1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

placement_policy = azure_native.avs.PlacementPolicy("placementPolicy",
    cluster_name="cluster1",
    placement_policy_name="policy1",
    private_cloud_name="cloud1",
    properties=azure_native.avs.VmHostPlacementPolicyPropertiesArgs(
        affinity_strength="Must",
        affinity_type="AntiAffinity",
        azure_hybrid_benefit_type="SqlHost",
        host_members=[
            "fakehost22.nyc1.kubernetes.center",
            "fakehost23.nyc1.kubernetes.center",
            "fakehost24.nyc1.kubernetes.center",
        ],
        type="VmHost",
        vm_members=[
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-128",
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-256",
        ],
    ),
    resource_group_name="group1")

```

```yaml
resources:
  placementPolicy:
    type: azure-native:avs:PlacementPolicy
    properties:
      clusterName: cluster1
      placementPolicyName: policy1
      privateCloudName: cloud1
      properties:
        affinityStrength: Must
        affinityType: AntiAffinity
        azureHybridBenefitType: SqlHost
        hostMembers:
          - fakehost22.nyc1.kubernetes.center
          - fakehost23.nyc1.kubernetes.center
          - fakehost24.nyc1.kubernetes.center
        type: VmHost
        vmMembers:
          - /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-128
          - /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/virtualMachines/vm-256
      resourceGroupName: group1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:PlacementPolicy policy1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/placementPolicies/policy1 
```
