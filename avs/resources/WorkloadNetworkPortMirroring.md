NSX Port Mirroring
API Version: 2022-05-01.
Previous API Version: 2020-07-17-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkloadNetworks_CreatePortMirroring
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workloadNetworkPortMirroring = new AzureNative.AVS.WorkloadNetworkPortMirroring("workloadNetworkPortMirroring", new()
    {
        Destination = "vmGroup2",
        Direction = "BIDIRECTIONAL",
        DisplayName = "portMirroring1",
        PortMirroringId = "portMirroring1",
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
        Revision = 1,
        Source = "vmGroup1",
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
		_, err := avs.NewWorkloadNetworkPortMirroring(ctx, "workloadNetworkPortMirroring", &avs.WorkloadNetworkPortMirroringArgs{
			Destination:       pulumi.String("vmGroup2"),
			Direction:         pulumi.String("BIDIRECTIONAL"),
			DisplayName:       pulumi.String("portMirroring1"),
			PortMirroringId:   pulumi.String("portMirroring1"),
			PrivateCloudName:  pulumi.String("cloud1"),
			ResourceGroupName: pulumi.String("group1"),
			Revision:          pulumi.Float64(1),
			Source:            pulumi.String("vmGroup1"),
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
import com.pulumi.azurenative.avs.WorkloadNetworkPortMirroring;
import com.pulumi.azurenative.avs.WorkloadNetworkPortMirroringArgs;
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
        var workloadNetworkPortMirroring = new WorkloadNetworkPortMirroring("workloadNetworkPortMirroring", WorkloadNetworkPortMirroringArgs.builder()        
            .destination("vmGroup2")
            .direction("BIDIRECTIONAL")
            .displayName("portMirroring1")
            .portMirroringId("portMirroring1")
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .revision(1)
            .source("vmGroup1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workloadNetworkPortMirroring = new azure_native.avs.WorkloadNetworkPortMirroring("workloadNetworkPortMirroring", {
    destination: "vmGroup2",
    direction: "BIDIRECTIONAL",
    displayName: "portMirroring1",
    portMirroringId: "portMirroring1",
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
    revision: 1,
    source: "vmGroup1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workload_network_port_mirroring = azure_native.avs.WorkloadNetworkPortMirroring("workloadNetworkPortMirroring",
    destination="vmGroup2",
    direction="BIDIRECTIONAL",
    display_name="portMirroring1",
    port_mirroring_id="portMirroring1",
    private_cloud_name="cloud1",
    resource_group_name="group1",
    revision=1,
    source="vmGroup1")

```

```yaml
resources:
  workloadNetworkPortMirroring:
    type: azure-native:avs:WorkloadNetworkPortMirroring
    properties:
      destination: vmGroup2
      direction: BIDIRECTIONAL
      displayName: portMirroring1
      portMirroringId: portMirroring1
      privateCloudName: cloud1
      resourceGroupName: group1
      revision: 1
      source: vmGroup1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:WorkloadNetworkPortMirroring portMirroring1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/workloadNetworks/default/portMirroringProfiles/portMirroring1 
```
