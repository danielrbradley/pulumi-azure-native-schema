The essential information related to the peer's ASN.
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a peer ASN
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var peerAsn = new AzureNative.Peering.PeerAsn("peerAsn", new()
    {
        PeerAsn = 65000,
        PeerAsnName = "peerAsnName",
        PeerContactDetail = new[]
        {
            new AzureNative.Peering.Inputs.ContactDetailArgs
            {
                Email = "noc@contoso.com",
                Phone = "+1 (234) 567-8999",
                Role = "Noc",
            },
            new AzureNative.Peering.Inputs.ContactDetailArgs
            {
                Email = "abc@contoso.com",
                Phone = "+1 (234) 567-8900",
                Role = "Policy",
            },
            new AzureNative.Peering.Inputs.ContactDetailArgs
            {
                Email = "xyz@contoso.com",
                Phone = "+1 (234) 567-8900",
                Role = "Technical",
            },
        },
        PeerName = "Contoso",
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
		_, err := peering.NewPeerAsn(ctx, "peerAsn", &peering.PeerAsnArgs{
			PeerAsn:     pulumi.Int(65000),
			PeerAsnName: pulumi.String("peerAsnName"),
			PeerContactDetail: []peering.ContactDetailArgs{
				{
					Email: pulumi.String("noc@contoso.com"),
					Phone: pulumi.String("+1 (234) 567-8999"),
					Role:  pulumi.String("Noc"),
				},
				{
					Email: pulumi.String("abc@contoso.com"),
					Phone: pulumi.String("+1 (234) 567-8900"),
					Role:  pulumi.String("Policy"),
				},
				{
					Email: pulumi.String("xyz@contoso.com"),
					Phone: pulumi.String("+1 (234) 567-8900"),
					Role:  pulumi.String("Technical"),
				},
			},
			PeerName: pulumi.String("Contoso"),
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
import com.pulumi.azurenative.peering.PeerAsn;
import com.pulumi.azurenative.peering.PeerAsnArgs;
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
        var peerAsn = new PeerAsn("peerAsn", PeerAsnArgs.builder()        
            .peerAsn(65000)
            .peerAsnName("peerAsnName")
            .peerContactDetail(            
                Map.ofEntries(
                    Map.entry("email", "noc@contoso.com"),
                    Map.entry("phone", "+1 (234) 567-8999"),
                    Map.entry("role", "Noc")
                ),
                Map.ofEntries(
                    Map.entry("email", "abc@contoso.com"),
                    Map.entry("phone", "+1 (234) 567-8900"),
                    Map.entry("role", "Policy")
                ),
                Map.ofEntries(
                    Map.entry("email", "xyz@contoso.com"),
                    Map.entry("phone", "+1 (234) 567-8900"),
                    Map.entry("role", "Technical")
                ))
            .peerName("Contoso")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const peerAsn = new azure_native.peering.PeerAsn("peerAsn", {
    peerAsn: 65000,
    peerAsnName: "peerAsnName",
    peerContactDetail: [
        {
            email: "noc@contoso.com",
            phone: "+1 (234) 567-8999",
            role: "Noc",
        },
        {
            email: "abc@contoso.com",
            phone: "+1 (234) 567-8900",
            role: "Policy",
        },
        {
            email: "xyz@contoso.com",
            phone: "+1 (234) 567-8900",
            role: "Technical",
        },
    ],
    peerName: "Contoso",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

peer_asn = azure_native.peering.PeerAsn("peerAsn",
    peer_asn=65000,
    peer_asn_name="peerAsnName",
    peer_contact_detail=[
        azure_native.peering.ContactDetailArgs(
            email="noc@contoso.com",
            phone="+1 (234) 567-8999",
            role="Noc",
        ),
        azure_native.peering.ContactDetailArgs(
            email="abc@contoso.com",
            phone="+1 (234) 567-8900",
            role="Policy",
        ),
        azure_native.peering.ContactDetailArgs(
            email="xyz@contoso.com",
            phone="+1 (234) 567-8900",
            role="Technical",
        ),
    ],
    peer_name="Contoso")

```

```yaml
resources:
  peerAsn:
    type: azure-native:peering:PeerAsn
    properties:
      peerAsn: 65000
      peerAsnName: peerAsnName
      peerContactDetail:
        - email: noc@contoso.com
          phone: +1 (234) 567-8999
          role: Noc
        - email: abc@contoso.com
          phone: +1 (234) 567-8900
          role: Policy
        - email: xyz@contoso.com
          phone: +1 (234) 567-8900
          role: Technical
      peerName: Contoso

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:peering:PeerAsn peerAsnName /subscriptions/subId/providers/Microsoft.Peering/peerAsns/peerAsnName 
```
