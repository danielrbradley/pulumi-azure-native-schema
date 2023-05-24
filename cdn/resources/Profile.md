A profile is a logical grouping of endpoints that share the same settings.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Profiles_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var profile = new AzureNative.Cdn.Profile("profile", new()
    {
        Location = "global",
        ProfileName = "profile1",
        ResourceGroupName = "RG",
        Sku = new AzureNative.Cdn.Inputs.SkuArgs
        {
            Name = "Premium_AzureFrontDoor",
        },
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
		_, err := cdn.NewProfile(ctx, "profile", &cdn.ProfileArgs{
			Location:          pulumi.String("global"),
			ProfileName:       pulumi.String("profile1"),
			ResourceGroupName: pulumi.String("RG"),
			Sku: &cdn.SkuArgs{
				Name: pulumi.String("Premium_AzureFrontDoor"),
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
import com.pulumi.azurenative.cdn.Profile;
import com.pulumi.azurenative.cdn.ProfileArgs;
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
        var profile = new Profile("profile", ProfileArgs.builder()        
            .location("global")
            .profileName("profile1")
            .resourceGroupName("RG")
            .sku(Map.of("name", "Premium_AzureFrontDoor"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const profile = new azure_native.cdn.Profile("profile", {
    location: "global",
    profileName: "profile1",
    resourceGroupName: "RG",
    sku: {
        name: "Premium_AzureFrontDoor",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

profile = azure_native.cdn.Profile("profile",
    location="global",
    profile_name="profile1",
    resource_group_name="RG",
    sku=azure_native.cdn.SkuArgs(
        name="Premium_AzureFrontDoor",
    ))

```

```yaml
resources:
  profile:
    type: azure-native:cdn:Profile
    properties:
      location: global
      profileName: profile1
      resourceGroupName: RG
      sku:
        name: Premium_AzureFrontDoor

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:Profile profile1 /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1 
```
