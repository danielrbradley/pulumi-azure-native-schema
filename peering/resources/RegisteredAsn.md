The customer's ASN that is registered by the peering service provider.
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a registered ASN for the peering
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registeredAsn = new AzureNative.Peering.RegisteredAsn("registeredAsn", new()
    {
        Asn = 65000,
        PeeringName = "peeringName",
        RegisteredAsnName = "registeredAsnName",
        ResourceGroupName = "rgName",
    });

});


```

```go
package main

import (
	peering "github.com/pulumi/pulumi-azure-native-sdk/peering"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := peering.NewRegisteredAsn(ctx, "registeredAsn", &peering.RegisteredAsnArgs{
			Asn:               pulumi.Int(65000),
			PeeringName:       pulumi.String("peeringName"),
			RegisteredAsnName: pulumi.String("registeredAsnName"),
			ResourceGroupName: pulumi.String("rgName"),
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
import com.pulumi.azurenative.peering.RegisteredAsn;
import com.pulumi.azurenative.peering.RegisteredAsnArgs;
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
        var registeredAsn = new RegisteredAsn("registeredAsn", RegisteredAsnArgs.builder()        
            .asn(65000)
            .peeringName("peeringName")
            .registeredAsnName("registeredAsnName")
            .resourceGroupName("rgName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registeredAsn = new azure_native.peering.RegisteredAsn("registeredAsn", {
    asn: 65000,
    peeringName: "peeringName",
    registeredAsnName: "registeredAsnName",
    resourceGroupName: "rgName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registered_asn = azure_native.peering.RegisteredAsn("registeredAsn",
    asn=65000,
    peering_name="peeringName",
    registered_asn_name="registeredAsnName",
    resource_group_name="rgName")

```

```yaml
resources:
  registeredAsn:
    type: azure-native:peering:RegisteredAsn
    properties:
      asn: 65000
      peeringName: peeringName
      registeredAsnName: registeredAsnName
      resourceGroupName: rgName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:peering:RegisteredAsn registeredAsnName /subscriptions/subId/resourceGroups/rgName/providers/Microsoft.Peering/peerings/peeringName/registeredAsns/registeredAsnName 
```
