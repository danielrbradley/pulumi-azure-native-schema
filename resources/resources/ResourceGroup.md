Resource group information.
API Version: 2022-09-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a resource group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var resourceGroup = new AzureNative.Resources.ResourceGroup("resourceGroup", new()
    {
        Location = "eastus",
        ResourceGroupName = "my-resource-group",
    });

});


```

```go
package main

import (
	resources "github.com/pulumi/pulumi-azure-native-sdk/resources"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resources.NewResourceGroup(ctx, "resourceGroup", &resources.ResourceGroupArgs{
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("my-resource-group"),
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
import com.pulumi.azurenative.resources.ResourceGroup;
import com.pulumi.azurenative.resources.ResourceGroupArgs;
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
        var resourceGroup = new ResourceGroup("resourceGroup", ResourceGroupArgs.builder()        
            .location("eastus")
            .resourceGroupName("my-resource-group")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const resourceGroup = new azure_native.resources.ResourceGroup("resourceGroup", {
    location: "eastus",
    resourceGroupName: "my-resource-group",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

resource_group = azure_native.resources.ResourceGroup("resourceGroup",
    location="eastus",
    resource_group_name="my-resource-group")

```

```yaml
resources:
  resourceGroup:
    type: azure-native:resources:ResourceGroup
    properties:
      location: eastus
      resourceGroupName: my-resource-group

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resources:ResourceGroup my-resource-group /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/my-resource-group 
```
