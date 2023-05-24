Guest Usages Resource
API Version: 2021-04-01.
Previous API Version: 2020-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### GuestUsages_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var guestUsage = new AzureNative.AzureActiveDirectory.GuestUsage("guestUsage", new()
    {
        ResourceGroupName = "contosoResourceGroup",
        ResourceName = "contoso.onmicrosoft.com",
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
		_, err := azureactivedirectory.NewGuestUsage(ctx, "guestUsage", &azureactivedirectory.GuestUsageArgs{
			ResourceGroupName: pulumi.String("contosoResourceGroup"),
			ResourceName:      pulumi.String("contoso.onmicrosoft.com"),
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
import com.pulumi.azurenative.azureactivedirectory.GuestUsage;
import com.pulumi.azurenative.azureactivedirectory.GuestUsageArgs;
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
        var guestUsage = new GuestUsage("guestUsage", GuestUsageArgs.builder()        
            .resourceGroupName("contosoResourceGroup")
            .resourceName("contoso.onmicrosoft.com")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const guestUsage = new azure_native.azureactivedirectory.GuestUsage("guestUsage", {
    resourceGroupName: "contosoResourceGroup",
    resourceName: "contoso.onmicrosoft.com",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

guest_usage = azure_native.azureactivedirectory.GuestUsage("guestUsage",
    resource_group_name="contosoResourceGroup",
    resource_name_="contoso.onmicrosoft.com")

```

```yaml
resources:
  guestUsage:
    type: azure-native:azureactivedirectory:GuestUsage
    properties:
      resourceGroupName: contosoResourceGroup
      resourceName: contoso.onmicrosoft.com

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azureactivedirectory:GuestUsage contoso.onmicrosoft.com /subscriptions/c80fb759-c965-4c6a-9110-9b2b2d038882/resourceGroups/contosoResourceGroup/providers/Microsoft.AzureActiveDirectory/guestUsages/contoso.onmicrosoft.com 
```
