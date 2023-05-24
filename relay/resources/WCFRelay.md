Description of the WCF relay resource.
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RelayCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var wcfRelay = new AzureNative.Relay.WCFRelay("wcfRelay", new()
    {
        NamespaceName = "example-RelayNamespace-9953",
        RelayName = "example-Relay-Wcf-1194",
        RelayType = AzureNative.Relay.Relaytype.NetTcp,
        RequiresClientAuthorization = true,
        RequiresTransportSecurity = true,
        ResourceGroupName = "resourcegroup",
    });

});


```

```go
package main

import (
	relay "github.com/pulumi/pulumi-azure-native-sdk/relay"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := relay.NewWCFRelay(ctx, "wcfRelay", &relay.WCFRelayArgs{
			NamespaceName:               pulumi.String("example-RelayNamespace-9953"),
			RelayName:                   pulumi.String("example-Relay-Wcf-1194"),
			RelayType:                   relay.RelaytypeNetTcp,
			RequiresClientAuthorization: pulumi.Bool(true),
			RequiresTransportSecurity:   pulumi.Bool(true),
			ResourceGroupName:           pulumi.String("resourcegroup"),
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
import com.pulumi.azurenative.relay.WCFRelay;
import com.pulumi.azurenative.relay.WCFRelayArgs;
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
        var wcfRelay = new WCFRelay("wcfRelay", WCFRelayArgs.builder()        
            .namespaceName("example-RelayNamespace-9953")
            .relayName("example-Relay-Wcf-1194")
            .relayType("NetTcp")
            .requiresClientAuthorization(true)
            .requiresTransportSecurity(true)
            .resourceGroupName("resourcegroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const wcfRelay = new azure_native.relay.WCFRelay("wcfRelay", {
    namespaceName: "example-RelayNamespace-9953",
    relayName: "example-Relay-Wcf-1194",
    relayType: azure_native.relay.Relaytype.NetTcp,
    requiresClientAuthorization: true,
    requiresTransportSecurity: true,
    resourceGroupName: "resourcegroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

wcf_relay = azure_native.relay.WCFRelay("wcfRelay",
    namespace_name="example-RelayNamespace-9953",
    relay_name="example-Relay-Wcf-1194",
    relay_type=azure_native.relay.Relaytype.NET_TCP,
    requires_client_authorization=True,
    requires_transport_security=True,
    resource_group_name="resourcegroup")

```

```yaml
resources:
  wcfRelay:
    type: azure-native:relay:WCFRelay
    properties:
      namespaceName: example-RelayNamespace-9953
      relayName: example-Relay-Wcf-1194
      relayType: NetTcp
      requiresClientAuthorization: true
      requiresTransportSecurity: true
      resourceGroupName: resourcegroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:relay:WCFRelay example-Relay-Wcf-1194 /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/resourcegroup/providers/Microsoft.Relay/namespaces/example-RelayNamespace-9953/WcfRelays/example-Relay-Wcf-1194 
```
