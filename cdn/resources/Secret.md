Friendly Secret name mapping to the any Secret or secret related information.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Secrets_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var secret = new AzureNative.Cdn.Secret("secret", new()
    {
        Parameters = new AzureNative.Cdn.Inputs.CustomerCertificateParametersArgs
        {
            SecretSource = new AzureNative.Cdn.Inputs.ResourceReferenceArgs
            {
                Id = "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.KeyVault/vault/kvName/secrets/certificatename",
            },
            SecretVersion = "abcdef1234578900abcdef1234567890",
            Type = "CustomerCertificate",
            UseLatestVersion = false,
        },
        ProfileName = "profile1",
        ResourceGroupName = "RG",
        SecretName = "secret1",
    });

});


```

```go
package main

import (
	cdn "github.com/pulumi/pulumi-azure-native-sdk/cdn"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cdn.NewSecret(ctx, "secret", &cdn.SecretArgs{
			Parameters: cdn.CustomerCertificateParameters{
				SecretSource: cdn.ResourceReference{
					Id: "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.KeyVault/vault/kvName/secrets/certificatename",
				},
				SecretVersion:    "abcdef1234578900abcdef1234567890",
				Type:             "CustomerCertificate",
				UseLatestVersion: false,
			},
			ProfileName:       pulumi.String("profile1"),
			ResourceGroupName: pulumi.String("RG"),
			SecretName:        pulumi.String("secret1"),
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
import com.pulumi.azurenative.cdn.Secret;
import com.pulumi.azurenative.cdn.SecretArgs;
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
        var secret = new Secret("secret", SecretArgs.builder()        
            .parameters(Map.ofEntries(
                Map.entry("secretSource", Map.of("id", "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.KeyVault/vault/kvName/secrets/certificatename")),
                Map.entry("secretVersion", "abcdef1234578900abcdef1234567890"),
                Map.entry("type", "CustomerCertificate"),
                Map.entry("useLatestVersion", false)
            ))
            .profileName("profile1")
            .resourceGroupName("RG")
            .secretName("secret1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const secret = new azure_native.cdn.Secret("secret", {
    parameters: {
        secretSource: {
            id: "/subscriptions/subid/resourcegroups/RG/providers/Microsoft.KeyVault/vault/kvName/secrets/certificatename",
        },
        secretVersion: "abcdef1234578900abcdef1234567890",
        type: "CustomerCertificate",
        useLatestVersion: false,
    },
    profileName: "profile1",
    resourceGroupName: "RG",
    secretName: "secret1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

secret = azure_native.cdn.Secret("secret",
    parameters=azure_native.cdn.CustomerCertificateParametersArgs(
        secret_source=azure_native.cdn.ResourceReferenceArgs(
            id="/subscriptions/subid/resourcegroups/RG/providers/Microsoft.KeyVault/vault/kvName/secrets/certificatename",
        ),
        secret_version="abcdef1234578900abcdef1234567890",
        type="CustomerCertificate",
        use_latest_version=False,
    ),
    profile_name="profile1",
    resource_group_name="RG",
    secret_name="secret1")

```

```yaml
resources:
  secret:
    type: azure-native:cdn:Secret
    properties:
      parameters:
        secretSource:
          id: /subscriptions/subid/resourcegroups/RG/providers/Microsoft.KeyVault/vault/kvName/secrets/certificatename
        secretVersion: abcdef1234578900abcdef1234567890
        type: CustomerCertificate
        useLatestVersion: false
      profileName: profile1
      resourceGroupName: RG
      secretName: secret1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:Secret secret1 /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/secrets/secret1 
```
