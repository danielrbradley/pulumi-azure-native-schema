A private cloud resource
API Version: 2022-05-01.
Previous API Version: 2020-03-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateClouds_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateCloud = new AzureNative.AVS.PrivateCloud("privateCloud", new()
    {
        Identity = new AzureNative.AVS.Inputs.PrivateCloudIdentityArgs
        {
            Type = "SystemAssigned",
        },
        Location = "eastus2",
        ManagementCluster = new AzureNative.AVS.Inputs.ManagementClusterArgs
        {
            ClusterSize = 4,
        },
        NetworkBlock = "192.168.48.0/22",
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
        Sku = new AzureNative.AVS.Inputs.SkuArgs
        {
            Name = "AV36",
        },
        Tags = null,
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
		_, err := avs.NewPrivateCloud(ctx, "privateCloud", &avs.PrivateCloudArgs{
			Identity: &avs.PrivateCloudIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Location: pulumi.String("eastus2"),
			ManagementCluster: &avs.ManagementClusterArgs{
				ClusterSize: pulumi.Int(4),
			},
			NetworkBlock:      pulumi.String("192.168.48.0/22"),
			PrivateCloudName:  pulumi.String("cloud1"),
			ResourceGroupName: pulumi.String("group1"),
			Sku: &avs.SkuArgs{
				Name: pulumi.String("AV36"),
			},
			Tags: nil,
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
import com.pulumi.azurenative.avs.PrivateCloud;
import com.pulumi.azurenative.avs.PrivateCloudArgs;
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
        var privateCloud = new PrivateCloud("privateCloud", PrivateCloudArgs.builder()        
            .identity(Map.of("type", "SystemAssigned"))
            .location("eastus2")
            .managementCluster(Map.of("clusterSize", 4))
            .networkBlock("192.168.48.0/22")
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .sku(Map.of("name", "AV36"))
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateCloud = new azure_native.avs.PrivateCloud("privateCloud", {
    identity: {
        type: "SystemAssigned",
    },
    location: "eastus2",
    managementCluster: {
        clusterSize: 4,
    },
    networkBlock: "192.168.48.0/22",
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
    sku: {
        name: "AV36",
    },
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_cloud = azure_native.avs.PrivateCloud("privateCloud",
    identity=azure_native.avs.PrivateCloudIdentityArgs(
        type="SystemAssigned",
    ),
    location="eastus2",
    management_cluster=azure_native.avs.ManagementClusterArgs(
        cluster_size=4,
    ),
    network_block="192.168.48.0/22",
    private_cloud_name="cloud1",
    resource_group_name="group1",
    sku=azure_native.avs.SkuArgs(
        name="AV36",
    ),
    tags={})

```

```yaml
resources:
  privateCloud:
    type: azure-native:avs:PrivateCloud
    properties:
      identity:
        type: SystemAssigned
      location: eastus2
      managementCluster:
        clusterSize: 4
      networkBlock: 192.168.48.0/22
      privateCloudName: cloud1
      resourceGroupName: group1
      sku:
        name: AV36
      tags: {}

```

{{% /example %}}
{{% example %}}
### PrivateClouds_CreateOrUpdate_Stretched
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateCloud = new AzureNative.AVS.PrivateCloud("privateCloud", new()
    {
        Availability = new AzureNative.AVS.Inputs.AvailabilityPropertiesArgs
        {
            SecondaryZone = 2,
            Strategy = "DualZone",
            Zone = 1,
        },
        Location = "eastus2",
        ManagementCluster = new AzureNative.AVS.Inputs.ManagementClusterArgs
        {
            ClusterSize = 4,
        },
        NetworkBlock = "192.168.48.0/22",
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
        Sku = new AzureNative.AVS.Inputs.SkuArgs
        {
            Name = "AV36",
        },
        Tags = null,
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
		_, err := avs.NewPrivateCloud(ctx, "privateCloud", &avs.PrivateCloudArgs{
			Availability: &avs.AvailabilityPropertiesArgs{
				SecondaryZone: pulumi.Int(2),
				Strategy:      pulumi.String("DualZone"),
				Zone:          pulumi.Int(1),
			},
			Location: pulumi.String("eastus2"),
			ManagementCluster: &avs.ManagementClusterArgs{
				ClusterSize: pulumi.Int(4),
			},
			NetworkBlock:      pulumi.String("192.168.48.0/22"),
			PrivateCloudName:  pulumi.String("cloud1"),
			ResourceGroupName: pulumi.String("group1"),
			Sku: &avs.SkuArgs{
				Name: pulumi.String("AV36"),
			},
			Tags: nil,
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
import com.pulumi.azurenative.avs.PrivateCloud;
import com.pulumi.azurenative.avs.PrivateCloudArgs;
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
        var privateCloud = new PrivateCloud("privateCloud", PrivateCloudArgs.builder()        
            .availability(Map.ofEntries(
                Map.entry("secondaryZone", 2),
                Map.entry("strategy", "DualZone"),
                Map.entry("zone", 1)
            ))
            .location("eastus2")
            .managementCluster(Map.of("clusterSize", 4))
            .networkBlock("192.168.48.0/22")
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .sku(Map.of("name", "AV36"))
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateCloud = new azure_native.avs.PrivateCloud("privateCloud", {
    availability: {
        secondaryZone: 2,
        strategy: "DualZone",
        zone: 1,
    },
    location: "eastus2",
    managementCluster: {
        clusterSize: 4,
    },
    networkBlock: "192.168.48.0/22",
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
    sku: {
        name: "AV36",
    },
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_cloud = azure_native.avs.PrivateCloud("privateCloud",
    availability=azure_native.avs.AvailabilityPropertiesArgs(
        secondary_zone=2,
        strategy="DualZone",
        zone=1,
    ),
    location="eastus2",
    management_cluster=azure_native.avs.ManagementClusterArgs(
        cluster_size=4,
    ),
    network_block="192.168.48.0/22",
    private_cloud_name="cloud1",
    resource_group_name="group1",
    sku=azure_native.avs.SkuArgs(
        name="AV36",
    ),
    tags={})

```

```yaml
resources:
  privateCloud:
    type: azure-native:avs:PrivateCloud
    properties:
      availability:
        secondaryZone: 2
        strategy: DualZone
        zone: 1
      location: eastus2
      managementCluster:
        clusterSize: 4
      networkBlock: 192.168.48.0/22
      privateCloudName: cloud1
      resourceGroupName: group1
      sku:
        name: AV36
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:PrivateCloud cloud1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1 
```
