Identity Provider details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateIdentityProvider
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var identityProvider = new AzureNative.ApiManagement.IdentityProvider("identityProvider", new()
    {
        ClientId = "facebookid",
        ClientSecret = "facebookapplicationsecret",
        IdentityProviderName = "facebook",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewIdentityProvider(ctx, "identityProvider", &apimanagement.IdentityProviderArgs{
			ClientId:             pulumi.String("facebookid"),
			ClientSecret:         pulumi.String("facebookapplicationsecret"),
			IdentityProviderName: pulumi.String("facebook"),
			ResourceGroupName:    pulumi.String("rg1"),
			ServiceName:          pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.IdentityProvider;
import com.pulumi.azurenative.apimanagement.IdentityProviderArgs;
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
        var identityProvider = new IdentityProvider("identityProvider", IdentityProviderArgs.builder()        
            .clientId("facebookid")
            .clientSecret("facebookapplicationsecret")
            .identityProviderName("facebook")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const identityProvider = new azure_native.apimanagement.IdentityProvider("identityProvider", {
    clientId: "facebookid",
    clientSecret: "facebookapplicationsecret",
    identityProviderName: "facebook",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

identity_provider = azure_native.apimanagement.IdentityProvider("identityProvider",
    client_id="facebookid",
    client_secret="facebookapplicationsecret",
    identity_provider_name="facebook",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  identityProvider:
    type: azure-native:apimanagement:IdentityProvider
    properties:
      clientId: facebookid
      clientSecret: facebookapplicationsecret
      identityProviderName: facebook
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:IdentityProvider Facebook /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/identityProviders/Facebook 
```
