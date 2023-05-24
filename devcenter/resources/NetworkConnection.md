Network related settings
API Version: 2022-11-11-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NetworkConnections_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkConnection = new AzureNative.DevCenter.NetworkConnection("networkConnection", new()
    {
        DomainJoinType = "HybridAzureADJoin",
        DomainName = "mydomaincontroller.local",
        DomainPassword = "Password value for user",
        DomainUsername = "testuser@mydomaincontroller.local",
        Location = "centralus",
        NetworkConnectionName = "uswest3network",
        NetworkingResourceGroupName = "NetworkInterfaces",
        ResourceGroupName = "rg1",
        SubnetId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default",
    });

});


```

```go
package main

import (
	devcenter "github.com/pulumi/pulumi-azure-native-sdk/devcenter"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devcenter.NewNetworkConnection(ctx, "networkConnection", &devcenter.NetworkConnectionArgs{
			DomainJoinType:              pulumi.String("HybridAzureADJoin"),
			DomainName:                  pulumi.String("mydomaincontroller.local"),
			DomainPassword:              pulumi.String("Password value for user"),
			DomainUsername:              pulumi.String("testuser@mydomaincontroller.local"),
			Location:                    pulumi.String("centralus"),
			NetworkConnectionName:       pulumi.String("uswest3network"),
			NetworkingResourceGroupName: pulumi.String("NetworkInterfaces"),
			ResourceGroupName:           pulumi.String("rg1"),
			SubnetId:                    pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default"),
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
import com.pulumi.azurenative.devcenter.NetworkConnection;
import com.pulumi.azurenative.devcenter.NetworkConnectionArgs;
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
        var networkConnection = new NetworkConnection("networkConnection", NetworkConnectionArgs.builder()        
            .domainJoinType("HybridAzureADJoin")
            .domainName("mydomaincontroller.local")
            .domainPassword("Password value for user")
            .domainUsername("testuser@mydomaincontroller.local")
            .location("centralus")
            .networkConnectionName("uswest3network")
            .networkingResourceGroupName("NetworkInterfaces")
            .resourceGroupName("rg1")
            .subnetId("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkConnection = new azure_native.devcenter.NetworkConnection("networkConnection", {
    domainJoinType: "HybridAzureADJoin",
    domainName: "mydomaincontroller.local",
    domainPassword: "Password value for user",
    domainUsername: "testuser@mydomaincontroller.local",
    location: "centralus",
    networkConnectionName: "uswest3network",
    networkingResourceGroupName: "NetworkInterfaces",
    resourceGroupName: "rg1",
    subnetId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_connection = azure_native.devcenter.NetworkConnection("networkConnection",
    domain_join_type="HybridAzureADJoin",
    domain_name="mydomaincontroller.local",
    domain_password="Password value for user",
    domain_username="testuser@mydomaincontroller.local",
    location="centralus",
    network_connection_name="uswest3network",
    networking_resource_group_name="NetworkInterfaces",
    resource_group_name="rg1",
    subnet_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default")

```

```yaml
resources:
  networkConnection:
    type: azure-native:devcenter:NetworkConnection
    properties:
      domainJoinType: HybridAzureADJoin
      domainName: mydomaincontroller.local
      domainPassword: Password value for user
      domainUsername: testuser@mydomaincontroller.local
      location: centralus
      networkConnectionName: uswest3network
      networkingResourceGroupName: NetworkInterfaces
      resourceGroupName: rg1
      subnetId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devcenter:NetworkConnection uswest3network /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/networkconnections/uswest3network 
```
