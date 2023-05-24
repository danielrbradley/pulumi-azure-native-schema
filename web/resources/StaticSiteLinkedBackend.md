Static Site Linked Backend ARM resource.
API Version: 2022-09-01.
Previous API Version: 2022-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Link a backend to a static site
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var staticSiteLinkedBackend = new AzureNative.Web.StaticSiteLinkedBackend("staticSiteLinkedBackend", new()
    {
        BackendResourceId = "/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/backendRg/providers/Microsoft.Web/sites/testBackend",
        LinkedBackendName = "testBackend",
        Name = "testStaticSite0",
        Region = "West US 2",
        ResourceGroupName = "rg",
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewStaticSiteLinkedBackend(ctx, "staticSiteLinkedBackend", &web.StaticSiteLinkedBackendArgs{
			BackendResourceId: pulumi.String("/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/backendRg/providers/Microsoft.Web/sites/testBackend"),
			LinkedBackendName: pulumi.String("testBackend"),
			Name:              pulumi.String("testStaticSite0"),
			Region:            pulumi.String("West US 2"),
			ResourceGroupName: pulumi.String("rg"),
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
import com.pulumi.azurenative.web.StaticSiteLinkedBackend;
import com.pulumi.azurenative.web.StaticSiteLinkedBackendArgs;
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
        var staticSiteLinkedBackend = new StaticSiteLinkedBackend("staticSiteLinkedBackend", StaticSiteLinkedBackendArgs.builder()        
            .backendResourceId("/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/backendRg/providers/Microsoft.Web/sites/testBackend")
            .linkedBackendName("testBackend")
            .name("testStaticSite0")
            .region("West US 2")
            .resourceGroupName("rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const staticSiteLinkedBackend = new azure_native.web.StaticSiteLinkedBackend("staticSiteLinkedBackend", {
    backendResourceId: "/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/backendRg/providers/Microsoft.Web/sites/testBackend",
    linkedBackendName: "testBackend",
    name: "testStaticSite0",
    region: "West US 2",
    resourceGroupName: "rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

static_site_linked_backend = azure_native.web.StaticSiteLinkedBackend("staticSiteLinkedBackend",
    backend_resource_id="/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/backendRg/providers/Microsoft.Web/sites/testBackend",
    linked_backend_name="testBackend",
    name="testStaticSite0",
    region="West US 2",
    resource_group_name="rg")

```

```yaml
resources:
  staticSiteLinkedBackend:
    type: azure-native:web:StaticSiteLinkedBackend
    properties:
      backendResourceId: /subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/backendRg/providers/Microsoft.Web/sites/testBackend
      linkedBackendName: testBackend
      name: testStaticSite0
      region: West US 2
      resourceGroupName: rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:StaticSiteLinkedBackend testBackend /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/staticSites/testStaticSite0/builds/default/linkedBackends/testBackend 
```
