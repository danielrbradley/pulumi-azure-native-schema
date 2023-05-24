NSX Segment
API Version: 2022-05-01.
Previous API Version: 2020-07-17-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkloadNetworks_CreateSegments
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workloadNetworkSegment = new AzureNative.AVS.WorkloadNetworkSegment("workloadNetworkSegment", new()
    {
        ConnectedGateway = "/infra/tier-1s/gateway",
        DisplayName = "segment1",
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
        Revision = 1,
        SegmentId = "segment1",
        Subnet = new AzureNative.AVS.Inputs.WorkloadNetworkSegmentSubnetArgs
        {
            DhcpRanges = new[]
            {
                "40.20.0.0-40.20.0.1",
            },
            GatewayAddress = "40.20.20.20/16",
        },
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
		_, err := avs.NewWorkloadNetworkSegment(ctx, "workloadNetworkSegment", &avs.WorkloadNetworkSegmentArgs{
			ConnectedGateway:  pulumi.String("/infra/tier-1s/gateway"),
			DisplayName:       pulumi.String("segment1"),
			PrivateCloudName:  pulumi.String("cloud1"),
			ResourceGroupName: pulumi.String("group1"),
			Revision:          pulumi.Float64(1),
			SegmentId:         pulumi.String("segment1"),
			Subnet: &avs.WorkloadNetworkSegmentSubnetArgs{
				DhcpRanges: pulumi.StringArray{
					pulumi.String("40.20.0.0-40.20.0.1"),
				},
				GatewayAddress: pulumi.String("40.20.20.20/16"),
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
import com.pulumi.azurenative.avs.WorkloadNetworkSegment;
import com.pulumi.azurenative.avs.WorkloadNetworkSegmentArgs;
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
        var workloadNetworkSegment = new WorkloadNetworkSegment("workloadNetworkSegment", WorkloadNetworkSegmentArgs.builder()        
            .connectedGateway("/infra/tier-1s/gateway")
            .displayName("segment1")
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .revision(1)
            .segmentId("segment1")
            .subnet(Map.ofEntries(
                Map.entry("dhcpRanges", "40.20.0.0-40.20.0.1"),
                Map.entry("gatewayAddress", "40.20.20.20/16")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workloadNetworkSegment = new azure_native.avs.WorkloadNetworkSegment("workloadNetworkSegment", {
    connectedGateway: "/infra/tier-1s/gateway",
    displayName: "segment1",
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
    revision: 1,
    segmentId: "segment1",
    subnet: {
        dhcpRanges: ["40.20.0.0-40.20.0.1"],
        gatewayAddress: "40.20.20.20/16",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workload_network_segment = azure_native.avs.WorkloadNetworkSegment("workloadNetworkSegment",
    connected_gateway="/infra/tier-1s/gateway",
    display_name="segment1",
    private_cloud_name="cloud1",
    resource_group_name="group1",
    revision=1,
    segment_id="segment1",
    subnet=azure_native.avs.WorkloadNetworkSegmentSubnetArgs(
        dhcp_ranges=["40.20.0.0-40.20.0.1"],
        gateway_address="40.20.20.20/16",
    ))

```

```yaml
resources:
  workloadNetworkSegment:
    type: azure-native:avs:WorkloadNetworkSegment
    properties:
      connectedGateway: /infra/tier-1s/gateway
      displayName: segment1
      privateCloudName: cloud1
      resourceGroupName: group1
      revision: 1
      segmentId: segment1
      subnet:
        dhcpRanges:
          - 40.20.0.0-40.20.0.1
        gatewayAddress: 40.20.20.20/16

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:WorkloadNetworkSegment segment1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/workloadNetworks/default/segments/segment1 
```
