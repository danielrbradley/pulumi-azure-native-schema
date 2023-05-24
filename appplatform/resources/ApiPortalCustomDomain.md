Custom domain of the API portal
API Version: 2022-12-01.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiPortalCustomDomains_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiPortalCustomDomain = new AzureNative.AppPlatform.ApiPortalCustomDomain("apiPortalCustomDomain", new()
    {
        ApiPortalName = "default",
        DomainName = "myDomainName",
        Properties = new AzureNative.AppPlatform.Inputs.ApiPortalCustomDomainPropertiesArgs
        {
            Thumbprint = "*",
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
    });

});


```

```go
package main

import (
	appplatform "github.com/pulumi/pulumi-azure-native-sdk/appplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appplatform.NewApiPortalCustomDomain(ctx, "apiPortalCustomDomain", &appplatform.ApiPortalCustomDomainArgs{
			ApiPortalName: pulumi.String("default"),
			DomainName:    pulumi.String("myDomainName"),
			Properties: &appplatform.ApiPortalCustomDomainPropertiesArgs{
				Thumbprint: pulumi.String("*"),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ServiceName:       pulumi.String("myservice"),
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
import com.pulumi.azurenative.appplatform.ApiPortalCustomDomain;
import com.pulumi.azurenative.appplatform.ApiPortalCustomDomainArgs;
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
        var apiPortalCustomDomain = new ApiPortalCustomDomain("apiPortalCustomDomain", ApiPortalCustomDomainArgs.builder()        
            .apiPortalName("default")
            .domainName("myDomainName")
            .properties(Map.of("thumbprint", "*"))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiPortalCustomDomain = new azure_native.appplatform.ApiPortalCustomDomain("apiPortalCustomDomain", {
    apiPortalName: "default",
    domainName: "myDomainName",
    properties: {
        thumbprint: "*",
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_portal_custom_domain = azure_native.appplatform.ApiPortalCustomDomain("apiPortalCustomDomain",
    api_portal_name="default",
    domain_name="myDomainName",
    properties=azure_native.appplatform.ApiPortalCustomDomainPropertiesArgs(
        thumbprint="*",
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  apiPortalCustomDomain:
    type: azure-native:appplatform:ApiPortalCustomDomain
    properties:
      apiPortalName: default
      domainName: myDomainName
      properties:
        thumbprint: '*'
      resourceGroupName: myResourceGroup
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:ApiPortalCustomDomain myDomainName /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/apiPortals/default/domains/myDomainName 
```
