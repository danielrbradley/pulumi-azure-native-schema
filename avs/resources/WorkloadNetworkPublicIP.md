NSX Public IP Block
API Version: 2022-05-01.
Previous API Version: 2021-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkloadNetworks_CreatePublicIP
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workloadNetworkPublicIP = new AzureNative.AVS.WorkloadNetworkPublicIP("workloadNetworkPublicIP", new()
    {
        DisplayName = "publicIP1",
        NumberOfPublicIPs = 32,
        PrivateCloudName = "cloud1",
        PublicIPId = "publicIP1",
        ResourceGroupName = "group1",
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
		_, err := avs.NewWorkloadNetworkPublicIP(ctx, "workloadNetworkPublicIP", &avs.WorkloadNetworkPublicIPArgs{
			DisplayName:       pulumi.String("publicIP1"),
			NumberOfPublicIPs: pulumi.Float64(32),
			PrivateCloudName:  pulumi.String("cloud1"),
			PublicIPId:        pulumi.String("publicIP1"),
			ResourceGroupName: pulumi.String("group1"),
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
import com.pulumi.azurenative.avs.WorkloadNetworkPublicIP;
import com.pulumi.azurenative.avs.WorkloadNetworkPublicIPArgs;
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
        var workloadNetworkPublicIP = new WorkloadNetworkPublicIP("workloadNetworkPublicIP", WorkloadNetworkPublicIPArgs.builder()        
            .displayName("publicIP1")
            .numberOfPublicIPs(32)
            .privateCloudName("cloud1")
            .publicIPId("publicIP1")
            .resourceGroupName("group1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workloadNetworkPublicIP = new azure_native.avs.WorkloadNetworkPublicIP("workloadNetworkPublicIP", {
    displayName: "publicIP1",
    numberOfPublicIPs: 32,
    privateCloudName: "cloud1",
    publicIPId: "publicIP1",
    resourceGroupName: "group1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workload_network_public_ip = azure_native.avs.WorkloadNetworkPublicIP("workloadNetworkPublicIP",
    display_name="publicIP1",
    number_of_public_ips=32,
    private_cloud_name="cloud1",
    public_ip_id="publicIP1",
    resource_group_name="group1")

```

```yaml
resources:
  workloadNetworkPublicIP:
    type: azure-native:avs:WorkloadNetworkPublicIP
    properties:
      displayName: publicIP1
      numberOfPublicIPs: 32
      privateCloudName: cloud1
      publicIPId: publicIP1
      resourceGroupName: group1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:WorkloadNetworkPublicIP publicIP1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/workloadNetworks/default/publicIPs/publicIP1 
```
