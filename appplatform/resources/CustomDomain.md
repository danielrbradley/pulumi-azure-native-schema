Custom domain resource payload.
API Version: 2022-12-01.
Previous API Version: 2020-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CustomDomains_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var customDomain = new AzureNative.AppPlatform.CustomDomain("customDomain", new()
    {
        AppName = "myapp",
        DomainName = "mydomain.com",
        Properties = new AzureNative.AppPlatform.Inputs.CustomDomainPropertiesArgs
        {
            CertName = "mycert",
            Thumbprint = "934367bf1c97033f877db0f15cb1b586957d3133",
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
		_, err := appplatform.NewCustomDomain(ctx, "customDomain", &appplatform.CustomDomainArgs{
			AppName:    pulumi.String("myapp"),
			DomainName: pulumi.String("mydomain.com"),
			Properties: &appplatform.CustomDomainPropertiesArgs{
				CertName:   pulumi.String("mycert"),
				Thumbprint: pulumi.String("934367bf1c97033f877db0f15cb1b586957d3133"),
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
import com.pulumi.azurenative.appplatform.CustomDomain;
import com.pulumi.azurenative.appplatform.CustomDomainArgs;
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
        var customDomain = new CustomDomain("customDomain", CustomDomainArgs.builder()        
            .appName("myapp")
            .domainName("mydomain.com")
            .properties(Map.ofEntries(
                Map.entry("certName", "mycert"),
                Map.entry("thumbprint", "934367bf1c97033f877db0f15cb1b586957d3133")
            ))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const customDomain = new azure_native.appplatform.CustomDomain("customDomain", {
    appName: "myapp",
    domainName: "mydomain.com",
    properties: {
        certName: "mycert",
        thumbprint: "934367bf1c97033f877db0f15cb1b586957d3133",
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

custom_domain = azure_native.appplatform.CustomDomain("customDomain",
    app_name="myapp",
    domain_name="mydomain.com",
    properties=azure_native.appplatform.CustomDomainPropertiesArgs(
        cert_name="mycert",
        thumbprint="934367bf1c97033f877db0f15cb1b586957d3133",
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  customDomain:
    type: azure-native:appplatform:CustomDomain
    properties:
      appName: myapp
      domainName: mydomain.com
      properties:
        certName: mycert
        thumbprint: 934367bf1c97033f877db0f15cb1b586957d3133
      resourceGroupName: myResourceGroup
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:CustomDomain mydomain.com /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/apps/myapp/domains/mydomain.com 
```
