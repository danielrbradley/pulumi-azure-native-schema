
API Version: 2020-05-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Resource Management Private Link.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var resourceManagementPrivateLink = new AzureNative.Authorization.ResourceManagementPrivateLink("resourceManagementPrivateLink", new()
    {
        Location = "eastus",
        ResourceGroupName = "my-resource-group",
        RmplName = "my-rmplName",
    });

});


```

```go
package main

import (
	authorization "github.com/pulumi/pulumi-azure-native-sdk/authorization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := authorization.NewResourceManagementPrivateLink(ctx, "resourceManagementPrivateLink", &authorization.ResourceManagementPrivateLinkArgs{
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("my-resource-group"),
			RmplName:          pulumi.String("my-rmplName"),
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
import com.pulumi.azurenative.authorization.ResourceManagementPrivateLink;
import com.pulumi.azurenative.authorization.ResourceManagementPrivateLinkArgs;
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
        var resourceManagementPrivateLink = new ResourceManagementPrivateLink("resourceManagementPrivateLink", ResourceManagementPrivateLinkArgs.builder()        
            .location("eastus")
            .resourceGroupName("my-resource-group")
            .rmplName("my-rmplName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const resourceManagementPrivateLink = new azure_native.authorization.ResourceManagementPrivateLink("resourceManagementPrivateLink", {
    location: "eastus",
    resourceGroupName: "my-resource-group",
    rmplName: "my-rmplName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

resource_management_private_link = azure_native.authorization.ResourceManagementPrivateLink("resourceManagementPrivateLink",
    location="eastus",
    resource_group_name="my-resource-group",
    rmpl_name="my-rmplName")

```

```yaml
resources:
  resourceManagementPrivateLink:
    type: azure-native:authorization:ResourceManagementPrivateLink
    properties:
      location: eastus
      resourceGroupName: my-resource-group
      rmplName: my-rmplName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:ResourceManagementPrivateLink my-pla 00000000-0000-0000-0000-000000000000 
```
