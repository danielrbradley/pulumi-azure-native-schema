Class representing a Kusto cluster.
API Version: 2022-12-29.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### KustoClustersCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.Kusto.Cluster("cluster", new()
    {
        AllowedIpRangeList = new[]
        {
            "0.0.0.0/0",
        },
        ClusterName = "kustoCluster",
        EnableAutoStop = true,
        EnableDoubleEncryption = false,
        EnablePurge = true,
        EnableStreamingIngest = true,
        Identity = new AzureNative.Kusto.Inputs.IdentityArgs
        {
            Type = "SystemAssigned",
        },
        LanguageExtensions = new AzureNative.Kusto.Inputs.LanguageExtensionsListArgs
        {
            Value = new[]
            {
                new AzureNative.Kusto.Inputs.LanguageExtensionArgs
                {
                    LanguageExtensionImageName = "Python3_10_8",
                    LanguageExtensionName = "PYTHON",
                },
                new AzureNative.Kusto.Inputs.LanguageExtensionArgs
                {
                    LanguageExtensionImageName = "R",
                    LanguageExtensionName = "R",
                },
            },
        },
        Location = "westus",
        PublicIPType = "DualStack",
        PublicNetworkAccess = "Enabled",
        ResourceGroupName = "kustorptest",
        Sku = new AzureNative.Kusto.Inputs.AzureSkuArgs
        {
            Capacity = 2,
            Name = "Standard_L16as_v3",
            Tier = "Standard",
        },
    });

});


```

```go
package main

import (
	kusto "github.com/pulumi/pulumi-azure-native-sdk/kusto"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := kusto.NewCluster(ctx, "cluster", &kusto.ClusterArgs{
			AllowedIpRangeList: pulumi.StringArray{
				pulumi.String("0.0.0.0/0"),
			},
			ClusterName:            pulumi.String("kustoCluster"),
			EnableAutoStop:         pulumi.Bool(true),
			EnableDoubleEncryption: pulumi.Bool(false),
			EnablePurge:            pulumi.Bool(true),
			EnableStreamingIngest:  pulumi.Bool(true),
			Identity: &kusto.IdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			LanguageExtensions: kusto.LanguageExtensionsListResponse{
				Value: kusto.LanguageExtensionArray{
					&kusto.LanguageExtensionArgs{
						LanguageExtensionImageName: pulumi.String("Python3_10_8"),
						LanguageExtensionName:      pulumi.String("PYTHON"),
					},
					&kusto.LanguageExtensionArgs{
						LanguageExtensionImageName: pulumi.String("R"),
						LanguageExtensionName:      pulumi.String("R"),
					},
				},
			},
			Location:            pulumi.String("westus"),
			PublicIPType:        pulumi.String("DualStack"),
			PublicNetworkAccess: pulumi.String("Enabled"),
			ResourceGroupName:   pulumi.String("kustorptest"),
			Sku: &kusto.AzureSkuArgs{
				Capacity: pulumi.Int(2),
				Name:     pulumi.String("Standard_L16as_v3"),
				Tier:     pulumi.String("Standard"),
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
import com.pulumi.azurenative.kusto.Cluster;
import com.pulumi.azurenative.kusto.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .allowedIpRangeList("0.0.0.0/0")
            .clusterName("kustoCluster")
            .enableAutoStop(true)
            .enableDoubleEncryption(false)
            .enablePurge(true)
            .enableStreamingIngest(true)
            .identity(Map.of("type", "SystemAssigned"))
            .languageExtensions(Map.of("value",             
                Map.ofEntries(
                    Map.entry("languageExtensionImageName", "Python3_10_8"),
                    Map.entry("languageExtensionName", "PYTHON")
                ),
                Map.ofEntries(
                    Map.entry("languageExtensionImageName", "R"),
                    Map.entry("languageExtensionName", "R")
                )))
            .location("westus")
            .publicIPType("DualStack")
            .publicNetworkAccess("Enabled")
            .resourceGroupName("kustorptest")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("name", "Standard_L16as_v3"),
                Map.entry("tier", "Standard")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.kusto.Cluster("cluster", {
    allowedIpRangeList: ["0.0.0.0/0"],
    clusterName: "kustoCluster",
    enableAutoStop: true,
    enableDoubleEncryption: false,
    enablePurge: true,
    enableStreamingIngest: true,
    identity: {
        type: "SystemAssigned",
    },
    languageExtensions: {
        value: [
            {
                languageExtensionImageName: "Python3_10_8",
                languageExtensionName: "PYTHON",
            },
            {
                languageExtensionImageName: "R",
                languageExtensionName: "R",
            },
        ],
    },
    location: "westus",
    publicIPType: "DualStack",
    publicNetworkAccess: "Enabled",
    resourceGroupName: "kustorptest",
    sku: {
        capacity: 2,
        name: "Standard_L16as_v3",
        tier: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.kusto.Cluster("cluster",
    allowed_ip_range_list=["0.0.0.0/0"],
    cluster_name="kustoCluster",
    enable_auto_stop=True,
    enable_double_encryption=False,
    enable_purge=True,
    enable_streaming_ingest=True,
    identity=azure_native.kusto.IdentityArgs(
        type="SystemAssigned",
    ),
    language_extensions=azure_native.kusto.LanguageExtensionsListResponseArgs(
        value=[
            azure_native.kusto.LanguageExtensionArgs(
                language_extension_image_name="Python3_10_8",
                language_extension_name="PYTHON",
            ),
            azure_native.kusto.LanguageExtensionArgs(
                language_extension_image_name="R",
                language_extension_name="R",
            ),
        ],
    ),
    location="westus",
    public_ip_type="DualStack",
    public_network_access="Enabled",
    resource_group_name="kustorptest",
    sku=azure_native.kusto.AzureSkuArgs(
        capacity=2,
        name="Standard_L16as_v3",
        tier="Standard",
    ))

```

```yaml
resources:
  cluster:
    type: azure-native:kusto:Cluster
    properties:
      allowedIpRangeList:
        - 0.0.0.0/0
      clusterName: kustoCluster
      enableAutoStop: true
      enableDoubleEncryption: false
      enablePurge: true
      enableStreamingIngest: true
      identity:
        type: SystemAssigned
      languageExtensions:
        value:
          - languageExtensionImageName: Python3_10_8
            languageExtensionName: PYTHON
          - languageExtensionImageName: R
            languageExtensionName: R
      location: westus
      publicIPType: DualStack
      publicNetworkAccess: Enabled
      resourceGroupName: kustorptest
      sku:
        capacity: 2
        name: Standard_L16as_v3
        tier: Standard

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kusto:Cluster kustoCluster /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster 
```
