Resource representation of a workflow
API Version: 2022-04-01-preview.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Workflow
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workflow = new AzureNative.DevHub.Workflow("workflow", new()
    {
        Acr = new AzureNative.DevHub.Inputs.ACRArgs
        {
            AcrRegistryName = "registry1",
            AcrRepositoryName = "repo1",
            AcrResourceGroup = "resourceGroup1",
            AcrSubscriptionId = "subscriptionId1",
        },
        AksResourceId = "/subscriptions/subscriptionId1/resourcegroups/resourceGroup1/providers/Microsoft.ContainerService/managedClusters/cluster1",
        BranchName = "branch1",
        DeploymentProperties = new AzureNative.DevHub.Inputs.DeploymentPropertiesArgs
        {
            KubeManifestLocations = new[]
            {
                "/src/manifests/",
            },
            ManifestType = "kube",
            Overrides = 
            {
                { "key1", "value1" },
            },
        },
        DockerBuildContext = "repo1/src/",
        Dockerfile = "repo1/images/Dockerfile",
        Location = "location1",
        OidcCredentials = new AzureNative.DevHub.Inputs.GitHubWorkflowProfileOidcCredentialsArgs
        {
            AzureClientId = "12345678-3456-7890-5678-012345678901",
            AzureTenantId = "66666666-3456-7890-5678-012345678901",
        },
        RepositoryName = "repo1",
        RepositoryOwner = "owner1",
        ResourceGroupName = "resourceGroup1",
        Tags = 
        {
            { "appname", "testApp" },
        },
        WorkflowName = "workflow1",
    });

});


```

```go
package main

import (
	devhub "github.com/pulumi/pulumi-azure-native-sdk/devhub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devhub.NewWorkflow(ctx, "workflow", &devhub.WorkflowArgs{
			Acr: &devhub.ACRArgs{
				AcrRegistryName:   pulumi.String("registry1"),
				AcrRepositoryName: pulumi.String("repo1"),
				AcrResourceGroup:  pulumi.String("resourceGroup1"),
				AcrSubscriptionId: pulumi.String("subscriptionId1"),
			},
			AksResourceId: pulumi.String("/subscriptions/subscriptionId1/resourcegroups/resourceGroup1/providers/Microsoft.ContainerService/managedClusters/cluster1"),
			BranchName:    pulumi.String("branch1"),
			DeploymentProperties: &devhub.DeploymentPropertiesArgs{
				KubeManifestLocations: pulumi.StringArray{
					pulumi.String("/src/manifests/"),
				},
				ManifestType: pulumi.String("kube"),
				Overrides: pulumi.StringMap{
					"key1": pulumi.String("value1"),
				},
			},
			DockerBuildContext: pulumi.String("repo1/src/"),
			Dockerfile:         pulumi.String("repo1/images/Dockerfile"),
			Location:           pulumi.String("location1"),
			OidcCredentials: &devhub.GitHubWorkflowProfileOidcCredentialsArgs{
				AzureClientId: pulumi.String("12345678-3456-7890-5678-012345678901"),
				AzureTenantId: pulumi.String("66666666-3456-7890-5678-012345678901"),
			},
			RepositoryName:    pulumi.String("repo1"),
			RepositoryOwner:   pulumi.String("owner1"),
			ResourceGroupName: pulumi.String("resourceGroup1"),
			Tags: pulumi.StringMap{
				"appname": pulumi.String("testApp"),
			},
			WorkflowName: pulumi.String("workflow1"),
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
import com.pulumi.azurenative.devhub.Workflow;
import com.pulumi.azurenative.devhub.WorkflowArgs;
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
        var workflow = new Workflow("workflow", WorkflowArgs.builder()        
            .acr(Map.ofEntries(
                Map.entry("acrRegistryName", "registry1"),
                Map.entry("acrRepositoryName", "repo1"),
                Map.entry("acrResourceGroup", "resourceGroup1"),
                Map.entry("acrSubscriptionId", "subscriptionId1")
            ))
            .aksResourceId("/subscriptions/subscriptionId1/resourcegroups/resourceGroup1/providers/Microsoft.ContainerService/managedClusters/cluster1")
            .branchName("branch1")
            .deploymentProperties(Map.ofEntries(
                Map.entry("kubeManifestLocations", "/src/manifests/"),
                Map.entry("manifestType", "kube"),
                Map.entry("overrides", Map.of("key1", "value1"))
            ))
            .dockerBuildContext("repo1/src/")
            .dockerfile("repo1/images/Dockerfile")
            .location("location1")
            .oidcCredentials(Map.ofEntries(
                Map.entry("azureClientId", "12345678-3456-7890-5678-012345678901"),
                Map.entry("azureTenantId", "66666666-3456-7890-5678-012345678901")
            ))
            .repositoryName("repo1")
            .repositoryOwner("owner1")
            .resourceGroupName("resourceGroup1")
            .tags(Map.of("appname", "testApp"))
            .workflowName("workflow1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workflow = new azure_native.devhub.Workflow("workflow", {
    acr: {
        acrRegistryName: "registry1",
        acrRepositoryName: "repo1",
        acrResourceGroup: "resourceGroup1",
        acrSubscriptionId: "subscriptionId1",
    },
    aksResourceId: "/subscriptions/subscriptionId1/resourcegroups/resourceGroup1/providers/Microsoft.ContainerService/managedClusters/cluster1",
    branchName: "branch1",
    deploymentProperties: {
        kubeManifestLocations: ["/src/manifests/"],
        manifestType: "kube",
        overrides: {
            key1: "value1",
        },
    },
    dockerBuildContext: "repo1/src/",
    dockerfile: "repo1/images/Dockerfile",
    location: "location1",
    oidcCredentials: {
        azureClientId: "12345678-3456-7890-5678-012345678901",
        azureTenantId: "66666666-3456-7890-5678-012345678901",
    },
    repositoryName: "repo1",
    repositoryOwner: "owner1",
    resourceGroupName: "resourceGroup1",
    tags: {
        appname: "testApp",
    },
    workflowName: "workflow1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workflow = azure_native.devhub.Workflow("workflow",
    acr=azure_native.devhub.ACRArgs(
        acr_registry_name="registry1",
        acr_repository_name="repo1",
        acr_resource_group="resourceGroup1",
        acr_subscription_id="subscriptionId1",
    ),
    aks_resource_id="/subscriptions/subscriptionId1/resourcegroups/resourceGroup1/providers/Microsoft.ContainerService/managedClusters/cluster1",
    branch_name="branch1",
    deployment_properties=azure_native.devhub.DeploymentPropertiesArgs(
        kube_manifest_locations=["/src/manifests/"],
        manifest_type="kube",
        overrides={
            "key1": "value1",
        },
    ),
    docker_build_context="repo1/src/",
    dockerfile="repo1/images/Dockerfile",
    location="location1",
    oidc_credentials=azure_native.devhub.GitHubWorkflowProfileOidcCredentialsArgs(
        azure_client_id="12345678-3456-7890-5678-012345678901",
        azure_tenant_id="66666666-3456-7890-5678-012345678901",
    ),
    repository_name="repo1",
    repository_owner="owner1",
    resource_group_name="resourceGroup1",
    tags={
        "appname": "testApp",
    },
    workflow_name="workflow1")

```

```yaml
resources:
  workflow:
    type: azure-native:devhub:Workflow
    properties:
      acr:
        acrRegistryName: registry1
        acrRepositoryName: repo1
        acrResourceGroup: resourceGroup1
        acrSubscriptionId: subscriptionId1
      aksResourceId: /subscriptions/subscriptionId1/resourcegroups/resourceGroup1/providers/Microsoft.ContainerService/managedClusters/cluster1
      branchName: branch1
      deploymentProperties:
        kubeManifestLocations:
          - /src/manifests/
        manifestType: kube
        overrides:
          key1: value1
      dockerBuildContext: repo1/src/
      dockerfile: repo1/images/Dockerfile
      location: location1
      oidcCredentials:
        azureClientId: 12345678-3456-7890-5678-012345678901
        azureTenantId: 66666666-3456-7890-5678-012345678901
      repositoryName: repo1
      repositoryOwner: owner1
      resourceGroupName: resourceGroup1
      tags:
        appname: testApp
      workflowName: workflow1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devhub:Workflow workflow1 /subscription/subscriptionId1/resourceGroups/resourceGroup1/providers/Microsoft.DevHub/workflow/workflow1 
```
