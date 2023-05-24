An HCX Enterprise Site resource
API Version: 2022-05-01.
Previous API Version: 2020-03-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### HcxEnterpriseSites_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hcxEnterpriseSite = new AzureNative.AVS.HcxEnterpriseSite("hcxEnterpriseSite", new()
    {
        HcxEnterpriseSiteName = "site1",
        PrivateCloudName = "cloud1",
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
		_, err := avs.NewHcxEnterpriseSite(ctx, "hcxEnterpriseSite", &avs.HcxEnterpriseSiteArgs{
			HcxEnterpriseSiteName: pulumi.String("site1"),
			PrivateCloudName:      pulumi.String("cloud1"),
			ResourceGroupName:     pulumi.String("group1"),
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
import com.pulumi.azurenative.avs.HcxEnterpriseSite;
import com.pulumi.azurenative.avs.HcxEnterpriseSiteArgs;
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
        var hcxEnterpriseSite = new HcxEnterpriseSite("hcxEnterpriseSite", HcxEnterpriseSiteArgs.builder()        
            .hcxEnterpriseSiteName("site1")
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hcxEnterpriseSite = new azure_native.avs.HcxEnterpriseSite("hcxEnterpriseSite", {
    hcxEnterpriseSiteName: "site1",
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hcx_enterprise_site = azure_native.avs.HcxEnterpriseSite("hcxEnterpriseSite",
    hcx_enterprise_site_name="site1",
    private_cloud_name="cloud1",
    resource_group_name="group1")

```

```yaml
resources:
  hcxEnterpriseSite:
    type: azure-native:avs:HcxEnterpriseSite
    properties:
      hcxEnterpriseSiteName: site1
      privateCloudName: cloud1
      resourceGroupName: group1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:HcxEnterpriseSite site1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/hcxEnterpriseSites/site1 
```
