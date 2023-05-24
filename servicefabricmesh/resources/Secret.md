This type describes a secret resource.
API Version: 2018-09-01-preview.
Previous API Version: 2018-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdateSecret
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var secret = new AzureNative.ServiceFabricMesh.Secret("secret", new()
    {
        Location = "EastUS",
        Properties = null,
        ResourceGroupName = "sbz_demo",
        SecretResourceName = "dbConnectionString",
        Tags = null,
    });

});


```

```go
package main

import (
	servicefabricmesh "github.com/pulumi/pulumi-azure-native-sdk/servicefabricmesh"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabricmesh.NewSecret(ctx, "secret", &servicefabricmesh.SecretArgs{
			Location:           pulumi.String("EastUS"),
			Properties:         nil,
			ResourceGroupName:  pulumi.String("sbz_demo"),
			SecretResourceName: pulumi.String("dbConnectionString"),
			Tags:               nil,
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
import com.pulumi.azurenative.servicefabricmesh.Secret;
import com.pulumi.azurenative.servicefabricmesh.SecretArgs;
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
            .location("EastUS")
            .properties()
            .resourceGroupName("sbz_demo")
            .secretResourceName("dbConnectionString")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const secret = new azure_native.servicefabricmesh.Secret("secret", {
    location: "EastUS",
    properties: {},
    resourceGroupName: "sbz_demo",
    secretResourceName: "dbConnectionString",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

secret = azure_native.servicefabricmesh.Secret("secret",
    location="EastUS",
    properties=azure_native.servicefabricmesh.SecretResourcePropertiesArgs(),
    resource_group_name="sbz_demo",
    secret_resource_name="dbConnectionString",
    tags={})

```

```yaml
resources:
  secret:
    type: azure-native:servicefabricmesh:Secret
    properties:
      location: EastUS
      properties: {}
      resourceGroupName: sbz_demo
      secretResourceName: dbConnectionString
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicefabricmesh:Secret dbConnectionString /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/sbz_demo/providers/Microsoft.ServiceFabricMesh/secrets/dbConnectionString 
```
