The integration account certificate.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a certificate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationAccountCertificate = new AzureNative.Logic.IntegrationAccountCertificate("integrationAccountCertificate", new()
    {
        CertificateName = "testCertificate",
        IntegrationAccountName = "testIntegrationAccount",
        Key = new AzureNative.Logic.Inputs.KeyVaultKeyReferenceArgs
        {
            KeyName = "<keyName>",
            KeyVault = new AzureNative.Logic.Inputs.KeyVaultKeyReferenceKeyVaultArgs
            {
                Id = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testResourceGroup/providers/microsoft.keyvault/vaults/<keyVaultName>",
            },
            KeyVersion = "87d9764197604449b9b8eb7bd8710868",
        },
        Location = "brazilsouth",
        PublicCertificate = "<publicCertificateValue>",
        ResourceGroupName = "testResourceGroup",
    });

});


```

```go
package main

import (
	logic "github.com/pulumi/pulumi-azure-native-sdk/logic"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := logic.NewIntegrationAccountCertificate(ctx, "integrationAccountCertificate", &logic.IntegrationAccountCertificateArgs{
			CertificateName:        pulumi.String("testCertificate"),
			IntegrationAccountName: pulumi.String("testIntegrationAccount"),
			Key: logic.KeyVaultKeyReferenceResponse{
				KeyName: pulumi.String("<keyName>"),
				KeyVault: &logic.KeyVaultKeyReferenceKeyVaultArgs{
					Id: pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testResourceGroup/providers/microsoft.keyvault/vaults/<keyVaultName>"),
				},
				KeyVersion: pulumi.String("87d9764197604449b9b8eb7bd8710868"),
			},
			Location:          pulumi.String("brazilsouth"),
			PublicCertificate: pulumi.String("<publicCertificateValue>"),
			ResourceGroupName: pulumi.String("testResourceGroup"),
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
import com.pulumi.azurenative.logic.IntegrationAccountCertificate;
import com.pulumi.azurenative.logic.IntegrationAccountCertificateArgs;
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
        var integrationAccountCertificate = new IntegrationAccountCertificate("integrationAccountCertificate", IntegrationAccountCertificateArgs.builder()        
            .certificateName("testCertificate")
            .integrationAccountName("testIntegrationAccount")
            .key(Map.ofEntries(
                Map.entry("keyName", "<keyName>"),
                Map.entry("keyVault", Map.of("id", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testResourceGroup/providers/microsoft.keyvault/vaults/<keyVaultName>")),
                Map.entry("keyVersion", "87d9764197604449b9b8eb7bd8710868")
            ))
            .location("brazilsouth")
            .publicCertificate("<publicCertificateValue>")
            .resourceGroupName("testResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationAccountCertificate = new azure_native.logic.IntegrationAccountCertificate("integrationAccountCertificate", {
    certificateName: "testCertificate",
    integrationAccountName: "testIntegrationAccount",
    key: {
        keyName: "<keyName>",
        keyVault: {
            id: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testResourceGroup/providers/microsoft.keyvault/vaults/<keyVaultName>",
        },
        keyVersion: "87d9764197604449b9b8eb7bd8710868",
    },
    location: "brazilsouth",
    publicCertificate: "<publicCertificateValue>",
    resourceGroupName: "testResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_account_certificate = azure_native.logic.IntegrationAccountCertificate("integrationAccountCertificate",
    certificate_name="testCertificate",
    integration_account_name="testIntegrationAccount",
    key=azure_native.logic.KeyVaultKeyReferenceResponseArgs(
        key_name="<keyName>",
        key_vault=azure_native.logic.KeyVaultKeyReferenceKeyVaultArgs(
            id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testResourceGroup/providers/microsoft.keyvault/vaults/<keyVaultName>",
        ),
        key_version="87d9764197604449b9b8eb7bd8710868",
    ),
    location="brazilsouth",
    public_certificate="<publicCertificateValue>",
    resource_group_name="testResourceGroup")

```

```yaml
resources:
  integrationAccountCertificate:
    type: azure-native:logic:IntegrationAccountCertificate
    properties:
      certificateName: testCertificate
      integrationAccountName: testIntegrationAccount
      key:
        keyName: <keyName>
        keyVault:
          id: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourcegroups/testResourceGroup/providers/microsoft.keyvault/vaults/<keyVaultName>
        keyVersion: 87d9764197604449b9b8eb7bd8710868
      location: brazilsouth
      publicCertificate: <publicCertificateValue>
      resourceGroupName: testResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:IntegrationAccountCertificate testCertificate /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testResourceGroup/providers/Microsoft.Logic/integrationAccounts/testIntegrationAccount/certificates/testCertificate 
```
