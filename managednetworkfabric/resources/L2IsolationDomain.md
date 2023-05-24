The L2IsolationDomain resource definition.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### L2IsolationDomains_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var l2IsolationDomain = new AzureNative.ManagedNetworkFabric.L2IsolationDomain("l2IsolationDomain", new()
    {
        L2IsolationDomainName = "example-l2domain",
        Location = "eastus",
        Mtu = 1500,
        NetworkFabricId = "/subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName",
        ResourceGroupName = "resourceGroupName",
        VlanId = 501,
    });

});


```

```go
package main

import (
	managednetworkfabric "github.com/pulumi/pulumi-azure-native-sdk/managednetworkfabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managednetworkfabric.NewL2IsolationDomain(ctx, "l2IsolationDomain", &managednetworkfabric.L2IsolationDomainArgs{
			L2IsolationDomainName: pulumi.String("example-l2domain"),
			Location:              pulumi.String("eastus"),
			Mtu:                   pulumi.Int(1500),
			NetworkFabricId:       pulumi.String("/subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName"),
			ResourceGroupName:     pulumi.String("resourceGroupName"),
			VlanId:                pulumi.Int(501),
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
import com.pulumi.azurenative.managednetworkfabric.L2IsolationDomain;
import com.pulumi.azurenative.managednetworkfabric.L2IsolationDomainArgs;
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
        var l2IsolationDomain = new L2IsolationDomain("l2IsolationDomain", L2IsolationDomainArgs.builder()        
            .l2IsolationDomainName("example-l2domain")
            .location("eastus")
            .mtu(1500)
            .networkFabricId("/subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName")
            .resourceGroupName("resourceGroupName")
            .vlanId(501)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const l2IsolationDomain = new azure_native.managednetworkfabric.L2IsolationDomain("l2IsolationDomain", {
    l2IsolationDomainName: "example-l2domain",
    location: "eastus",
    mtu: 1500,
    networkFabricId: "/subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName",
    resourceGroupName: "resourceGroupName",
    vlanId: 501,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

l2_isolation_domain = azure_native.managednetworkfabric.L2IsolationDomain("l2IsolationDomain",
    l2_isolation_domain_name="example-l2domain",
    location="eastus",
    mtu=1500,
    network_fabric_id="/subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName",
    resource_group_name="resourceGroupName",
    vlan_id=501)

```

```yaml
resources:
  l2IsolationDomain:
    type: azure-native:managednetworkfabric:L2IsolationDomain
    properties:
      l2IsolationDomainName: example-l2domain
      location: eastus
      mtu: 1500
      networkFabricId: /subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/networkFabrics/FabricName
      resourceGroupName: resourceGroupName
      vlanId: 501

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:L2IsolationDomain wcpalyqmig /subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/l2IsolationDomains/example-l2domain 
```
