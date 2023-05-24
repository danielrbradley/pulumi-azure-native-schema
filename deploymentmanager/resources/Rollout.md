Defines the PUT rollout request body.
API Version: 2019-11-01-preview.
Previous API Version: 2019-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update rollout
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var rollout = new AzureNative.DeploymentManager.Rollout("rollout", new()
    {
        ArtifactSourceId = "/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/artifactSources/myArtifactSource",
        BuildVersion = "1.0.0.1",
        Identity = new AzureNative.DeploymentManager.Inputs.IdentityArgs
        {
            IdentityIds = new[]
            {
                "/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userassignedidentities/myuseridentity",
            },
            Type = "userAssigned",
        },
        Location = "centralus",
        ResourceGroupName = "myResourceGroup",
        RolloutName = "myRollout",
        StepGroups = new[]
        {
            new AzureNative.DeploymentManager.Inputs.StepGroupArgs
            {
                DeploymentTargetId = "Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit1'",
                Name = "FirstRegion",
                PostDeploymentSteps = new[]
                {
                    new AzureNative.DeploymentManager.Inputs.PrePostStepArgs
                    {
                        StepId = "Microsoft.DeploymentManager/steps/postDeployStep1",
                    },
                },
                PreDeploymentSteps = new[]
                {
                    new AzureNative.DeploymentManager.Inputs.PrePostStepArgs
                    {
                        StepId = "Microsoft.DeploymentManager/steps/preDeployStep1",
                    },
                    new AzureNative.DeploymentManager.Inputs.PrePostStepArgs
                    {
                        StepId = "Microsoft.DeploymentManager/steps/preDeployStep2",
                    },
                },
            },
            new AzureNative.DeploymentManager.Inputs.StepGroupArgs
            {
                DependsOnStepGroups = new[]
                {
                    "FirstRegion",
                },
                DeploymentTargetId = "Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit2'",
                Name = "SecondRegion",
                PostDeploymentSteps = new[]
                {
                    new AzureNative.DeploymentManager.Inputs.PrePostStepArgs
                    {
                        StepId = "Microsoft.DeploymentManager/steps/postDeployStep5",
                    },
                },
                PreDeploymentSteps = new[]
                {
                    new AzureNative.DeploymentManager.Inputs.PrePostStepArgs
                    {
                        StepId = "Microsoft.DeploymentManager/steps/preDeployStep3",
                    },
                    new AzureNative.DeploymentManager.Inputs.PrePostStepArgs
                    {
                        StepId = "Microsoft.DeploymentManager/steps/preDeployStep4",
                    },
                },
            },
        },
        Tags = null,
        TargetServiceTopologyId = "/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/serviceTopologies/myTopology",
    });

});


```

```go
package main

import (
	deploymentmanager "github.com/pulumi/pulumi-azure-native-sdk/deploymentmanager"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := deploymentmanager.NewRollout(ctx, "rollout", &deploymentmanager.RolloutArgs{
			ArtifactSourceId: pulumi.String("/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/artifactSources/myArtifactSource"),
			BuildVersion:     pulumi.String("1.0.0.1"),
			Identity: &deploymentmanager.IdentityArgs{
				IdentityIds: pulumi.StringArray{
					pulumi.String("/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userassignedidentities/myuseridentity"),
				},
				Type: pulumi.String("userAssigned"),
			},
			Location:          pulumi.String("centralus"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			RolloutName:       pulumi.String("myRollout"),
			StepGroups: []deploymentmanager.StepGroupArgs{
				{
					DeploymentTargetId: pulumi.String("Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit1'"),
					Name:               pulumi.String("FirstRegion"),
					PostDeploymentSteps: deploymentmanager.PrePostStepArray{
						{
							StepId: pulumi.String("Microsoft.DeploymentManager/steps/postDeployStep1"),
						},
					},
					PreDeploymentSteps: deploymentmanager.PrePostStepArray{
						{
							StepId: pulumi.String("Microsoft.DeploymentManager/steps/preDeployStep1"),
						},
						{
							StepId: pulumi.String("Microsoft.DeploymentManager/steps/preDeployStep2"),
						},
					},
				},
				{
					DependsOnStepGroups: pulumi.StringArray{
						pulumi.String("FirstRegion"),
					},
					DeploymentTargetId: pulumi.String("Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit2'"),
					Name:               pulumi.String("SecondRegion"),
					PostDeploymentSteps: deploymentmanager.PrePostStepArray{
						{
							StepId: pulumi.String("Microsoft.DeploymentManager/steps/postDeployStep5"),
						},
					},
					PreDeploymentSteps: deploymentmanager.PrePostStepArray{
						{
							StepId: pulumi.String("Microsoft.DeploymentManager/steps/preDeployStep3"),
						},
						{
							StepId: pulumi.String("Microsoft.DeploymentManager/steps/preDeployStep4"),
						},
					},
				},
			},
			Tags:                    nil,
			TargetServiceTopologyId: pulumi.String("/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/serviceTopologies/myTopology"),
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
import com.pulumi.azurenative.deploymentmanager.Rollout;
import com.pulumi.azurenative.deploymentmanager.RolloutArgs;
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
        var rollout = new Rollout("rollout", RolloutArgs.builder()        
            .artifactSourceId("/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/artifactSources/myArtifactSource")
            .buildVersion("1.0.0.1")
            .identity(Map.ofEntries(
                Map.entry("identityIds", "/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userassignedidentities/myuseridentity"),
                Map.entry("type", "userAssigned")
            ))
            .location("centralus")
            .resourceGroupName("myResourceGroup")
            .rolloutName("myRollout")
            .stepGroups(            
                Map.ofEntries(
                    Map.entry("deploymentTargetId", "Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit1'"),
                    Map.entry("name", "FirstRegion"),
                    Map.entry("postDeploymentSteps", Map.of("stepId", "Microsoft.DeploymentManager/steps/postDeployStep1")),
                    Map.entry("preDeploymentSteps",                     
                        Map.of("stepId", "Microsoft.DeploymentManager/steps/preDeployStep1"),
                        Map.of("stepId", "Microsoft.DeploymentManager/steps/preDeployStep2"))
                ),
                Map.ofEntries(
                    Map.entry("dependsOnStepGroups", "FirstRegion"),
                    Map.entry("deploymentTargetId", "Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit2'"),
                    Map.entry("name", "SecondRegion"),
                    Map.entry("postDeploymentSteps", Map.of("stepId", "Microsoft.DeploymentManager/steps/postDeployStep5")),
                    Map.entry("preDeploymentSteps",                     
                        Map.of("stepId", "Microsoft.DeploymentManager/steps/preDeployStep3"),
                        Map.of("stepId", "Microsoft.DeploymentManager/steps/preDeployStep4"))
                ))
            .tags()
            .targetServiceTopologyId("/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/serviceTopologies/myTopology")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const rollout = new azure_native.deploymentmanager.Rollout("rollout", {
    artifactSourceId: "/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/artifactSources/myArtifactSource",
    buildVersion: "1.0.0.1",
    identity: {
        identityIds: ["/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userassignedidentities/myuseridentity"],
        type: "userAssigned",
    },
    location: "centralus",
    resourceGroupName: "myResourceGroup",
    rolloutName: "myRollout",
    stepGroups: [
        {
            deploymentTargetId: "Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit1'",
            name: "FirstRegion",
            postDeploymentSteps: [{
                stepId: "Microsoft.DeploymentManager/steps/postDeployStep1",
            }],
            preDeploymentSteps: [
                {
                    stepId: "Microsoft.DeploymentManager/steps/preDeployStep1",
                },
                {
                    stepId: "Microsoft.DeploymentManager/steps/preDeployStep2",
                },
            ],
        },
        {
            dependsOnStepGroups: ["FirstRegion"],
            deploymentTargetId: "Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit2'",
            name: "SecondRegion",
            postDeploymentSteps: [{
                stepId: "Microsoft.DeploymentManager/steps/postDeployStep5",
            }],
            preDeploymentSteps: [
                {
                    stepId: "Microsoft.DeploymentManager/steps/preDeployStep3",
                },
                {
                    stepId: "Microsoft.DeploymentManager/steps/preDeployStep4",
                },
            ],
        },
    ],
    tags: {},
    targetServiceTopologyId: "/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/serviceTopologies/myTopology",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

rollout = azure_native.deploymentmanager.Rollout("rollout",
    artifact_source_id="/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/artifactSources/myArtifactSource",
    build_version="1.0.0.1",
    identity=azure_native.deploymentmanager.IdentityArgs(
        identity_ids=["/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userassignedidentities/myuseridentity"],
        type="userAssigned",
    ),
    location="centralus",
    resource_group_name="myResourceGroup",
    rollout_name="myRollout",
    step_groups=[
        {
            "deploymentTargetId": "Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit1'",
            "name": "FirstRegion",
            "postDeploymentSteps": [azure_native.deploymentmanager.PrePostStepArgs(
                step_id="Microsoft.DeploymentManager/steps/postDeployStep1",
            )],
            "preDeploymentSteps": [
                azure_native.deploymentmanager.PrePostStepArgs(
                    step_id="Microsoft.DeploymentManager/steps/preDeployStep1",
                ),
                azure_native.deploymentmanager.PrePostStepArgs(
                    step_id="Microsoft.DeploymentManager/steps/preDeployStep2",
                ),
            ],
        },
        {
            "dependsOnStepGroups": ["FirstRegion"],
            "deploymentTargetId": "Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit2'",
            "name": "SecondRegion",
            "postDeploymentSteps": [azure_native.deploymentmanager.PrePostStepArgs(
                step_id="Microsoft.DeploymentManager/steps/postDeployStep5",
            )],
            "preDeploymentSteps": [
                azure_native.deploymentmanager.PrePostStepArgs(
                    step_id="Microsoft.DeploymentManager/steps/preDeployStep3",
                ),
                azure_native.deploymentmanager.PrePostStepArgs(
                    step_id="Microsoft.DeploymentManager/steps/preDeployStep4",
                ),
            ],
        },
    ],
    tags={},
    target_service_topology_id="/subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/serviceTopologies/myTopology")

```

```yaml
resources:
  rollout:
    type: azure-native:deploymentmanager:Rollout
    properties:
      artifactSourceId: /subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/artifactSources/myArtifactSource
      buildVersion: 1.0.0.1
      identity:
        identityIds:
          - /subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userassignedidentities/myuseridentity
        type: userAssigned
      location: centralus
      resourceGroupName: myResourceGroup
      rolloutName: myRollout
      stepGroups:
        - deploymentTargetId: Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit1'
          name: FirstRegion
          postDeploymentSteps:
            - stepId: Microsoft.DeploymentManager/steps/postDeployStep1
          preDeploymentSteps:
            - stepId: Microsoft.DeploymentManager/steps/preDeployStep1
            - stepId: Microsoft.DeploymentManager/steps/preDeployStep2
        - dependsOnStepGroups:
            - FirstRegion
          deploymentTargetId: Microsoft.DeploymentManager/serviceTopologies/myTopology/services/myService/serviceUnits/myServiceUnit2'
          name: SecondRegion
          postDeploymentSteps:
            - stepId: Microsoft.DeploymentManager/steps/postDeployStep5
          preDeploymentSteps:
            - stepId: Microsoft.DeploymentManager/steps/preDeployStep3
            - stepId: Microsoft.DeploymentManager/steps/preDeployStep4
      tags: {}
      targetServiceTopologyId: /subscriptions/caac1590-e859-444f-a9e0-62091c0f5929/resourceGroups/myResourceGroup/Microsoft.DeploymentManager/serviceTopologies/myTopology

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:deploymentmanager:Rollout myRollout /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DeploymentManager/rollouts/{rolloutName} 
```
