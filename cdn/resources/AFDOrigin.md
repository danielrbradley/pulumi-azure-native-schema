CDN origin is the source of the content being delivered via CDN. When the edge nodes represented by an endpoint do not have the requested content cached, they attempt to fetch it from one or more of the configured origins.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AFDOrigins_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var afdOrigin = new AzureNative.Cdn.AFDOrigin("afdOrigin", new()
    {
        EnabledState = "Enabled",
        HostName = "host1.blob.core.windows.net",
        HttpPort = 80,
        HttpsPort = 443,
        OriginGroupName = "origingroup1",
        OriginHostHeader = "host1.foo.com",
        OriginName = "origin1",
        ProfileName = "profile1",
        ResourceGroupName = "RG",
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
		_, err := cdn.NewAFDOrigin(ctx, "afdOrigin", &cdn.AFDOriginArgs{
			EnabledState:      pulumi.String("Enabled"),
			HostName:          pulumi.String("host1.blob.core.windows.net"),
			HttpPort:          pulumi.Int(80),
			HttpsPort:         pulumi.Int(443),
			OriginGroupName:   pulumi.String("origingroup1"),
			OriginHostHeader:  pulumi.String("host1.foo.com"),
			OriginName:        pulumi.String("origin1"),
			ProfileName:       pulumi.String("profile1"),
			ResourceGroupName: pulumi.String("RG"),
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
import com.pulumi.azurenative.cdn.AFDOrigin;
import com.pulumi.azurenative.cdn.AFDOriginArgs;
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
        var afdOrigin = new AFDOrigin("afdOrigin", AFDOriginArgs.builder()        
            .enabledState("Enabled")
            .hostName("host1.blob.core.windows.net")
            .httpPort(80)
            .httpsPort(443)
            .originGroupName("origingroup1")
            .originHostHeader("host1.foo.com")
            .originName("origin1")
            .profileName("profile1")
            .resourceGroupName("RG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const afdOrigin = new azure_native.cdn.AFDOrigin("afdOrigin", {
    enabledState: "Enabled",
    hostName: "host1.blob.core.windows.net",
    httpPort: 80,
    httpsPort: 443,
    originGroupName: "origingroup1",
    originHostHeader: "host1.foo.com",
    originName: "origin1",
    profileName: "profile1",
    resourceGroupName: "RG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

afd_origin = azure_native.cdn.AFDOrigin("afdOrigin",
    enabled_state="Enabled",
    host_name="host1.blob.core.windows.net",
    http_port=80,
    https_port=443,
    origin_group_name="origingroup1",
    origin_host_header="host1.foo.com",
    origin_name="origin1",
    profile_name="profile1",
    resource_group_name="RG")

```

```yaml
resources:
  afdOrigin:
    type: azure-native:cdn:AFDOrigin
    properties:
      enabledState: Enabled
      hostName: host1.blob.core.windows.net
      httpPort: 80
      httpsPort: 443
      originGroupName: origingroup1
      originHostHeader: host1.foo.com
      originName: origin1
      profileName: profile1
      resourceGroupName: RG

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:AFDOrigin origin1 /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/origingroups/origingroup1/origins/origin1 
```
