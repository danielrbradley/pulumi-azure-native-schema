Full view of the custom domain suffix configuration for ASEv3.
API Version: 2022-09-01.
Previous API Version: 2022-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update ASE custom DNS suffix configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var appServiceEnvironmentAseCustomDnsSuffixConfiguration = new AzureNative.Web.AppServiceEnvironmentAseCustomDnsSuffixConfiguration("appServiceEnvironmentAseCustomDnsSuffixConfiguration", new()
    {
        CertificateUrl = "https://test-kv.vault.azure.net/secrets/contosocert",
        DnsSuffix = "contoso.com",
        KeyVaultReferenceIdentity = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/test-rg/providers/microsoft.managedidentity/userassignedidentities/test-user-mi",
        Name = "test-ase",
        ResourceGroupName = "test-rg",
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewAppServiceEnvironmentAseCustomDnsSuffixConfiguration(ctx, "appServiceEnvironmentAseCustomDnsSuffixConfiguration", &web.AppServiceEnvironmentAseCustomDnsSuffixConfigurationArgs{
			CertificateUrl:            pulumi.String("https://test-kv.vault.azure.net/secrets/contosocert"),
			DnsSuffix:                 pulumi.String("contoso.com"),
			KeyVaultReferenceIdentity: pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/test-rg/providers/microsoft.managedidentity/userassignedidentities/test-user-mi"),
			Name:                      pulumi.String("test-ase"),
			ResourceGroupName:         pulumi.String("test-rg"),
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
import com.pulumi.azurenative.web.AppServiceEnvironmentAseCustomDnsSuffixConfiguration;
import com.pulumi.azurenative.web.AppServiceEnvironmentAseCustomDnsSuffixConfigurationArgs;
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
        var appServiceEnvironmentAseCustomDnsSuffixConfiguration = new AppServiceEnvironmentAseCustomDnsSuffixConfiguration("appServiceEnvironmentAseCustomDnsSuffixConfiguration", AppServiceEnvironmentAseCustomDnsSuffixConfigurationArgs.builder()        
            .certificateUrl("https://test-kv.vault.azure.net/secrets/contosocert")
            .dnsSuffix("contoso.com")
            .keyVaultReferenceIdentity("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/test-rg/providers/microsoft.managedidentity/userassignedidentities/test-user-mi")
            .name("test-ase")
            .resourceGroupName("test-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const appServiceEnvironmentAseCustomDnsSuffixConfiguration = new azure_native.web.AppServiceEnvironmentAseCustomDnsSuffixConfiguration("appServiceEnvironmentAseCustomDnsSuffixConfiguration", {
    certificateUrl: "https://test-kv.vault.azure.net/secrets/contosocert",
    dnsSuffix: "contoso.com",
    keyVaultReferenceIdentity: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/test-rg/providers/microsoft.managedidentity/userassignedidentities/test-user-mi",
    name: "test-ase",
    resourceGroupName: "test-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

app_service_environment_ase_custom_dns_suffix_configuration = azure_native.web.AppServiceEnvironmentAseCustomDnsSuffixConfiguration("appServiceEnvironmentAseCustomDnsSuffixConfiguration",
    certificate_url="https://test-kv.vault.azure.net/secrets/contosocert",
    dns_suffix="contoso.com",
    key_vault_reference_identity="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/test-rg/providers/microsoft.managedidentity/userassignedidentities/test-user-mi",
    name="test-ase",
    resource_group_name="test-rg")

```

```yaml
resources:
  appServiceEnvironmentAseCustomDnsSuffixConfiguration:
    type: azure-native:web:AppServiceEnvironmentAseCustomDnsSuffixConfiguration
    properties:
      certificateUrl: https://test-kv.vault.azure.net/secrets/contosocert
      dnsSuffix: contoso.com
      keyVaultReferenceIdentity: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/test-rg/providers/microsoft.managedidentity/userassignedidentities/test-user-mi
      name: test-ase
      resourceGroupName: test-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:AppServiceEnvironmentAseCustomDnsSuffixConfiguration customDnsSuffix /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-rg/providers/Microsoft.Web/hostingEnvironments/test-ase/configurations/customdnssuffix 
```
