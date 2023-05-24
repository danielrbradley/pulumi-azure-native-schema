The Flux Configuration object returned in Get & Put response.
API Version: 2022-11-01.
Previous API Version: 2021-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Flux Configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var fluxConfiguration = new AzureNative.KubernetesConfiguration.FluxConfiguration("fluxConfiguration", new()
    {
        ClusterName = "clusterName1",
        ClusterResourceName = "connectedClusters",
        ClusterRp = "Microsoft.Kubernetes",
        FluxConfigurationName = "srs-fluxconfig",
        GitRepository = new AzureNative.KubernetesConfiguration.Inputs.GitRepositoryDefinitionArgs
        {
            HttpsCACert = "ZXhhbXBsZWNlcnRpZmljYXRl",
            RepositoryRef = new AzureNative.KubernetesConfiguration.Inputs.RepositoryRefDefinitionArgs
            {
                Branch = "master",
            },
            SyncIntervalInSeconds = 600,
            TimeoutInSeconds = 600,
            Url = "https://github.com/Azure/arc-k8s-demo",
        },
        Kustomizations = 
        {
            { "srs-kustomization1", new AzureNative.KubernetesConfiguration.Inputs.KustomizationDefinitionArgs
            {
                DependsOn = new[] {},
                Path = "./test/path",
                SyncIntervalInSeconds = 600,
                TimeoutInSeconds = 600,
            } },
            { "srs-kustomization2", new AzureNative.KubernetesConfiguration.Inputs.KustomizationDefinitionArgs
            {
                DependsOn = new[]
                {
                    "srs-kustomization1",
                },
                Path = "./other/test/path",
                Prune = false,
                RetryIntervalInSeconds = 600,
                SyncIntervalInSeconds = 600,
                TimeoutInSeconds = 600,
            } },
        },
        Namespace = "srs-namespace",
        ResourceGroupName = "rg1",
        Scope = "cluster",
        SourceKind = "GitRepository",
        Suspend = false,
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
		_, err := kubernetesconfiguration.NewFluxConfiguration(ctx, "fluxConfiguration", &kubernetesconfiguration.FluxConfigurationArgs{
			ClusterName:           pulumi.String("clusterName1"),
			ClusterResourceName:   pulumi.String("connectedClusters"),
			ClusterRp:             pulumi.String("Microsoft.Kubernetes"),
			FluxConfigurationName: pulumi.String("srs-fluxconfig"),
			GitRepository: kubernetesconfiguration.GitRepositoryDefinitionResponse{
				HttpsCACert: pulumi.String("ZXhhbXBsZWNlcnRpZmljYXRl"),
				RepositoryRef: &kubernetesconfiguration.RepositoryRefDefinitionArgs{
					Branch: pulumi.String("master"),
				},
				SyncIntervalInSeconds: pulumi.Float64(600),
				TimeoutInSeconds:      pulumi.Float64(600),
				Url:                   pulumi.String("https://github.com/Azure/arc-k8s-demo"),
			},
			Kustomizations: kubernetesconfiguration.KustomizationDefinitionMap{
				"srs-kustomization1": &kubernetesconfiguration.KustomizationDefinitionArgs{
					DependsOn:             pulumi.StringArray{},
					Path:                  pulumi.String("./test/path"),
					SyncIntervalInSeconds: pulumi.Float64(600),
					TimeoutInSeconds:      pulumi.Float64(600),
				},
				"srs-kustomization2": &kubernetesconfiguration.KustomizationDefinitionArgs{
					DependsOn: pulumi.StringArray{
						pulumi.String("srs-kustomization1"),
					},
					Path:                   pulumi.String("./other/test/path"),
					Prune:                  pulumi.Bool(false),
					RetryIntervalInSeconds: pulumi.Float64(600),
					SyncIntervalInSeconds:  pulumi.Float64(600),
					TimeoutInSeconds:       pulumi.Float64(600),
				},
			},
			Namespace:         pulumi.String("srs-namespace"),
			ResourceGroupName: pulumi.String("rg1"),
			Scope:             pulumi.String("cluster"),
			SourceKind:        pulumi.String("GitRepository"),
			Suspend:           pulumi.Bool(false),
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
import com.pulumi.azurenative.kubernetesconfiguration.FluxConfiguration;
import com.pulumi.azurenative.kubernetesconfiguration.FluxConfigurationArgs;
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
        var fluxConfiguration = new FluxConfiguration("fluxConfiguration", FluxConfigurationArgs.builder()        
            .clusterName("clusterName1")
            .clusterResourceName("connectedClusters")
            .clusterRp("Microsoft.Kubernetes")
            .fluxConfigurationName("srs-fluxconfig")
            .gitRepository(Map.ofEntries(
                Map.entry("httpsCACert", "ZXhhbXBsZWNlcnRpZmljYXRl"),
                Map.entry("repositoryRef", Map.of("branch", "master")),
                Map.entry("syncIntervalInSeconds", 600),
                Map.entry("timeoutInSeconds", 600),
                Map.entry("url", "https://github.com/Azure/arc-k8s-demo")
            ))
            .kustomizations(Map.ofEntries(
                Map.entry("srs-kustomization1", Map.ofEntries(
                    Map.entry("dependsOn", ),
                    Map.entry("path", "./test/path"),
                    Map.entry("syncIntervalInSeconds", 600),
                    Map.entry("timeoutInSeconds", 600)
                )),
                Map.entry("srs-kustomization2", Map.ofEntries(
                    Map.entry("dependsOn", "srs-kustomization1"),
                    Map.entry("path", "./other/test/path"),
                    Map.entry("prune", false),
                    Map.entry("retryIntervalInSeconds", 600),
                    Map.entry("syncIntervalInSeconds", 600),
                    Map.entry("timeoutInSeconds", 600)
                ))
            ))
            .namespace("srs-namespace")
            .resourceGroupName("rg1")
            .scope("cluster")
            .sourceKind("GitRepository")
            .suspend(false)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const fluxConfiguration = new azure_native.kubernetesconfiguration.FluxConfiguration("fluxConfiguration", {
    clusterName: "clusterName1",
    clusterResourceName: "connectedClusters",
    clusterRp: "Microsoft.Kubernetes",
    fluxConfigurationName: "srs-fluxconfig",
    gitRepository: {
        httpsCACert: "ZXhhbXBsZWNlcnRpZmljYXRl",
        repositoryRef: {
            branch: "master",
        },
        syncIntervalInSeconds: 600,
        timeoutInSeconds: 600,
        url: "https://github.com/Azure/arc-k8s-demo",
    },
    kustomizations: {
        "srs-kustomization1": {
            dependsOn: [],
            path: "./test/path",
            syncIntervalInSeconds: 600,
            timeoutInSeconds: 600,
        },
        "srs-kustomization2": {
            dependsOn: ["srs-kustomization1"],
            path: "./other/test/path",
            prune: false,
            retryIntervalInSeconds: 600,
            syncIntervalInSeconds: 600,
            timeoutInSeconds: 600,
        },
    },
    namespace: "srs-namespace",
    resourceGroupName: "rg1",
    scope: "cluster",
    sourceKind: "GitRepository",
    suspend: false,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

flux_configuration = azure_native.kubernetesconfiguration.FluxConfiguration("fluxConfiguration",
    cluster_name="clusterName1",
    cluster_resource_name="connectedClusters",
    cluster_rp="Microsoft.Kubernetes",
    flux_configuration_name="srs-fluxconfig",
    git_repository=azure_native.kubernetesconfiguration.GitRepositoryDefinitionResponseArgs(
        https_ca_cert="ZXhhbXBsZWNlcnRpZmljYXRl",
        repository_ref=azure_native.kubernetesconfiguration.RepositoryRefDefinitionArgs(
            branch="master",
        ),
        sync_interval_in_seconds=600,
        timeout_in_seconds=600,
        url="https://github.com/Azure/arc-k8s-demo",
    ),
    kustomizations={
        "srs-kustomization1": azure_native.kubernetesconfiguration.KustomizationDefinitionArgs(
            depends_on=[],
            path="./test/path",
            sync_interval_in_seconds=600,
            timeout_in_seconds=600,
        ),
        "srs-kustomization2": azure_native.kubernetesconfiguration.KustomizationDefinitionArgs(
            depends_on=["srs-kustomization1"],
            path="./other/test/path",
            prune=False,
            retry_interval_in_seconds=600,
            sync_interval_in_seconds=600,
            timeout_in_seconds=600,
        ),
    },
    namespace="srs-namespace",
    resource_group_name="rg1",
    scope="cluster",
    source_kind="GitRepository",
    suspend=False)

```

```yaml
resources:
  fluxConfiguration:
    type: azure-native:kubernetesconfiguration:FluxConfiguration
    properties:
      clusterName: clusterName1
      clusterResourceName: connectedClusters
      clusterRp: Microsoft.Kubernetes
      fluxConfigurationName: srs-fluxconfig
      gitRepository:
        httpsCACert: ZXhhbXBsZWNlcnRpZmljYXRl
        repositoryRef:
          branch: master
        syncIntervalInSeconds: 600
        timeoutInSeconds: 600
        url: https://github.com/Azure/arc-k8s-demo
      kustomizations:
        srs-kustomization1:
          dependsOn: []
          path: ./test/path
          syncIntervalInSeconds: 600
          timeoutInSeconds: 600
        srs-kustomization2:
          dependsOn:
            - srs-kustomization1
          path: ./other/test/path
          prune: false
          retryIntervalInSeconds: 600
          syncIntervalInSeconds: 600
          timeoutInSeconds: 600
      namespace: srs-namespace
      resourceGroupName: rg1
      scope: cluster
      sourceKind: GitRepository
      suspend: false

```

{{% /example %}}
{{% example %}}
### Create Flux Configuration with Bucket Source Kind
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var fluxConfiguration = new AzureNative.KubernetesConfiguration.FluxConfiguration("fluxConfiguration", new()
    {
        Bucket = new AzureNative.KubernetesConfiguration.Inputs.BucketDefinitionArgs
        {
            AccessKey = "fluxminiotest",
            BucketName = "flux",
            SyncIntervalInSeconds = 1000,
            TimeoutInSeconds = 1000,
            Url = "https://fluxminiotest.az.minio.io",
        },
        ClusterName = "clusterName1",
        ClusterResourceName = "connectedClusters",
        ClusterRp = "Microsoft.Kubernetes",
        FluxConfigurationName = "srs-fluxconfig",
        Kustomizations = 
        {
            { "srs-kustomization1", new AzureNative.KubernetesConfiguration.Inputs.KustomizationDefinitionArgs
            {
                DependsOn = new[] {},
                Path = "./test/path",
                SyncIntervalInSeconds = 600,
                TimeoutInSeconds = 600,
            } },
            { "srs-kustomization2", new AzureNative.KubernetesConfiguration.Inputs.KustomizationDefinitionArgs
            {
                DependsOn = new[]
                {
                    "srs-kustomization1",
                },
                Path = "./other/test/path",
                Prune = false,
                RetryIntervalInSeconds = 600,
                SyncIntervalInSeconds = 600,
                TimeoutInSeconds = 600,
            } },
        },
        Namespace = "srs-namespace",
        ResourceGroupName = "rg1",
        Scope = "cluster",
        SourceKind = "Bucket",
        Suspend = false,
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
		_, err := kubernetesconfiguration.NewFluxConfiguration(ctx, "fluxConfiguration", &kubernetesconfiguration.FluxConfigurationArgs{
			Bucket: &kubernetesconfiguration.BucketDefinitionArgs{
				AccessKey:             pulumi.String("fluxminiotest"),
				BucketName:            pulumi.String("flux"),
				SyncIntervalInSeconds: pulumi.Float64(1000),
				TimeoutInSeconds:      pulumi.Float64(1000),
				Url:                   pulumi.String("https://fluxminiotest.az.minio.io"),
			},
			ClusterName:           pulumi.String("clusterName1"),
			ClusterResourceName:   pulumi.String("connectedClusters"),
			ClusterRp:             pulumi.String("Microsoft.Kubernetes"),
			FluxConfigurationName: pulumi.String("srs-fluxconfig"),
			Kustomizations: kubernetesconfiguration.KustomizationDefinitionMap{
				"srs-kustomization1": &kubernetesconfiguration.KustomizationDefinitionArgs{
					DependsOn:             pulumi.StringArray{},
					Path:                  pulumi.String("./test/path"),
					SyncIntervalInSeconds: pulumi.Float64(600),
					TimeoutInSeconds:      pulumi.Float64(600),
				},
				"srs-kustomization2": &kubernetesconfiguration.KustomizationDefinitionArgs{
					DependsOn: pulumi.StringArray{
						pulumi.String("srs-kustomization1"),
					},
					Path:                   pulumi.String("./other/test/path"),
					Prune:                  pulumi.Bool(false),
					RetryIntervalInSeconds: pulumi.Float64(600),
					SyncIntervalInSeconds:  pulumi.Float64(600),
					TimeoutInSeconds:       pulumi.Float64(600),
				},
			},
			Namespace:         pulumi.String("srs-namespace"),
			ResourceGroupName: pulumi.String("rg1"),
			Scope:             pulumi.String("cluster"),
			SourceKind:        pulumi.String("Bucket"),
			Suspend:           pulumi.Bool(false),
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
import com.pulumi.azurenative.kubernetesconfiguration.FluxConfiguration;
import com.pulumi.azurenative.kubernetesconfiguration.FluxConfigurationArgs;
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
        var fluxConfiguration = new FluxConfiguration("fluxConfiguration", FluxConfigurationArgs.builder()        
            .bucket(Map.ofEntries(
                Map.entry("accessKey", "fluxminiotest"),
                Map.entry("bucketName", "flux"),
                Map.entry("syncIntervalInSeconds", 1000),
                Map.entry("timeoutInSeconds", 1000),
                Map.entry("url", "https://fluxminiotest.az.minio.io")
            ))
            .clusterName("clusterName1")
            .clusterResourceName("connectedClusters")
            .clusterRp("Microsoft.Kubernetes")
            .fluxConfigurationName("srs-fluxconfig")
            .kustomizations(Map.ofEntries(
                Map.entry("srs-kustomization1", Map.ofEntries(
                    Map.entry("dependsOn", ),
                    Map.entry("path", "./test/path"),
                    Map.entry("syncIntervalInSeconds", 600),
                    Map.entry("timeoutInSeconds", 600)
                )),
                Map.entry("srs-kustomization2", Map.ofEntries(
                    Map.entry("dependsOn", "srs-kustomization1"),
                    Map.entry("path", "./other/test/path"),
                    Map.entry("prune", false),
                    Map.entry("retryIntervalInSeconds", 600),
                    Map.entry("syncIntervalInSeconds", 600),
                    Map.entry("timeoutInSeconds", 600)
                ))
            ))
            .namespace("srs-namespace")
            .resourceGroupName("rg1")
            .scope("cluster")
            .sourceKind("Bucket")
            .suspend(false)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const fluxConfiguration = new azure_native.kubernetesconfiguration.FluxConfiguration("fluxConfiguration", {
    bucket: {
        accessKey: "fluxminiotest",
        bucketName: "flux",
        syncIntervalInSeconds: 1000,
        timeoutInSeconds: 1000,
        url: "https://fluxminiotest.az.minio.io",
    },
    clusterName: "clusterName1",
    clusterResourceName: "connectedClusters",
    clusterRp: "Microsoft.Kubernetes",
    fluxConfigurationName: "srs-fluxconfig",
    kustomizations: {
        "srs-kustomization1": {
            dependsOn: [],
            path: "./test/path",
            syncIntervalInSeconds: 600,
            timeoutInSeconds: 600,
        },
        "srs-kustomization2": {
            dependsOn: ["srs-kustomization1"],
            path: "./other/test/path",
            prune: false,
            retryIntervalInSeconds: 600,
            syncIntervalInSeconds: 600,
            timeoutInSeconds: 600,
        },
    },
    namespace: "srs-namespace",
    resourceGroupName: "rg1",
    scope: "cluster",
    sourceKind: "Bucket",
    suspend: false,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

flux_configuration = azure_native.kubernetesconfiguration.FluxConfiguration("fluxConfiguration",
    bucket=azure_native.kubernetesconfiguration.BucketDefinitionArgs(
        access_key="fluxminiotest",
        bucket_name="flux",
        sync_interval_in_seconds=1000,
        timeout_in_seconds=1000,
        url="https://fluxminiotest.az.minio.io",
    ),
    cluster_name="clusterName1",
    cluster_resource_name="connectedClusters",
    cluster_rp="Microsoft.Kubernetes",
    flux_configuration_name="srs-fluxconfig",
    kustomizations={
        "srs-kustomization1": azure_native.kubernetesconfiguration.KustomizationDefinitionArgs(
            depends_on=[],
            path="./test/path",
            sync_interval_in_seconds=600,
            timeout_in_seconds=600,
        ),
        "srs-kustomization2": azure_native.kubernetesconfiguration.KustomizationDefinitionArgs(
            depends_on=["srs-kustomization1"],
            path="./other/test/path",
            prune=False,
            retry_interval_in_seconds=600,
            sync_interval_in_seconds=600,
            timeout_in_seconds=600,
        ),
    },
    namespace="srs-namespace",
    resource_group_name="rg1",
    scope="cluster",
    source_kind="Bucket",
    suspend=False)

```

```yaml
resources:
  fluxConfiguration:
    type: azure-native:kubernetesconfiguration:FluxConfiguration
    properties:
      bucket:
        accessKey: fluxminiotest
        bucketName: flux
        syncIntervalInSeconds: 1000
        timeoutInSeconds: 1000
        url: https://fluxminiotest.az.minio.io
      clusterName: clusterName1
      clusterResourceName: connectedClusters
      clusterRp: Microsoft.Kubernetes
      fluxConfigurationName: srs-fluxconfig
      kustomizations:
        srs-kustomization1:
          dependsOn: []
          path: ./test/path
          syncIntervalInSeconds: 600
          timeoutInSeconds: 600
        srs-kustomization2:
          dependsOn:
            - srs-kustomization1
          path: ./other/test/path
          prune: false
          retryIntervalInSeconds: 600
          syncIntervalInSeconds: 600
          timeoutInSeconds: 600
      namespace: srs-namespace
      resourceGroupName: rg1
      scope: cluster
      sourceKind: Bucket
      suspend: false

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kubernetesconfiguration:FluxConfiguration srs-fluxconfig /subscriptions/subId1/resourceGroups/rg1/providers/Microsoft.Kubernetes/connectedClusters/clusterName1/providers/Microsoft.KubernetesConfiguration/fluxConfigurations/srs-fluxconfig 
```
