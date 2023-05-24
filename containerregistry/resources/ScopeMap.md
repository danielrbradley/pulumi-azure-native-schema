An object that represents a scope map for a container registry.
API Version: 2022-12-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ScopeMapCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scopeMap = new AzureNative.ContainerRegistry.ScopeMap("scopeMap", new()
    {
        Actions = new[]
        {
            "repositories/myrepository/contentWrite",
            "repositories/myrepository/delete",
        },
        Description = "Developer Scopes",
        RegistryName = "myRegistry",
        ResourceGroupName = "myResourceGroup",
        ScopeMapName = "myScopeMap",
    });

});


```

```go
package main

import (
	containerregistry "github.com/pulumi/pulumi-azure-native-sdk/containerregistry"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerregistry.NewScopeMap(ctx, "scopeMap", &containerregistry.ScopeMapArgs{
			Actions: pulumi.StringArray{
				pulumi.String("repositories/myrepository/contentWrite"),
				pulumi.String("repositories/myrepository/delete"),
			},
			Description:       pulumi.String("Developer Scopes"),
			RegistryName:      pulumi.String("myRegistry"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ScopeMapName:      pulumi.String("myScopeMap"),
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
import com.pulumi.azurenative.containerregistry.ScopeMap;
import com.pulumi.azurenative.containerregistry.ScopeMapArgs;
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
        var scopeMap = new ScopeMap("scopeMap", ScopeMapArgs.builder()        
            .actions(            
                "repositories/myrepository/contentWrite",
                "repositories/myrepository/delete")
            .description("Developer Scopes")
            .registryName("myRegistry")
            .resourceGroupName("myResourceGroup")
            .scopeMapName("myScopeMap")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scopeMap = new azure_native.containerregistry.ScopeMap("scopeMap", {
    actions: [
        "repositories/myrepository/contentWrite",
        "repositories/myrepository/delete",
    ],
    description: "Developer Scopes",
    registryName: "myRegistry",
    resourceGroupName: "myResourceGroup",
    scopeMapName: "myScopeMap",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scope_map = azure_native.containerregistry.ScopeMap("scopeMap",
    actions=[
        "repositories/myrepository/contentWrite",
        "repositories/myrepository/delete",
    ],
    description="Developer Scopes",
    registry_name="myRegistry",
    resource_group_name="myResourceGroup",
    scope_map_name="myScopeMap")

```

```yaml
resources:
  scopeMap:
    type: azure-native:containerregistry:ScopeMap
    properties:
      actions:
        - repositories/myrepository/contentWrite
        - repositories/myrepository/delete
      description: Developer Scopes
      registryName: myRegistry
      resourceGroupName: myResourceGroup
      scopeMapName: myScopeMap

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerregistry:ScopeMap myScopeMap /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.ContainerRegistry/registries/myRegistry/scopeMaps/myScopeMap 
```
