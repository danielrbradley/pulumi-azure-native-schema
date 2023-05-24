The Network Manager Connection resource
API Version: 2022-09-01.
Previous API Version: 2022-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Subscription Network Manager Connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var subscriptionNetworkManagerConnection = new AzureNative.Network.SubscriptionNetworkManagerConnection("subscriptionNetworkManagerConnection", new()
    {
        NetworkManagerConnectionName = "TestNMConnection",
        NetworkManagerId = "/subscriptions/subscriptionC/resourceGroup/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewSubscriptionNetworkManagerConnection(ctx, "subscriptionNetworkManagerConnection", &network.SubscriptionNetworkManagerConnectionArgs{
			NetworkManagerConnectionName: pulumi.String("TestNMConnection"),
			NetworkManagerId:             pulumi.String("/subscriptions/subscriptionC/resourceGroup/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager"),
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
import com.pulumi.azurenative.network.SubscriptionNetworkManagerConnection;
import com.pulumi.azurenative.network.SubscriptionNetworkManagerConnectionArgs;
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
        var subscriptionNetworkManagerConnection = new SubscriptionNetworkManagerConnection("subscriptionNetworkManagerConnection", SubscriptionNetworkManagerConnectionArgs.builder()        
            .networkManagerConnectionName("TestNMConnection")
            .networkManagerId("/subscriptions/subscriptionC/resourceGroup/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const subscriptionNetworkManagerConnection = new azure_native.network.SubscriptionNetworkManagerConnection("subscriptionNetworkManagerConnection", {
    networkManagerConnectionName: "TestNMConnection",
    networkManagerId: "/subscriptions/subscriptionC/resourceGroup/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

subscription_network_manager_connection = azure_native.network.SubscriptionNetworkManagerConnection("subscriptionNetworkManagerConnection",
    network_manager_connection_name="TestNMConnection",
    network_manager_id="/subscriptions/subscriptionC/resourceGroup/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager")

```

```yaml
resources:
  subscriptionNetworkManagerConnection:
    type: azure-native:network:SubscriptionNetworkManagerConnection
    properties:
      networkManagerConnectionName: TestNMConnection
      networkManagerId: /subscriptions/subscriptionC/resourceGroup/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:SubscriptionNetworkManagerConnection TestNMConnection /subscriptions/00000000-0000-0000-0000-000000000000/providers/Microsoft.Network/networkManagerConnections/TestNMConnection 
```
