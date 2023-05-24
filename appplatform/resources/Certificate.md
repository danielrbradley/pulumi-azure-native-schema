Certificate resource payload.
API Version: 2022-12-01.
Previous API Version: 2020-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Certificates_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var certificate = new AzureNative.AppPlatform.Certificate("certificate", new()
    {
        CertificateName = "mycertificate",
        Properties = new AzureNative.AppPlatform.Inputs.KeyVaultCertificatePropertiesArgs
        {
            CertVersion = "08a219d06d874795a96db47e06fbb01e",
            KeyVaultCertName = "mycert",
            Type = "KeyVaultCertificate",
            VaultUri = "https://myvault.vault.azure.net",
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
		_, err := appplatform.NewCertificate(ctx, "certificate", &appplatform.CertificateArgs{
			CertificateName: pulumi.String("mycertificate"),
			Properties: appplatform.KeyVaultCertificateProperties{
				CertVersion:      "08a219d06d874795a96db47e06fbb01e",
				KeyVaultCertName: "mycert",
				Type:             "KeyVaultCertificate",
				VaultUri:         "https://myvault.vault.azure.net",
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
import com.pulumi.azurenative.appplatform.Certificate;
import com.pulumi.azurenative.appplatform.CertificateArgs;
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
        var certificate = new Certificate("certificate", CertificateArgs.builder()        
            .certificateName("mycertificate")
            .properties(Map.ofEntries(
                Map.entry("certVersion", "08a219d06d874795a96db47e06fbb01e"),
                Map.entry("keyVaultCertName", "mycert"),
                Map.entry("type", "KeyVaultCertificate"),
                Map.entry("vaultUri", "https://myvault.vault.azure.net")
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

const certificate = new azure_native.appplatform.Certificate("certificate", {
    certificateName: "mycertificate",
    properties: {
        certVersion: "08a219d06d874795a96db47e06fbb01e",
        keyVaultCertName: "mycert",
        type: "KeyVaultCertificate",
        vaultUri: "https://myvault.vault.azure.net",
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

certificate = azure_native.appplatform.Certificate("certificate",
    certificate_name="mycertificate",
    properties=azure_native.appplatform.KeyVaultCertificatePropertiesArgs(
        cert_version="08a219d06d874795a96db47e06fbb01e",
        key_vault_cert_name="mycert",
        type="KeyVaultCertificate",
        vault_uri="https://myvault.vault.azure.net",
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  certificate:
    type: azure-native:appplatform:Certificate
    properties:
      certificateName: mycertificate
      properties:
        certVersion: 08a219d06d874795a96db47e06fbb01e
        keyVaultCertName: mycert
        type: KeyVaultCertificate
        vaultUri: https://myvault.vault.azure.net
      resourceGroupName: myResourceGroup
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:Certificate mycertificate /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/certificates/mycertificate 
```
