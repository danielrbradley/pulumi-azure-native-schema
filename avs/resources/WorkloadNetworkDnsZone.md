NSX DNS Zone
API Version: 2022-05-01.
Previous API Version: 2020-07-17-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkloadNetworks_CreateDnsZone
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workloadNetworkDnsZone = new AzureNative.AVS.WorkloadNetworkDnsZone("workloadNetworkDnsZone", new()
    {
        DisplayName = "dnsZone1",
        DnsServerIps = new[]
        {
            "1.1.1.1",
        },
        DnsZoneId = "dnsZone1",
        Domain = new[] {},
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
        Revision = 1,
        SourceIp = "8.8.8.8",
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
		_, err := avs.NewWorkloadNetworkDnsZone(ctx, "workloadNetworkDnsZone", &avs.WorkloadNetworkDnsZoneArgs{
			DisplayName: pulumi.String("dnsZone1"),
			DnsServerIps: pulumi.StringArray{
				pulumi.String("1.1.1.1"),
			},
			DnsZoneId:         pulumi.String("dnsZone1"),
			Domain:            pulumi.StringArray{},
			PrivateCloudName:  pulumi.String("cloud1"),
			ResourceGroupName: pulumi.String("group1"),
			Revision:          pulumi.Float64(1),
			SourceIp:          pulumi.String("8.8.8.8"),
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
import com.pulumi.azurenative.avs.WorkloadNetworkDnsZone;
import com.pulumi.azurenative.avs.WorkloadNetworkDnsZoneArgs;
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
        var workloadNetworkDnsZone = new WorkloadNetworkDnsZone("workloadNetworkDnsZone", WorkloadNetworkDnsZoneArgs.builder()        
            .displayName("dnsZone1")
            .dnsServerIps("1.1.1.1")
            .dnsZoneId("dnsZone1")
            .domain()
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .revision(1)
            .sourceIp("8.8.8.8")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workloadNetworkDnsZone = new azure_native.avs.WorkloadNetworkDnsZone("workloadNetworkDnsZone", {
    displayName: "dnsZone1",
    dnsServerIps: ["1.1.1.1"],
    dnsZoneId: "dnsZone1",
    domain: [],
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
    revision: 1,
    sourceIp: "8.8.8.8",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workload_network_dns_zone = azure_native.avs.WorkloadNetworkDnsZone("workloadNetworkDnsZone",
    display_name="dnsZone1",
    dns_server_ips=["1.1.1.1"],
    dns_zone_id="dnsZone1",
    domain=[],
    private_cloud_name="cloud1",
    resource_group_name="group1",
    revision=1,
    source_ip="8.8.8.8")

```

```yaml
resources:
  workloadNetworkDnsZone:
    type: azure-native:avs:WorkloadNetworkDnsZone
    properties:
      displayName: dnsZone1
      dnsServerIps:
        - 1.1.1.1
      dnsZoneId: dnsZone1
      domain: []
      privateCloudName: cloud1
      resourceGroupName: group1
      revision: 1
      sourceIp: 8.8.8.8

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:WorkloadNetworkDnsZone dnsZone1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/workloadNetworks/default/dnsZones/dnsZone1 
```
