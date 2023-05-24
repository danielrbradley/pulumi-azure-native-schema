Key Vault container ARM resource for a certificate that is purchased through Azure.
API Version: 2022-09-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Certificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var appServiceCertificateOrderCertificate = new AzureNative.CertificateRegistration.AppServiceCertificateOrderCertificate("appServiceCertificateOrderCertificate", new()
    {
        CertificateOrderName = "SampleCertificateOrderName",
        KeyVaultId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName",
        KeyVaultSecretName = "SampleSecretName1",
        Location = "Global",
        Name = "SampleCertName1",
        ResourceGroupName = "testrg123",
    });

});


```

```go
package main

import (
	certificateregistration "github.com/pulumi/pulumi-azure-native-sdk/certificateregistration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := certificateregistration.NewAppServiceCertificateOrderCertificate(ctx, "appServiceCertificateOrderCertificate", &certificateregistration.AppServiceCertificateOrderCertificateArgs{
			CertificateOrderName: pulumi.String("SampleCertificateOrderName"),
			KeyVaultId:           pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName"),
			KeyVaultSecretName:   pulumi.String("SampleSecretName1"),
			Location:             pulumi.String("Global"),
			Name:                 pulumi.String("SampleCertName1"),
			ResourceGroupName:    pulumi.String("testrg123"),
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
import com.pulumi.azurenative.certificateregistration.AppServiceCertificateOrderCertificate;
import com.pulumi.azurenative.certificateregistration.AppServiceCertificateOrderCertificateArgs;
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
        var appServiceCertificateOrderCertificate = new AppServiceCertificateOrderCertificate("appServiceCertificateOrderCertificate", AppServiceCertificateOrderCertificateArgs.builder()        
            .certificateOrderName("SampleCertificateOrderName")
            .keyVaultId("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName")
            .keyVaultSecretName("SampleSecretName1")
            .location("Global")
            .name("SampleCertName1")
            .resourceGroupName("testrg123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const appServiceCertificateOrderCertificate = new azure_native.certificateregistration.AppServiceCertificateOrderCertificate("appServiceCertificateOrderCertificate", {
    certificateOrderName: "SampleCertificateOrderName",
    keyVaultId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName",
    keyVaultSecretName: "SampleSecretName1",
    location: "Global",
    name: "SampleCertName1",
    resourceGroupName: "testrg123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

app_service_certificate_order_certificate = azure_native.certificateregistration.AppServiceCertificateOrderCertificate("appServiceCertificateOrderCertificate",
    certificate_order_name="SampleCertificateOrderName",
    key_vault_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName",
    key_vault_secret_name="SampleSecretName1",
    location="Global",
    name="SampleCertName1",
    resource_group_name="testrg123")

```

```yaml
resources:
  appServiceCertificateOrderCertificate:
    type: azure-native:certificateregistration:AppServiceCertificateOrderCertificate
    properties:
      certificateOrderName: SampleCertificateOrderName
      keyVaultId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName
      keyVaultSecretName: SampleSecretName1
      location: Global
      name: SampleCertName1
      resourceGroupName: testrg123

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:certificateregistration:AppServiceCertificateOrderCertificate SampleCertName1 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.CertificateRegistration/certificateOrders/SampleCertificateOrderName/certificates/SampleCertName1 
```
