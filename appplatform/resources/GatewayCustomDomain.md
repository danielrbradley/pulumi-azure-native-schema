Custom domain of the Spring Cloud Gateway
API Version: 2022-12-01.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### GatewayCustomDomains_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gatewayCustomDomain = new AzureNative.AppPlatform.GatewayCustomDomain("gatewayCustomDomain", new()
    {
        DomainName = "myDomainName",
        GatewayName = "default",
        Properties = new AzureNative.AppPlatform.Inputs.GatewayCustomDomainPropertiesArgs
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
		_, err := appplatform.NewGatewayCustomDomain(ctx, "gatewayCustomDomain", &appplatform.GatewayCustomDomainArgs{
			DomainName:  pulumi.String("myDomainName"),
			GatewayName: pulumi.String("default"),
			Properties: &appplatform.GatewayCustomDomainPropertiesArgs{
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
import com.pulumi.azurenative.appplatform.GatewayCustomDomain;
import com.pulumi.azurenative.appplatform.GatewayCustomDomainArgs;
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
        var gatewayCustomDomain = new GatewayCustomDomain("gatewayCustomDomain", GatewayCustomDomainArgs.builder()        
            .domainName("myDomainName")
            .gatewayName("default")
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

const gatewayCustomDomain = new azure_native.appplatform.GatewayCustomDomain("gatewayCustomDomain", {
    domainName: "myDomainName",
    gatewayName: "default",
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

gateway_custom_domain = azure_native.appplatform.GatewayCustomDomain("gatewayCustomDomain",
    domain_name="myDomainName",
    gateway_name="default",
    properties=azure_native.appplatform.GatewayCustomDomainPropertiesArgs(
        thumbprint="*",
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  gatewayCustomDomain:
    type: azure-native:appplatform:GatewayCustomDomain
    properties:
      domainName: myDomainName
      gatewayName: default
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
$ pulumi import azure-native:appplatform:GatewayCustomDomain myDomainName /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/gateways/default/domains/myDomainName 
```
