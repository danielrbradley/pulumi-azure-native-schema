Static Site Custom Domain Overview ARM resource.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a custom domain for a static site
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var staticSiteCustomDomain = new AzureNative.Web.StaticSiteCustomDomain("staticSiteCustomDomain", new()
    {
        DomainName = "custom.domain.net",
        Name = "testStaticSite0",
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
		_, err := web.NewStaticSiteCustomDomain(ctx, "staticSiteCustomDomain", &web.StaticSiteCustomDomainArgs{
			DomainName:        pulumi.String("custom.domain.net"),
			Name:              pulumi.String("testStaticSite0"),
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
import com.pulumi.azurenative.web.StaticSiteCustomDomain;
import com.pulumi.azurenative.web.StaticSiteCustomDomainArgs;
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
        var staticSiteCustomDomain = new StaticSiteCustomDomain("staticSiteCustomDomain", StaticSiteCustomDomainArgs.builder()        
            .domainName("custom.domain.net")
            .name("testStaticSite0")
            .resourceGroupName("rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const staticSiteCustomDomain = new azure_native.web.StaticSiteCustomDomain("staticSiteCustomDomain", {
    domainName: "custom.domain.net",
    name: "testStaticSite0",
    resourceGroupName: "rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

static_site_custom_domain = azure_native.web.StaticSiteCustomDomain("staticSiteCustomDomain",
    domain_name="custom.domain.net",
    name="testStaticSite0",
    resource_group_name="rg")

```

```yaml
resources:
  staticSiteCustomDomain:
    type: azure-native:web:StaticSiteCustomDomain
    properties:
      domainName: custom.domain.net
      name: testStaticSite0
      resourceGroupName: rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:StaticSiteCustomDomain myresource1 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/staticSitesBuilds/testStaticSite0/customDomains/custom.domain.net 
```
