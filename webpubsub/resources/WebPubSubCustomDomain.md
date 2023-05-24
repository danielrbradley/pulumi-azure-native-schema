A custom domain
API Version: 2023-02-01.

{{% examples %}}
## Example Usage
{{% example %}}
### WebPubSubCustomDomains_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webPubSubCustomDomain = new AzureNative.WebPubSub.WebPubSubCustomDomain("webPubSubCustomDomain", new()
    {
        CustomCertificate = new AzureNative.WebPubSub.Inputs.ResourceReferenceArgs
        {
            Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService/customCertificates/myCert",
        },
        DomainName = "example.com",
        Name = "myDomain",
        ResourceGroupName = "myResourceGroup",
        ResourceName = "myWebPubSubService",
    });

});


```

```go
package main

import (
	webpubsub "github.com/pulumi/pulumi-azure-native-sdk/webpubsub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := webpubsub.NewWebPubSubCustomDomain(ctx, "webPubSubCustomDomain", &webpubsub.WebPubSubCustomDomainArgs{
			CustomCertificate: &webpubsub.ResourceReferenceArgs{
				Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService/customCertificates/myCert"),
			},
			DomainName:        pulumi.String("example.com"),
			Name:              pulumi.String("myDomain"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ResourceName:      pulumi.String("myWebPubSubService"),
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
import com.pulumi.azurenative.webpubsub.WebPubSubCustomDomain;
import com.pulumi.azurenative.webpubsub.WebPubSubCustomDomainArgs;
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
        var webPubSubCustomDomain = new WebPubSubCustomDomain("webPubSubCustomDomain", WebPubSubCustomDomainArgs.builder()        
            .customCertificate(Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService/customCertificates/myCert"))
            .domainName("example.com")
            .name("myDomain")
            .resourceGroupName("myResourceGroup")
            .resourceName("myWebPubSubService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webPubSubCustomDomain = new azure_native.webpubsub.WebPubSubCustomDomain("webPubSubCustomDomain", {
    customCertificate: {
        id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService/customCertificates/myCert",
    },
    domainName: "example.com",
    name: "myDomain",
    resourceGroupName: "myResourceGroup",
    resourceName: "myWebPubSubService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_pub_sub_custom_domain = azure_native.webpubsub.WebPubSubCustomDomain("webPubSubCustomDomain",
    custom_certificate=azure_native.webpubsub.ResourceReferenceArgs(
        id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService/customCertificates/myCert",
    ),
    domain_name="example.com",
    name="myDomain",
    resource_group_name="myResourceGroup",
    resource_name_="myWebPubSubService")

```

```yaml
resources:
  webPubSubCustomDomain:
    type: azure-native:webpubsub:WebPubSubCustomDomain
    properties:
      customCertificate:
        id: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService/customCertificates/myCert
      domainName: example.com
      name: myDomain
      resourceGroupName: myResourceGroup
      resourceName: myWebPubSubService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:webpubsub:WebPubSubCustomDomain myDomain /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService/customDomains/myDomain 
```
