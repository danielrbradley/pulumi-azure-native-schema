Account resource details.
API Version: 2022-02-01.
Previous API Version: 2022-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update RecommendationsService Account resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.RecommendationsService.Account("account", new()
    {
        AccountName = "sampleAccount",
        Location = "West US",
        Properties = new AzureNative.RecommendationsService.Inputs.AccountResourcePropertiesArgs
        {
            Configuration = "Capacity",
            EndpointAuthentications = new[]
            {
                new AzureNative.RecommendationsService.Inputs.EndpointAuthenticationArgs
                {
                    AadTenantID = "tenant",
                    PrincipalID = "oid",
                    PrincipalType = "User",
                },
            },
        },
        ResourceGroupName = "rg",
        Tags = 
        {
            { "Environment", "Prod" },
        },
    });

});


```

```go
package main

import (
	recommendationsservice "github.com/pulumi/pulumi-azure-native-sdk/recommendationsservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recommendationsservice.NewAccount(ctx, "account", &recommendationsservice.AccountArgs{
			AccountName: pulumi.String("sampleAccount"),
			Location:    pulumi.String("West US"),
			Properties: recommendationsservice.AccountResourceResponseProperties{
				Configuration: pulumi.String("Capacity"),
				EndpointAuthentications: recommendationsservice.EndpointAuthenticationArray{
					&recommendationsservice.EndpointAuthenticationArgs{
						AadTenantID:   pulumi.String("tenant"),
						PrincipalID:   pulumi.String("oid"),
						PrincipalType: pulumi.String("User"),
					},
				},
			},
			ResourceGroupName: pulumi.String("rg"),
			Tags: pulumi.StringMap{
				"Environment": pulumi.String("Prod"),
			},
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
import com.pulumi.azurenative.recommendationsservice.Account;
import com.pulumi.azurenative.recommendationsservice.AccountArgs;
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
        var account = new Account("account", AccountArgs.builder()        
            .accountName("sampleAccount")
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("configuration", "Capacity"),
                Map.entry("endpointAuthentications", Map.ofEntries(
                    Map.entry("aadTenantID", "tenant"),
                    Map.entry("principalID", "oid"),
                    Map.entry("principalType", "User")
                ))
            ))
            .resourceGroupName("rg")
            .tags(Map.of("Environment", "Prod"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.recommendationsservice.Account("account", {
    accountName: "sampleAccount",
    location: "West US",
    properties: {
        configuration: "Capacity",
        endpointAuthentications: [{
            aadTenantID: "tenant",
            principalID: "oid",
            principalType: "User",
        }],
    },
    resourceGroupName: "rg",
    tags: {
        Environment: "Prod",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.recommendationsservice.Account("account",
    account_name="sampleAccount",
    location="West US",
    properties=azure_native.recommendationsservice.AccountResourceResponsePropertiesArgs(
        configuration="Capacity",
        endpoint_authentications=[azure_native.recommendationsservice.EndpointAuthenticationArgs(
            aad_tenant_id="tenant",
            principal_id="oid",
            principal_type="User",
        )],
    ),
    resource_group_name="rg",
    tags={
        "Environment": "Prod",
    })

```

```yaml
resources:
  account:
    type: azure-native:recommendationsservice:Account
    properties:
      accountName: sampleAccount
      location: West US
      properties:
        configuration: Capacity
        endpointAuthentications:
          - aadTenantID: tenant
            principalID: oid
            principalType: User
      resourceGroupName: rg
      tags:
        Environment: Prod

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recommendationsservice:Account sampleAccount /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/rg/providers/Microsoft.RecommendationsService/accounts/sampleAccount 
```
