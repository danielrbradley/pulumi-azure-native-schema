A custom domain
API Version: 2023-02-01.
Previous API Version: 2022-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SignalRCustomDomains_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var signalRCustomDomain = new AzureNative.SignalRService.SignalRCustomDomain("signalRCustomDomain", new()
    {
        CustomCertificate = new AzureNative.SignalRService.Inputs.ResourceReferenceArgs
        {
            Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/SignalR/mySignalRService/customCertificates/myCert",
        },
        DomainName = "example.com",
        Name = "myDomain",
        ResourceGroupName = "myResourceGroup",
        ResourceName = "mySignalRService",
    });

});


```

```go
package main

import (
	signalrservice "github.com/pulumi/pulumi-azure-native-sdk/signalrservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := signalrservice.NewSignalRCustomDomain(ctx, "signalRCustomDomain", &signalrservice.SignalRCustomDomainArgs{
			CustomCertificate: &signalrservice.ResourceReferenceArgs{
				Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/SignalR/mySignalRService/customCertificates/myCert"),
			},
			DomainName:        pulumi.String("example.com"),
			Name:              pulumi.String("myDomain"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ResourceName:      pulumi.String("mySignalRService"),
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
import com.pulumi.azurenative.signalrservice.SignalRCustomDomain;
import com.pulumi.azurenative.signalrservice.SignalRCustomDomainArgs;
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
        var signalRCustomDomain = new SignalRCustomDomain("signalRCustomDomain", SignalRCustomDomainArgs.builder()        
            .customCertificate(Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/SignalR/mySignalRService/customCertificates/myCert"))
            .domainName("example.com")
            .name("myDomain")
            .resourceGroupName("myResourceGroup")
            .resourceName("mySignalRService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const signalRCustomDomain = new azure_native.signalrservice.SignalRCustomDomain("signalRCustomDomain", {
    customCertificate: {
        id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/SignalR/mySignalRService/customCertificates/myCert",
    },
    domainName: "example.com",
    name: "myDomain",
    resourceGroupName: "myResourceGroup",
    resourceName: "mySignalRService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

signal_r_custom_domain = azure_native.signalrservice.SignalRCustomDomain("signalRCustomDomain",
    custom_certificate=azure_native.signalrservice.ResourceReferenceArgs(
        id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/SignalR/mySignalRService/customCertificates/myCert",
    ),
    domain_name="example.com",
    name="myDomain",
    resource_group_name="myResourceGroup",
    resource_name_="mySignalRService")

```

```yaml
resources:
  signalRCustomDomain:
    type: azure-native:signalrservice:SignalRCustomDomain
    properties:
      customCertificate:
        id: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/SignalR/mySignalRService/customCertificates/myCert
      domainName: example.com
      name: myDomain
      resourceGroupName: myResourceGroup
      resourceName: mySignalRService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:signalrservice:SignalRCustomDomain myDomain /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/SignalR/mySignalRService/customDomains/myDomain 
```
