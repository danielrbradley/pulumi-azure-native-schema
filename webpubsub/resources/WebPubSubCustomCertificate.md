A custom certificate.
API Version: 2023-02-01.

{{% examples %}}
## Example Usage
{{% example %}}
### WebPubSubCustomCertificates_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webPubSubCustomCertificate = new AzureNative.WebPubSub.WebPubSubCustomCertificate("webPubSubCustomCertificate", new()
    {
        CertificateName = "myCert",
        KeyVaultBaseUri = "https://myvault.keyvault.azure.net/",
        KeyVaultSecretName = "mycert",
        KeyVaultSecretVersion = "bb6a44b2743f47f68dad0d6cc9756432",
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
		_, err := webpubsub.NewWebPubSubCustomCertificate(ctx, "webPubSubCustomCertificate", &webpubsub.WebPubSubCustomCertificateArgs{
			CertificateName:       pulumi.String("myCert"),
			KeyVaultBaseUri:       pulumi.String("https://myvault.keyvault.azure.net/"),
			KeyVaultSecretName:    pulumi.String("mycert"),
			KeyVaultSecretVersion: pulumi.String("bb6a44b2743f47f68dad0d6cc9756432"),
			ResourceGroupName:     pulumi.String("myResourceGroup"),
			ResourceName:          pulumi.String("myWebPubSubService"),
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
import com.pulumi.azurenative.webpubsub.WebPubSubCustomCertificate;
import com.pulumi.azurenative.webpubsub.WebPubSubCustomCertificateArgs;
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
        var webPubSubCustomCertificate = new WebPubSubCustomCertificate("webPubSubCustomCertificate", WebPubSubCustomCertificateArgs.builder()        
            .certificateName("myCert")
            .keyVaultBaseUri("https://myvault.keyvault.azure.net/")
            .keyVaultSecretName("mycert")
            .keyVaultSecretVersion("bb6a44b2743f47f68dad0d6cc9756432")
            .resourceGroupName("myResourceGroup")
            .resourceName("myWebPubSubService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webPubSubCustomCertificate = new azure_native.webpubsub.WebPubSubCustomCertificate("webPubSubCustomCertificate", {
    certificateName: "myCert",
    keyVaultBaseUri: "https://myvault.keyvault.azure.net/",
    keyVaultSecretName: "mycert",
    keyVaultSecretVersion: "bb6a44b2743f47f68dad0d6cc9756432",
    resourceGroupName: "myResourceGroup",
    resourceName: "myWebPubSubService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_pub_sub_custom_certificate = azure_native.webpubsub.WebPubSubCustomCertificate("webPubSubCustomCertificate",
    certificate_name="myCert",
    key_vault_base_uri="https://myvault.keyvault.azure.net/",
    key_vault_secret_name="mycert",
    key_vault_secret_version="bb6a44b2743f47f68dad0d6cc9756432",
    resource_group_name="myResourceGroup",
    resource_name_="myWebPubSubService")

```

```yaml
resources:
  webPubSubCustomCertificate:
    type: azure-native:webpubsub:WebPubSubCustomCertificate
    properties:
      certificateName: myCert
      keyVaultBaseUri: https://myvault.keyvault.azure.net/
      keyVaultSecretName: mycert
      keyVaultSecretVersion: bb6a44b2743f47f68dad0d6cc9756432
      resourceGroupName: myResourceGroup
      resourceName: myWebPubSubService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:webpubsub:WebPubSubCustomCertificate myCert /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService/customCertificates/myCert 
```
