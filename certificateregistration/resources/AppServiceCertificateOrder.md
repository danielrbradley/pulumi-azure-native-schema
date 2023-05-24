SSL certificate purchase order.
API Version: 2022-09-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Certificate order
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var appServiceCertificateOrder = new AzureNative.CertificateRegistration.AppServiceCertificateOrder("appServiceCertificateOrder", new()
    {
        AutoRenew = true,
        CertificateOrderName = "SampleCertificateOrderName",
        Certificates = 
        {
            { "SampleCertName1", new AzureNative.CertificateRegistration.Inputs.AppServiceCertificateArgs
            {
                KeyVaultId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName",
                KeyVaultSecretName = "SampleSecretName1",
            } },
            { "SampleCertName2", new AzureNative.CertificateRegistration.Inputs.AppServiceCertificateArgs
            {
                KeyVaultId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName",
                KeyVaultSecretName = "SampleSecretName2",
            } },
        },
        DistinguishedName = "CN=SampleCustomDomain.com",
        KeySize = 2048,
        Location = "Global",
        ProductType = AzureNative.CertificateRegistration.CertificateProductType.StandardDomainValidatedSsl,
        ResourceGroupName = "testrg123",
        ValidityInYears = 2,
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
		_, err := certificateregistration.NewAppServiceCertificateOrder(ctx, "appServiceCertificateOrder", &certificateregistration.AppServiceCertificateOrderArgs{
			AutoRenew:            pulumi.Bool(true),
			CertificateOrderName: pulumi.String("SampleCertificateOrderName"),
			Certificates: certificateregistration.AppServiceCertificateMap{
				"SampleCertName1": &certificateregistration.AppServiceCertificateArgs{
					KeyVaultId:         pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName"),
					KeyVaultSecretName: pulumi.String("SampleSecretName1"),
				},
				"SampleCertName2": &certificateregistration.AppServiceCertificateArgs{
					KeyVaultId:         pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName"),
					KeyVaultSecretName: pulumi.String("SampleSecretName2"),
				},
			},
			DistinguishedName: pulumi.String("CN=SampleCustomDomain.com"),
			KeySize:           pulumi.Int(2048),
			Location:          pulumi.String("Global"),
			ProductType:       certificateregistration.CertificateProductTypeStandardDomainValidatedSsl,
			ResourceGroupName: pulumi.String("testrg123"),
			ValidityInYears:   pulumi.Int(2),
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
import com.pulumi.azurenative.certificateregistration.AppServiceCertificateOrder;
import com.pulumi.azurenative.certificateregistration.AppServiceCertificateOrderArgs;
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
        var appServiceCertificateOrder = new AppServiceCertificateOrder("appServiceCertificateOrder", AppServiceCertificateOrderArgs.builder()        
            .autoRenew(true)
            .certificateOrderName("SampleCertificateOrderName")
            .certificates(Map.ofEntries(
                Map.entry("SampleCertName1", Map.ofEntries(
                    Map.entry("keyVaultId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName"),
                    Map.entry("keyVaultSecretName", "SampleSecretName1")
                )),
                Map.entry("SampleCertName2", Map.ofEntries(
                    Map.entry("keyVaultId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName"),
                    Map.entry("keyVaultSecretName", "SampleSecretName2")
                ))
            ))
            .distinguishedName("CN=SampleCustomDomain.com")
            .keySize(2048)
            .location("Global")
            .productType("StandardDomainValidatedSsl")
            .resourceGroupName("testrg123")
            .validityInYears(2)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const appServiceCertificateOrder = new azure_native.certificateregistration.AppServiceCertificateOrder("appServiceCertificateOrder", {
    autoRenew: true,
    certificateOrderName: "SampleCertificateOrderName",
    certificates: {
        SampleCertName1: {
            keyVaultId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName",
            keyVaultSecretName: "SampleSecretName1",
        },
        SampleCertName2: {
            keyVaultId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName",
            keyVaultSecretName: "SampleSecretName2",
        },
    },
    distinguishedName: "CN=SampleCustomDomain.com",
    keySize: 2048,
    location: "Global",
    productType: azure_native.certificateregistration.CertificateProductType.StandardDomainValidatedSsl,
    resourceGroupName: "testrg123",
    validityInYears: 2,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

app_service_certificate_order = azure_native.certificateregistration.AppServiceCertificateOrder("appServiceCertificateOrder",
    auto_renew=True,
    certificate_order_name="SampleCertificateOrderName",
    certificates={
        "SampleCertName1": azure_native.certificateregistration.AppServiceCertificateArgs(
            key_vault_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName",
            key_vault_secret_name="SampleSecretName1",
        ),
        "SampleCertName2": azure_native.certificateregistration.AppServiceCertificateArgs(
            key_vault_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName",
            key_vault_secret_name="SampleSecretName2",
        ),
    },
    distinguished_name="CN=SampleCustomDomain.com",
    key_size=2048,
    location="Global",
    product_type=azure_native.certificateregistration.CertificateProductType.STANDARD_DOMAIN_VALIDATED_SSL,
    resource_group_name="testrg123",
    validity_in_years=2)

```

```yaml
resources:
  appServiceCertificateOrder:
    type: azure-native:certificateregistration:AppServiceCertificateOrder
    properties:
      autoRenew: true
      certificateOrderName: SampleCertificateOrderName
      certificates:
        SampleCertName1:
          keyVaultId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName
          keyVaultSecretName: SampleSecretName1
        SampleCertName2:
          keyVaultId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testrg123/providers/microsoft.keyvault/vaults/SamplevaultName
          keyVaultSecretName: SampleSecretName2
      distinguishedName: CN=SampleCustomDomain.com
      keySize: 2048
      location: Global
      productType: StandardDomainValidatedSsl
      resourceGroupName: testrg123
      validityInYears: 2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:certificateregistration:AppServiceCertificateOrder SampleCertificateOrderName /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.CertificateRegistration/certificateOrders/SampleCertificateOrderName 
```
