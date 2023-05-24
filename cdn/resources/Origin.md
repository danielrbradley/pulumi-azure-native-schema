CDN origin is the source of the content being delivered via CDN. When the edge nodes represented by an endpoint do not have the requested content cached, they attempt to fetch it from one or more of the configured origins.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Origins_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var origin = new AzureNative.Cdn.Origin("origin", new()
    {
        Enabled = true,
        EndpointName = "endpoint1",
        HostName = "www.someDomain.net",
        HttpPort = 80,
        HttpsPort = 443,
        OriginHostHeader = "www.someDomain.net",
        OriginName = "www-someDomain-net",
        Priority = 1,
        PrivateLinkApprovalMessage = "Please approve the connection request for this Private Link",
        PrivateLinkLocation = "eastus",
        PrivateLinkResourceId = "/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1",
        ProfileName = "profile1",
        ResourceGroupName = "RG",
        Weight = 50,
    });

});


```

```go
package main

import (
	cdn "github.com/pulumi/pulumi-azure-native-sdk/cdn"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cdn.NewOrigin(ctx, "origin", &cdn.OriginArgs{
			Enabled:                    pulumi.Bool(true),
			EndpointName:               pulumi.String("endpoint1"),
			HostName:                   pulumi.String("www.someDomain.net"),
			HttpPort:                   pulumi.Int(80),
			HttpsPort:                  pulumi.Int(443),
			OriginHostHeader:           pulumi.String("www.someDomain.net"),
			OriginName:                 pulumi.String("www-someDomain-net"),
			Priority:                   pulumi.Int(1),
			PrivateLinkApprovalMessage: pulumi.String("Please approve the connection request for this Private Link"),
			PrivateLinkLocation:        pulumi.String("eastus"),
			PrivateLinkResourceId:      pulumi.String("/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1"),
			ProfileName:                pulumi.String("profile1"),
			ResourceGroupName:          pulumi.String("RG"),
			Weight:                     pulumi.Int(50),
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
import com.pulumi.azurenative.cdn.Origin;
import com.pulumi.azurenative.cdn.OriginArgs;
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
        var origin = new Origin("origin", OriginArgs.builder()        
            .enabled(true)
            .endpointName("endpoint1")
            .hostName("www.someDomain.net")
            .httpPort(80)
            .httpsPort(443)
            .originHostHeader("www.someDomain.net")
            .originName("www-someDomain-net")
            .priority(1)
            .privateLinkApprovalMessage("Please approve the connection request for this Private Link")
            .privateLinkLocation("eastus")
            .privateLinkResourceId("/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1")
            .profileName("profile1")
            .resourceGroupName("RG")
            .weight(50)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const origin = new azure_native.cdn.Origin("origin", {
    enabled: true,
    endpointName: "endpoint1",
    hostName: "www.someDomain.net",
    httpPort: 80,
    httpsPort: 443,
    originHostHeader: "www.someDomain.net",
    originName: "www-someDomain-net",
    priority: 1,
    privateLinkApprovalMessage: "Please approve the connection request for this Private Link",
    privateLinkLocation: "eastus",
    privateLinkResourceId: "/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1",
    profileName: "profile1",
    resourceGroupName: "RG",
    weight: 50,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

origin = azure_native.cdn.Origin("origin",
    enabled=True,
    endpoint_name="endpoint1",
    host_name="www.someDomain.net",
    http_port=80,
    https_port=443,
    origin_host_header="www.someDomain.net",
    origin_name="www-someDomain-net",
    priority=1,
    private_link_approval_message="Please approve the connection request for this Private Link",
    private_link_location="eastus",
    private_link_resource_id="/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1",
    profile_name="profile1",
    resource_group_name="RG",
    weight=50)

```

```yaml
resources:
  origin:
    type: azure-native:cdn:Origin
    properties:
      enabled: true
      endpointName: endpoint1
      hostName: www.someDomain.net
      httpPort: 80
      httpsPort: 443
      originHostHeader: www.someDomain.net
      originName: www-someDomain-net
      priority: 1
      privateLinkApprovalMessage: Please approve the connection request for this Private Link
      privateLinkLocation: eastus
      privateLinkResourceId: /subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1
      profileName: profile1
      resourceGroupName: RG
      weight: 50

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:Origin www-someDomain-net /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/www-someDomain-net 
```
