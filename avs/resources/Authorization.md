ExpressRoute Circuit Authorization
API Version: 2022-05-01.
Previous API Version: 2020-03-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Authorizations_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var authorization = new AzureNative.AVS.Authorization("authorization", new()
    {
        AuthorizationName = "authorization1",
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewAuthorization(ctx, "authorization", &avs.AuthorizationArgs{
			AuthorizationName: pulumi.String("authorization1"),
			PrivateCloudName:  pulumi.String("cloud1"),
			ResourceGroupName: pulumi.String("group1"),
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
import com.pulumi.azurenative.avs.Authorization;
import com.pulumi.azurenative.avs.AuthorizationArgs;
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
        var authorization = new Authorization("authorization", AuthorizationArgs.builder()        
            .authorizationName("authorization1")
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const authorization = new azure_native.avs.Authorization("authorization", {
    authorizationName: "authorization1",
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

authorization = azure_native.avs.Authorization("authorization",
    authorization_name="authorization1",
    private_cloud_name="cloud1",
    resource_group_name="group1")

```

```yaml
resources:
  authorization:
    type: azure-native:avs:Authorization
    properties:
      authorizationName: authorization1
      privateCloudName: cloud1
      resourceGroupName: group1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:Authorization authorization1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/authorizations/authorization1 
```
