The SourceControl Configuration object returned in Get & Put response.
API Version: 2022-11-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Source Control Configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sourceControlConfiguration = new AzureNative.KubernetesConfiguration.SourceControlConfiguration("sourceControlConfiguration", new()
    {
        ClusterName = "clusterName1",
        ClusterResourceName = "connectedClusters",
        ClusterRp = "Microsoft.Kubernetes",
        ConfigurationProtectedSettings = 
        {
            { "protectedSetting1Key", "protectedSetting1Value" },
        },
        EnableHelmOperator = true,
        HelmOperatorProperties = new AzureNative.KubernetesConfiguration.Inputs.HelmOperatorPropertiesArgs
        {
            ChartValues = "--set git.ssh.secretName=flux-git-deploy --set tillerNamespace=kube-system",
            ChartVersion = "0.3.0",
        },
        OperatorInstanceName = "SRSGitHubFluxOp-01",
        OperatorNamespace = "SRS_Namespace",
        OperatorParams = "--git-email=xyzgituser@users.srs.github.com",
        OperatorScope = "namespace",
        OperatorType = "Flux",
        RepositoryUrl = "git@github.com:k8sdeveloper425/flux-get-started",
        ResourceGroupName = "rg1",
        SourceControlConfigurationName = "SRS_GitHubConfig",
        SshKnownHostsContents = "c3NoLmRldi5henVyZS5jb20gc3NoLXJzYSBBQUFBQjNOemFDMXljMkVBQUFBREFRQUJBQUFCQVFDN0hyMW9UV3FOcU9sekdKT2ZHSjROYWtWeUl6ZjFyWFlkNGQ3d282akJsa0x2Q0E0b2RCbEwwbURVeVowL1FVZlRUcWV1K3RtMjJnT3N2K1ZyVlRNazZ2d1JVNzVnWS95OXV0NU1iM2JSNUJWNThkS1h5cTlBOVVlQjVDYWtlaG41WmdtNngxbUtvVnlmK0ZGbjI2aVlxWEpSZ3pJWlpjWjVWNmhyRTBRZzM5a1ptNGF6NDhvMEFVYmY2U3A0U0xkdm51TWEyc1ZOd0hCYm9TN0VKa201N1hRUFZVMy9RcHlOTEhiV0Rkend0cmxTK2V6MzBTM0FkWWhMS0VPeEFHOHdlT255cnRMSkFVZW45bVRrb2w4b0lJMWVkZjdtV1diV1ZmMG5CbWx5MjErblpjbUNUSVNRQnRkY3lQYUVubzdmRlFNREQyNi9zMGxmS29iNEt3OEg=",
    });

});


```

```go
package main

import (
	kubernetesconfiguration "github.com/pulumi/pulumi-azure-native-sdk/kubernetesconfiguration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := kubernetesconfiguration.NewSourceControlConfiguration(ctx, "sourceControlConfiguration", &kubernetesconfiguration.SourceControlConfigurationArgs{
			ClusterName:         pulumi.String("clusterName1"),
			ClusterResourceName: pulumi.String("connectedClusters"),
			ClusterRp:           pulumi.String("Microsoft.Kubernetes"),
			ConfigurationProtectedSettings: pulumi.StringMap{
				"protectedSetting1Key": pulumi.String("protectedSetting1Value"),
			},
			EnableHelmOperator: pulumi.Bool(true),
			HelmOperatorProperties: &kubernetesconfiguration.HelmOperatorPropertiesArgs{
				ChartValues:  pulumi.String("--set git.ssh.secretName=flux-git-deploy --set tillerNamespace=kube-system"),
				ChartVersion: pulumi.String("0.3.0"),
			},
			OperatorInstanceName:           pulumi.String("SRSGitHubFluxOp-01"),
			OperatorNamespace:              pulumi.String("SRS_Namespace"),
			OperatorParams:                 pulumi.String("--git-email=xyzgituser@users.srs.github.com"),
			OperatorScope:                  pulumi.String("namespace"),
			OperatorType:                   pulumi.String("Flux"),
			RepositoryUrl:                  pulumi.String("git@github.com:k8sdeveloper425/flux-get-started"),
			ResourceGroupName:              pulumi.String("rg1"),
			SourceControlConfigurationName: pulumi.String("SRS_GitHubConfig"),
			SshKnownHostsContents:          pulumi.String("c3NoLmRldi5henVyZS5jb20gc3NoLXJzYSBBQUFBQjNOemFDMXljMkVBQUFBREFRQUJBQUFCQVFDN0hyMW9UV3FOcU9sekdKT2ZHSjROYWtWeUl6ZjFyWFlkNGQ3d282akJsa0x2Q0E0b2RCbEwwbURVeVowL1FVZlRUcWV1K3RtMjJnT3N2K1ZyVlRNazZ2d1JVNzVnWS95OXV0NU1iM2JSNUJWNThkS1h5cTlBOVVlQjVDYWtlaG41WmdtNngxbUtvVnlmK0ZGbjI2aVlxWEpSZ3pJWlpjWjVWNmhyRTBRZzM5a1ptNGF6NDhvMEFVYmY2U3A0U0xkdm51TWEyc1ZOd0hCYm9TN0VKa201N1hRUFZVMy9RcHlOTEhiV0Rkend0cmxTK2V6MzBTM0FkWWhMS0VPeEFHOHdlT255cnRMSkFVZW45bVRrb2w4b0lJMWVkZjdtV1diV1ZmMG5CbWx5MjErblpjbUNUSVNRQnRkY3lQYUVubzdmRlFNREQyNi9zMGxmS29iNEt3OEg="),
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
import com.pulumi.azurenative.kubernetesconfiguration.SourceControlConfiguration;
import com.pulumi.azurenative.kubernetesconfiguration.SourceControlConfigurationArgs;
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
        var sourceControlConfiguration = new SourceControlConfiguration("sourceControlConfiguration", SourceControlConfigurationArgs.builder()        
            .clusterName("clusterName1")
            .clusterResourceName("connectedClusters")
            .clusterRp("Microsoft.Kubernetes")
            .configurationProtectedSettings(Map.of("protectedSetting1Key", "protectedSetting1Value"))
            .enableHelmOperator(true)
            .helmOperatorProperties(Map.ofEntries(
                Map.entry("chartValues", "--set git.ssh.secretName=flux-git-deploy --set tillerNamespace=kube-system"),
                Map.entry("chartVersion", "0.3.0")
            ))
            .operatorInstanceName("SRSGitHubFluxOp-01")
            .operatorNamespace("SRS_Namespace")
            .operatorParams("--git-email=xyzgituser@users.srs.github.com")
            .operatorScope("namespace")
            .operatorType("Flux")
            .repositoryUrl("git@github.com:k8sdeveloper425/flux-get-started")
            .resourceGroupName("rg1")
            .sourceControlConfigurationName("SRS_GitHubConfig")
            .sshKnownHostsContents("c3NoLmRldi5henVyZS5jb20gc3NoLXJzYSBBQUFBQjNOemFDMXljMkVBQUFBREFRQUJBQUFCQVFDN0hyMW9UV3FOcU9sekdKT2ZHSjROYWtWeUl6ZjFyWFlkNGQ3d282akJsa0x2Q0E0b2RCbEwwbURVeVowL1FVZlRUcWV1K3RtMjJnT3N2K1ZyVlRNazZ2d1JVNzVnWS95OXV0NU1iM2JSNUJWNThkS1h5cTlBOVVlQjVDYWtlaG41WmdtNngxbUtvVnlmK0ZGbjI2aVlxWEpSZ3pJWlpjWjVWNmhyRTBRZzM5a1ptNGF6NDhvMEFVYmY2U3A0U0xkdm51TWEyc1ZOd0hCYm9TN0VKa201N1hRUFZVMy9RcHlOTEhiV0Rkend0cmxTK2V6MzBTM0FkWWhMS0VPeEFHOHdlT255cnRMSkFVZW45bVRrb2w4b0lJMWVkZjdtV1diV1ZmMG5CbWx5MjErblpjbUNUSVNRQnRkY3lQYUVubzdmRlFNREQyNi9zMGxmS29iNEt3OEg=")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sourceControlConfiguration = new azure_native.kubernetesconfiguration.SourceControlConfiguration("sourceControlConfiguration", {
    clusterName: "clusterName1",
    clusterResourceName: "connectedClusters",
    clusterRp: "Microsoft.Kubernetes",
    configurationProtectedSettings: {
        protectedSetting1Key: "protectedSetting1Value",
    },
    enableHelmOperator: true,
    helmOperatorProperties: {
        chartValues: "--set git.ssh.secretName=flux-git-deploy --set tillerNamespace=kube-system",
        chartVersion: "0.3.0",
    },
    operatorInstanceName: "SRSGitHubFluxOp-01",
    operatorNamespace: "SRS_Namespace",
    operatorParams: "--git-email=xyzgituser@users.srs.github.com",
    operatorScope: "namespace",
    operatorType: "Flux",
    repositoryUrl: "git@github.com:k8sdeveloper425/flux-get-started",
    resourceGroupName: "rg1",
    sourceControlConfigurationName: "SRS_GitHubConfig",
    sshKnownHostsContents: "c3NoLmRldi5henVyZS5jb20gc3NoLXJzYSBBQUFBQjNOemFDMXljMkVBQUFBREFRQUJBQUFCQVFDN0hyMW9UV3FOcU9sekdKT2ZHSjROYWtWeUl6ZjFyWFlkNGQ3d282akJsa0x2Q0E0b2RCbEwwbURVeVowL1FVZlRUcWV1K3RtMjJnT3N2K1ZyVlRNazZ2d1JVNzVnWS95OXV0NU1iM2JSNUJWNThkS1h5cTlBOVVlQjVDYWtlaG41WmdtNngxbUtvVnlmK0ZGbjI2aVlxWEpSZ3pJWlpjWjVWNmhyRTBRZzM5a1ptNGF6NDhvMEFVYmY2U3A0U0xkdm51TWEyc1ZOd0hCYm9TN0VKa201N1hRUFZVMy9RcHlOTEhiV0Rkend0cmxTK2V6MzBTM0FkWWhMS0VPeEFHOHdlT255cnRMSkFVZW45bVRrb2w4b0lJMWVkZjdtV1diV1ZmMG5CbWx5MjErblpjbUNUSVNRQnRkY3lQYUVubzdmRlFNREQyNi9zMGxmS29iNEt3OEg=",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

source_control_configuration = azure_native.kubernetesconfiguration.SourceControlConfiguration("sourceControlConfiguration",
    cluster_name="clusterName1",
    cluster_resource_name="connectedClusters",
    cluster_rp="Microsoft.Kubernetes",
    configuration_protected_settings={
        "protectedSetting1Key": "protectedSetting1Value",
    },
    enable_helm_operator=True,
    helm_operator_properties=azure_native.kubernetesconfiguration.HelmOperatorPropertiesArgs(
        chart_values="--set git.ssh.secretName=flux-git-deploy --set tillerNamespace=kube-system",
        chart_version="0.3.0",
    ),
    operator_instance_name="SRSGitHubFluxOp-01",
    operator_namespace="SRS_Namespace",
    operator_params="--git-email=xyzgituser@users.srs.github.com",
    operator_scope="namespace",
    operator_type="Flux",
    repository_url="git@github.com:k8sdeveloper425/flux-get-started",
    resource_group_name="rg1",
    source_control_configuration_name="SRS_GitHubConfig",
    ssh_known_hosts_contents="c3NoLmRldi5henVyZS5jb20gc3NoLXJzYSBBQUFBQjNOemFDMXljMkVBQUFBREFRQUJBQUFCQVFDN0hyMW9UV3FOcU9sekdKT2ZHSjROYWtWeUl6ZjFyWFlkNGQ3d282akJsa0x2Q0E0b2RCbEwwbURVeVowL1FVZlRUcWV1K3RtMjJnT3N2K1ZyVlRNazZ2d1JVNzVnWS95OXV0NU1iM2JSNUJWNThkS1h5cTlBOVVlQjVDYWtlaG41WmdtNngxbUtvVnlmK0ZGbjI2aVlxWEpSZ3pJWlpjWjVWNmhyRTBRZzM5a1ptNGF6NDhvMEFVYmY2U3A0U0xkdm51TWEyc1ZOd0hCYm9TN0VKa201N1hRUFZVMy9RcHlOTEhiV0Rkend0cmxTK2V6MzBTM0FkWWhMS0VPeEFHOHdlT255cnRMSkFVZW45bVRrb2w4b0lJMWVkZjdtV1diV1ZmMG5CbWx5MjErblpjbUNUSVNRQnRkY3lQYUVubzdmRlFNREQyNi9zMGxmS29iNEt3OEg=")

```

```yaml
resources:
  sourceControlConfiguration:
    type: azure-native:kubernetesconfiguration:SourceControlConfiguration
    properties:
      clusterName: clusterName1
      clusterResourceName: connectedClusters
      clusterRp: Microsoft.Kubernetes
      configurationProtectedSettings:
        protectedSetting1Key: protectedSetting1Value
      enableHelmOperator: true
      helmOperatorProperties:
        chartValues: --set git.ssh.secretName=flux-git-deploy --set tillerNamespace=kube-system
        chartVersion: 0.3.0
      operatorInstanceName: SRSGitHubFluxOp-01
      operatorNamespace: SRS_Namespace
      operatorParams: --git-email=xyzgituser@users.srs.github.com
      operatorScope: namespace
      operatorType: Flux
      repositoryUrl: git@github.com:k8sdeveloper425/flux-get-started
      resourceGroupName: rg1
      sourceControlConfigurationName: SRS_GitHubConfig
      sshKnownHostsContents: c3NoLmRldi5henVyZS5jb20gc3NoLXJzYSBBQUFBQjNOemFDMXljMkVBQUFBREFRQUJBQUFCQVFDN0hyMW9UV3FOcU9sekdKT2ZHSjROYWtWeUl6ZjFyWFlkNGQ3d282akJsa0x2Q0E0b2RCbEwwbURVeVowL1FVZlRUcWV1K3RtMjJnT3N2K1ZyVlRNazZ2d1JVNzVnWS95OXV0NU1iM2JSNUJWNThkS1h5cTlBOVVlQjVDYWtlaG41WmdtNngxbUtvVnlmK0ZGbjI2aVlxWEpSZ3pJWlpjWjVWNmhyRTBRZzM5a1ptNGF6NDhvMEFVYmY2U3A0U0xkdm51TWEyc1ZOd0hCYm9TN0VKa201N1hRUFZVMy9RcHlOTEhiV0Rkend0cmxTK2V6MzBTM0FkWWhMS0VPeEFHOHdlT255cnRMSkFVZW45bVRrb2w4b0lJMWVkZjdtV1diV1ZmMG5CbWx5MjErblpjbUNUSVNRQnRkY3lQYUVubzdmRlFNREQyNi9zMGxmS29iNEt3OEg=

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kubernetesconfiguration:SourceControlConfiguration SRS_GitHubConfig /subscriptions/subId1/resourceGroups/rg1/providers/Microsoft.Kubernetes/connectedClusters/clusterName1/providers/Microsoft.KubernetesConfiguration/sourceControlConfigurations/SRS_GitHubConfig 
```
