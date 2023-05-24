Site resource. Must be created in the same location as its parent mobile network.
API Version: 2022-11-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create mobile network site
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var site = new AzureNative.MobileNetwork.Site("site", new()
    {
        Location = "testLocation",
        MobileNetworkName = "testMobileNetwork",
        ResourceGroupName = "rg1",
        SiteName = "testSite",
    });

});


```

```go
package main

import (
	mobilenetwork "github.com/pulumi/pulumi-azure-native-sdk/mobilenetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := mobilenetwork.NewSite(ctx, "site", &mobilenetwork.SiteArgs{
			Location:          pulumi.String("testLocation"),
			MobileNetworkName: pulumi.String("testMobileNetwork"),
			ResourceGroupName: pulumi.String("rg1"),
			SiteName:          pulumi.String("testSite"),
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
import com.pulumi.azurenative.mobilenetwork.Site;
import com.pulumi.azurenative.mobilenetwork.SiteArgs;
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
        var site = new Site("site", SiteArgs.builder()        
            .location("testLocation")
            .mobileNetworkName("testMobileNetwork")
            .resourceGroupName("rg1")
            .siteName("testSite")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const site = new azure_native.mobilenetwork.Site("site", {
    location: "testLocation",
    mobileNetworkName: "testMobileNetwork",
    resourceGroupName: "rg1",
    siteName: "testSite",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

site = azure_native.mobilenetwork.Site("site",
    location="testLocation",
    mobile_network_name="testMobileNetwork",
    resource_group_name="rg1",
    site_name="testSite")

```

```yaml
resources:
  site:
    type: azure-native:mobilenetwork:Site
    properties:
      location: testLocation
      mobileNetworkName: testMobileNetwork
      resourceGroupName: rg1
      siteName: testSite

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mobilenetwork:Site testSite /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/sites/testSite 
```
