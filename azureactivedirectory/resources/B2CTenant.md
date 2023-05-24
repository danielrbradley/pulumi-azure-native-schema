
API Version: 2021-04-01.
Previous API Version: 2019-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create tenant
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var b2cTenant = new AzureNative.AzureActiveDirectory.B2CTenant("b2cTenant", new()
    {
        CountryCode = "US",
        DisplayName = "Contoso",
        Location = "United States",
        ResourceGroupName = "contosoResourceGroup",
        ResourceName = "contoso.onmicrosoft.com",
        Sku = new AzureNative.AzureActiveDirectory.Inputs.B2CResourceSKUArgs
        {
            Name = "Standard",
            Tier = "A0",
        },
    });

});


```

```go
package main

import (
	azureactivedirectory "github.com/pulumi/pulumi-azure-native-sdk/azureactivedirectory"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azureactivedirectory.NewB2CTenant(ctx, "b2cTenant", &azureactivedirectory.B2CTenantArgs{
			CountryCode:       pulumi.String("US"),
			DisplayName:       pulumi.String("Contoso"),
			Location:          pulumi.String("United States"),
			ResourceGroupName: pulumi.String("contosoResourceGroup"),
			ResourceName:      pulumi.String("contoso.onmicrosoft.com"),
			Sku: &azureactivedirectory.B2CResourceSKUArgs{
				Name: pulumi.String("Standard"),
				Tier: pulumi.String("A0"),
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
import com.pulumi.azurenative.azureactivedirectory.B2CTenant;
import com.pulumi.azurenative.azureactivedirectory.B2CTenantArgs;
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
        var b2cTenant = new B2CTenant("b2cTenant", B2CTenantArgs.builder()        
            .countryCode("US")
            .displayName("Contoso")
            .location("United States")
            .resourceGroupName("contosoResourceGroup")
            .resourceName("contoso.onmicrosoft.com")
            .sku(Map.ofEntries(
                Map.entry("name", "Standard"),
                Map.entry("tier", "A0")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const b2cTenant = new azure_native.azureactivedirectory.B2CTenant("b2cTenant", {
    countryCode: "US",
    displayName: "Contoso",
    location: "United States",
    resourceGroupName: "contosoResourceGroup",
    resourceName: "contoso.onmicrosoft.com",
    sku: {
        name: "Standard",
        tier: "A0",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

b2c_tenant = azure_native.azureactivedirectory.B2CTenant("b2cTenant",
    country_code="US",
    display_name="Contoso",
    location="United States",
    resource_group_name="contosoResourceGroup",
    resource_name_="contoso.onmicrosoft.com",
    sku=azure_native.azureactivedirectory.B2CResourceSKUArgs(
        name="Standard",
        tier="A0",
    ))

```

```yaml
resources:
  b2cTenant:
    type: azure-native:azureactivedirectory:B2CTenant
    properties:
      countryCode: US
      displayName: Contoso
      location: United States
      resourceGroupName: contosoResourceGroup
      resourceName: contoso.onmicrosoft.com
      sku:
        name: Standard
        tier: A0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azureactivedirectory:B2CTenant contoso.onmicrosoft.com /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/contosoResourceGroup/providers/Microsoft.AzureActiveDirectory/b2cDirectories/contoso.onmicrosoft.com 
```
