A custom certificate.
API Version: 2023-02-01.
Previous API Version: 2022-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SignalRCustomCertificates_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var signalRCustomCertificate = new AzureNative.SignalRService.SignalRCustomCertificate("signalRCustomCertificate", new()
    {
        CertificateName = "myCert",
        KeyVaultBaseUri = "https://myvault.keyvault.azure.net/",
        KeyVaultSecretName = "mycert",
        KeyVaultSecretVersion = "bb6a44b2743f47f68dad0d6cc9756432",
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
		_, err := signalrservice.NewSignalRCustomCertificate(ctx, "signalRCustomCertificate", &signalrservice.SignalRCustomCertificateArgs{
			CertificateName:       pulumi.String("myCert"),
			KeyVaultBaseUri:       pulumi.String("https://myvault.keyvault.azure.net/"),
			KeyVaultSecretName:    pulumi.String("mycert"),
			KeyVaultSecretVersion: pulumi.String("bb6a44b2743f47f68dad0d6cc9756432"),
			ResourceGroupName:     pulumi.String("myResourceGroup"),
			ResourceName:          pulumi.String("mySignalRService"),
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
import com.pulumi.azurenative.signalrservice.SignalRCustomCertificate;
import com.pulumi.azurenative.signalrservice.SignalRCustomCertificateArgs;
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
        var signalRCustomCertificate = new SignalRCustomCertificate("signalRCustomCertificate", SignalRCustomCertificateArgs.builder()        
            .certificateName("myCert")
            .keyVaultBaseUri("https://myvault.keyvault.azure.net/")
            .keyVaultSecretName("mycert")
            .keyVaultSecretVersion("bb6a44b2743f47f68dad0d6cc9756432")
            .resourceGroupName("myResourceGroup")
            .resourceName("mySignalRService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const signalRCustomCertificate = new azure_native.signalrservice.SignalRCustomCertificate("signalRCustomCertificate", {
    certificateName: "myCert",
    keyVaultBaseUri: "https://myvault.keyvault.azure.net/",
    keyVaultSecretName: "mycert",
    keyVaultSecretVersion: "bb6a44b2743f47f68dad0d6cc9756432",
    resourceGroupName: "myResourceGroup",
    resourceName: "mySignalRService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

signal_r_custom_certificate = azure_native.signalrservice.SignalRCustomCertificate("signalRCustomCertificate",
    certificate_name="myCert",
    key_vault_base_uri="https://myvault.keyvault.azure.net/",
    key_vault_secret_name="mycert",
    key_vault_secret_version="bb6a44b2743f47f68dad0d6cc9756432",
    resource_group_name="myResourceGroup",
    resource_name_="mySignalRService")

```

```yaml
resources:
  signalRCustomCertificate:
    type: azure-native:signalrservice:SignalRCustomCertificate
    properties:
      certificateName: myCert
      keyVaultBaseUri: https://myvault.keyvault.azure.net/
      keyVaultSecretName: mycert
      keyVaultSecretVersion: bb6a44b2743f47f68dad0d6cc9756432
      resourceGroupName: myResourceGroup
      resourceName: mySignalRService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:signalrservice:SignalRCustomCertificate myCert /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/SignalR/mySignalRService/customCertificates/myCert 
```
