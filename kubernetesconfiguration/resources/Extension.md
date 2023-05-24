The Extension object.
API Version: 2022-11-01.
Previous API Version: 2020-07-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Extension
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var extension = new AzureNative.KubernetesConfiguration.Extension("extension", new()
    {
        AutoUpgradeMinorVersion = true,
        ClusterName = "clusterName1",
        ClusterResourceName = "connectedClusters",
        ClusterRp = "Microsoft.Kubernetes",
        ConfigurationProtectedSettings = 
        {
            { "omsagent.secret.key", "secretKeyValue01" },
        },
        ConfigurationSettings = 
        {
            { "omsagent.env.clusterName", "clusterName1" },
            { "omsagent.secret.wsid", "a38cef99-5a89-52ed-b6db-22095c23664b" },
        },
        ExtensionName = "ClusterMonitor",
        ExtensionType = "azuremonitor-containers",
        ReleaseTrain = "Preview",
        ResourceGroupName = "rg1",
        Scope = new AzureNative.KubernetesConfiguration.Inputs.ScopeArgs
        {
            Cluster = new AzureNative.KubernetesConfiguration.Inputs.ScopeClusterArgs
            {
                ReleaseNamespace = "kube-system",
            },
        },
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
		_, err := kubernetesconfiguration.NewExtension(ctx, "extension", &kubernetesconfiguration.ExtensionArgs{
			AutoUpgradeMinorVersion: pulumi.Bool(true),
			ClusterName:             pulumi.String("clusterName1"),
			ClusterResourceName:     pulumi.String("connectedClusters"),
			ClusterRp:               pulumi.String("Microsoft.Kubernetes"),
			ConfigurationProtectedSettings: pulumi.StringMap{
				"omsagent.secret.key": pulumi.String("secretKeyValue01"),
			},
			ConfigurationSettings: pulumi.StringMap{
				"omsagent.env.clusterName": pulumi.String("clusterName1"),
				"omsagent.secret.wsid":     pulumi.String("a38cef99-5a89-52ed-b6db-22095c23664b"),
			},
			ExtensionName:     pulumi.String("ClusterMonitor"),
			ExtensionType:     pulumi.String("azuremonitor-containers"),
			ReleaseTrain:      pulumi.String("Preview"),
			ResourceGroupName: pulumi.String("rg1"),
			Scope: kubernetesconfiguration.ScopeResponse{
				Cluster: &kubernetesconfiguration.ScopeClusterArgs{
					ReleaseNamespace: pulumi.String("kube-system"),
				},
			},
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
import com.pulumi.azurenative.kubernetesconfiguration.Extension;
import com.pulumi.azurenative.kubernetesconfiguration.ExtensionArgs;
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
        var extension = new Extension("extension", ExtensionArgs.builder()        
            .autoUpgradeMinorVersion(true)
            .clusterName("clusterName1")
            .clusterResourceName("connectedClusters")
            .clusterRp("Microsoft.Kubernetes")
            .configurationProtectedSettings(Map.of("omsagent.secret.key", "secretKeyValue01"))
            .configurationSettings(Map.ofEntries(
                Map.entry("omsagent.env.clusterName", "clusterName1"),
                Map.entry("omsagent.secret.wsid", "a38cef99-5a89-52ed-b6db-22095c23664b")
            ))
            .extensionName("ClusterMonitor")
            .extensionType("azuremonitor-containers")
            .releaseTrain("Preview")
            .resourceGroupName("rg1")
            .scope(Map.of("cluster", Map.of("releaseNamespace", "kube-system")))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const extension = new azure_native.kubernetesconfiguration.Extension("extension", {
    autoUpgradeMinorVersion: true,
    clusterName: "clusterName1",
    clusterResourceName: "connectedClusters",
    clusterRp: "Microsoft.Kubernetes",
    configurationProtectedSettings: {
        "omsagent.secret.key": "secretKeyValue01",
    },
    configurationSettings: {
        "omsagent.env.clusterName": "clusterName1",
        "omsagent.secret.wsid": "a38cef99-5a89-52ed-b6db-22095c23664b",
    },
    extensionName: "ClusterMonitor",
    extensionType: "azuremonitor-containers",
    releaseTrain: "Preview",
    resourceGroupName: "rg1",
    scope: {
        cluster: {
            releaseNamespace: "kube-system",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

extension = azure_native.kubernetesconfiguration.Extension("extension",
    auto_upgrade_minor_version=True,
    cluster_name="clusterName1",
    cluster_resource_name="connectedClusters",
    cluster_rp="Microsoft.Kubernetes",
    configuration_protected_settings={
        "omsagent.secret.key": "secretKeyValue01",
    },
    configuration_settings={
        "omsagent.env.clusterName": "clusterName1",
        "omsagent.secret.wsid": "a38cef99-5a89-52ed-b6db-22095c23664b",
    },
    extension_name="ClusterMonitor",
    extension_type="azuremonitor-containers",
    release_train="Preview",
    resource_group_name="rg1",
    scope=azure_native.kubernetesconfiguration.ScopeResponseArgs(
        cluster=azure_native.kubernetesconfiguration.ScopeClusterArgs(
            release_namespace="kube-system",
        ),
    ))

```

```yaml
resources:
  extension:
    type: azure-native:kubernetesconfiguration:Extension
    properties:
      autoUpgradeMinorVersion: true
      clusterName: clusterName1
      clusterResourceName: connectedClusters
      clusterRp: Microsoft.Kubernetes
      configurationProtectedSettings:
        omsagent.secret.key: secretKeyValue01
      configurationSettings:
        omsagent.env.clusterName: clusterName1
        omsagent.secret.wsid: a38cef99-5a89-52ed-b6db-22095c23664b
      extensionName: ClusterMonitor
      extensionType: azuremonitor-containers
      releaseTrain: Preview
      resourceGroupName: rg1
      scope:
        cluster:
          releaseNamespace: kube-system

```

{{% /example %}}
{{% example %}}
### Create Extension with Plan
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var extension = new AzureNative.KubernetesConfiguration.Extension("extension", new()
    {
        AutoUpgradeMinorVersion = true,
        ClusterName = "clusterName1",
        ClusterResourceName = "connectedClusters",
        ClusterRp = "Microsoft.Kubernetes",
        ExtensionName = "azureVote",
        ExtensionType = "azure-vote",
        Plan = new AzureNative.KubernetesConfiguration.Inputs.PlanArgs
        {
            Name = "azure-vote-standard",
            Product = "azure-vote-standard-offer-id",
            Publisher = "Microsoft",
        },
        ReleaseTrain = "Preview",
        ResourceGroupName = "rg1",
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
		_, err := kubernetesconfiguration.NewExtension(ctx, "extension", &kubernetesconfiguration.ExtensionArgs{
			AutoUpgradeMinorVersion: pulumi.Bool(true),
			ClusterName:             pulumi.String("clusterName1"),
			ClusterResourceName:     pulumi.String("connectedClusters"),
			ClusterRp:               pulumi.String("Microsoft.Kubernetes"),
			ExtensionName:           pulumi.String("azureVote"),
			ExtensionType:           pulumi.String("azure-vote"),
			Plan: &kubernetesconfiguration.PlanArgs{
				Name:      pulumi.String("azure-vote-standard"),
				Product:   pulumi.String("azure-vote-standard-offer-id"),
				Publisher: pulumi.String("Microsoft"),
			},
			ReleaseTrain:      pulumi.String("Preview"),
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
import com.pulumi.azurenative.kubernetesconfiguration.Extension;
import com.pulumi.azurenative.kubernetesconfiguration.ExtensionArgs;
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
        var extension = new Extension("extension", ExtensionArgs.builder()        
            .autoUpgradeMinorVersion(true)
            .clusterName("clusterName1")
            .clusterResourceName("connectedClusters")
            .clusterRp("Microsoft.Kubernetes")
            .extensionName("azureVote")
            .extensionType("azure-vote")
            .plan(Map.ofEntries(
                Map.entry("name", "azure-vote-standard"),
                Map.entry("product", "azure-vote-standard-offer-id"),
                Map.entry("publisher", "Microsoft")
            ))
            .releaseTrain("Preview")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const extension = new azure_native.kubernetesconfiguration.Extension("extension", {
    autoUpgradeMinorVersion: true,
    clusterName: "clusterName1",
    clusterResourceName: "connectedClusters",
    clusterRp: "Microsoft.Kubernetes",
    extensionName: "azureVote",
    extensionType: "azure-vote",
    plan: {
        name: "azure-vote-standard",
        product: "azure-vote-standard-offer-id",
        publisher: "Microsoft",
    },
    releaseTrain: "Preview",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

extension = azure_native.kubernetesconfiguration.Extension("extension",
    auto_upgrade_minor_version=True,
    cluster_name="clusterName1",
    cluster_resource_name="connectedClusters",
    cluster_rp="Microsoft.Kubernetes",
    extension_name="azureVote",
    extension_type="azure-vote",
    plan=azure_native.kubernetesconfiguration.PlanArgs(
        name="azure-vote-standard",
        product="azure-vote-standard-offer-id",
        publisher="Microsoft",
    ),
    release_train="Preview",
    resource_group_name="rg1")

```

```yaml
resources:
  extension:
    type: azure-native:kubernetesconfiguration:Extension
    properties:
      autoUpgradeMinorVersion: true
      clusterName: clusterName1
      clusterResourceName: connectedClusters
      clusterRp: Microsoft.Kubernetes
      extensionName: azureVote
      extensionType: azure-vote
      plan:
        name: azure-vote-standard
        product: azure-vote-standard-offer-id
        publisher: Microsoft
      releaseTrain: Preview
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kubernetesconfiguration:Extension azureVote /subscriptions/subId1/resourceGroups/rg1/providers/Microsoft.Kubernetes/connectedClusters/clusterName1/providers/Microsoft.KubernetesConfiguration/extensions/azureVote 
```
