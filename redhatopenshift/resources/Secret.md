Secret represents a secret.
API Version: 2022-09-04.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a Secret with the specified subscription, resource group and resource name.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var secret = new AzureNative.RedHatOpenShift.Secret("secret", new()
    {
        ChildResourceName = "childResourceName",
        ResourceGroupName = "resourceGroup",
        ResourceName = "resourceName",
    });

});


```

```go
package main

import (
	redhatopenshift "github.com/pulumi/pulumi-azure-native-sdk/redhatopenshift"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := redhatopenshift.NewSecret(ctx, "secret", &redhatopenshift.SecretArgs{
			ChildResourceName: pulumi.String("childResourceName"),
			ResourceGroupName: pulumi.String("resourceGroup"),
			ResourceName:      pulumi.String("resourceName"),
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
import com.pulumi.azurenative.redhatopenshift.Secret;
import com.pulumi.azurenative.redhatopenshift.SecretArgs;
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
            .childResourceName("childResourceName")
            .resourceGroupName("resourceGroup")
            .resourceName("resourceName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const secret = new azure_native.redhatopenshift.Secret("secret", {
    childResourceName: "childResourceName",
    resourceGroupName: "resourceGroup",
    resourceName: "resourceName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

secret = azure_native.redhatopenshift.Secret("secret",
    child_resource_name="childResourceName",
    resource_group_name="resourceGroup",
    resource_name_="resourceName")

```

```yaml
resources:
  secret:
    type: azure-native:redhatopenshift:Secret
    properties:
      childResourceName: childResourceName
      resourceGroupName: resourceGroup
      resourceName: resourceName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:redhatopenshift:Secret mySecret /subscriptions/subscriptionId/resourceGroups/resourceGroup/providers/Microsoft.RedHatOpenShift/OpenShiftClusters/resourceName/secret/mySecret 
```
