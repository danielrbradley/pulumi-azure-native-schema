Describes a federated identity credential.
API Version: 2023-01-31.
Previous API Version: 2022-01-31-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### FederatedIdentityCredentialCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var federatedIdentityCredential = new AzureNative.ManagedIdentity.FederatedIdentityCredential("federatedIdentityCredential", new()
    {
        Audiences = new[]
        {
            "api://AzureADTokenExchange",
        },
        FederatedIdentityCredentialResourceName = "ficResourceName",
        Issuer = "https://oidc.prod-aks.azure.com/TenantGUID/IssuerGUID",
        ResourceGroupName = "rgName",
        ResourceName = "resourceName",
        Subject = "system:serviceaccount:ns:svcaccount",
    });

});


```

```go
package main

import (
	managedidentity "github.com/pulumi/pulumi-azure-native-sdk/managedidentity"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managedidentity.NewFederatedIdentityCredential(ctx, "federatedIdentityCredential", &managedidentity.FederatedIdentityCredentialArgs{
			Audiences: pulumi.StringArray{
				pulumi.String("api://AzureADTokenExchange"),
			},
			FederatedIdentityCredentialResourceName: pulumi.String("ficResourceName"),
			Issuer:                                  pulumi.String("https://oidc.prod-aks.azure.com/TenantGUID/IssuerGUID"),
			ResourceGroupName:                       pulumi.String("rgName"),
			ResourceName:                            pulumi.String("resourceName"),
			Subject:                                 pulumi.String("system:serviceaccount:ns:svcaccount"),
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
import com.pulumi.azurenative.managedidentity.FederatedIdentityCredential;
import com.pulumi.azurenative.managedidentity.FederatedIdentityCredentialArgs;
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
        var federatedIdentityCredential = new FederatedIdentityCredential("federatedIdentityCredential", FederatedIdentityCredentialArgs.builder()        
            .audiences("api://AzureADTokenExchange")
            .federatedIdentityCredentialResourceName("ficResourceName")
            .issuer("https://oidc.prod-aks.azure.com/TenantGUID/IssuerGUID")
            .resourceGroupName("rgName")
            .resourceName("resourceName")
            .subject("system:serviceaccount:ns:svcaccount")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const federatedIdentityCredential = new azure_native.managedidentity.FederatedIdentityCredential("federatedIdentityCredential", {
    audiences: ["api://AzureADTokenExchange"],
    federatedIdentityCredentialResourceName: "ficResourceName",
    issuer: "https://oidc.prod-aks.azure.com/TenantGUID/IssuerGUID",
    resourceGroupName: "rgName",
    resourceName: "resourceName",
    subject: "system:serviceaccount:ns:svcaccount",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

federated_identity_credential = azure_native.managedidentity.FederatedIdentityCredential("federatedIdentityCredential",
    audiences=["api://AzureADTokenExchange"],
    federated_identity_credential_resource_name="ficResourceName",
    issuer="https://oidc.prod-aks.azure.com/TenantGUID/IssuerGUID",
    resource_group_name="rgName",
    resource_name_="resourceName",
    subject="system:serviceaccount:ns:svcaccount")

```

```yaml
resources:
  federatedIdentityCredential:
    type: azure-native:managedidentity:FederatedIdentityCredential
    properties:
      audiences:
        - api://AzureADTokenExchange
      federatedIdentityCredentialResourceName: ficResourceName
      issuer: https://oidc.prod-aks.azure.com/TenantGUID/IssuerGUID
      resourceGroupName: rgName
      resourceName: resourceName
      subject: system:serviceaccount:ns:svcaccount

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managedidentity:FederatedIdentityCredential ficResourceName /subscriptions/c267c0e7-0a73-4789-9e17-d26aeb0904e5/resourcegroups/rgName/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identityName/federatedIdentityCredentials/ficResourceName 
```
