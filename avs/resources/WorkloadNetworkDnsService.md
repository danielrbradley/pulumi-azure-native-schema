NSX DNS Service
API Version: 2022-05-01.
Previous API Version: 2020-07-17-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkloadNetworks_CreateDnsService
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workloadNetworkDnsService = new AzureNative.AVS.WorkloadNetworkDnsService("workloadNetworkDnsService", new()
    {
        DefaultDnsZone = "defaultDnsZone1",
        DisplayName = "dnsService1",
        DnsServiceId = "dnsService1",
        DnsServiceIp = "5.5.5.5",
        FqdnZones = new[]
        {
            "fqdnZone1",
        },
        LogLevel = "INFO",
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
        Revision = 1,
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
		_, err := avs.NewWorkloadNetworkDnsService(ctx, "workloadNetworkDnsService", &avs.WorkloadNetworkDnsServiceArgs{
			DefaultDnsZone: pulumi.String("defaultDnsZone1"),
			DisplayName:    pulumi.String("dnsService1"),
			DnsServiceId:   pulumi.String("dnsService1"),
			DnsServiceIp:   pulumi.String("5.5.5.5"),
			FqdnZones: pulumi.StringArray{
				pulumi.String("fqdnZone1"),
			},
			LogLevel:          pulumi.String("INFO"),
			PrivateCloudName:  pulumi.String("cloud1"),
			ResourceGroupName: pulumi.String("group1"),
			Revision:          pulumi.Float64(1),
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
import com.pulumi.azurenative.avs.WorkloadNetworkDnsService;
import com.pulumi.azurenative.avs.WorkloadNetworkDnsServiceArgs;
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
        var workloadNetworkDnsService = new WorkloadNetworkDnsService("workloadNetworkDnsService", WorkloadNetworkDnsServiceArgs.builder()        
            .defaultDnsZone("defaultDnsZone1")
            .displayName("dnsService1")
            .dnsServiceId("dnsService1")
            .dnsServiceIp("5.5.5.5")
            .fqdnZones("fqdnZone1")
            .logLevel("INFO")
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .revision(1)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workloadNetworkDnsService = new azure_native.avs.WorkloadNetworkDnsService("workloadNetworkDnsService", {
    defaultDnsZone: "defaultDnsZone1",
    displayName: "dnsService1",
    dnsServiceId: "dnsService1",
    dnsServiceIp: "5.5.5.5",
    fqdnZones: ["fqdnZone1"],
    logLevel: "INFO",
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
    revision: 1,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workload_network_dns_service = azure_native.avs.WorkloadNetworkDnsService("workloadNetworkDnsService",
    default_dns_zone="defaultDnsZone1",
    display_name="dnsService1",
    dns_service_id="dnsService1",
    dns_service_ip="5.5.5.5",
    fqdn_zones=["fqdnZone1"],
    log_level="INFO",
    private_cloud_name="cloud1",
    resource_group_name="group1",
    revision=1)

```

```yaml
resources:
  workloadNetworkDnsService:
    type: azure-native:avs:WorkloadNetworkDnsService
    properties:
      defaultDnsZone: defaultDnsZone1
      displayName: dnsService1
      dnsServiceId: dnsService1
      dnsServiceIp: 5.5.5.5
      fqdnZones:
        - fqdnZone1
      logLevel: INFO
      privateCloudName: cloud1
      resourceGroupName: group1
      revision: 1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:WorkloadNetworkDnsService dnsService1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/workloadNetworks/default/dnsServices/dnsService1 
```
