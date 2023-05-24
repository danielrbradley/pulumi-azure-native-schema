Role definition.
API Version: 2022-04-01.
Previous API Version: 2018-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create role definition
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleDefinition = new AzureNative.Authorization.RoleDefinition("roleDefinition", new()
    {
        RoleDefinitionId = "roleDefinitionId",
        Scope = "scope",
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
		_, err := authorization.NewRoleDefinition(ctx, "roleDefinition", &authorization.RoleDefinitionArgs{
			RoleDefinitionId: pulumi.String("roleDefinitionId"),
			Scope:            pulumi.String("scope"),
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
import com.pulumi.azurenative.authorization.RoleDefinition;
import com.pulumi.azurenative.authorization.RoleDefinitionArgs;
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
        var roleDefinition = new RoleDefinition("roleDefinition", RoleDefinitionArgs.builder()        
            .roleDefinitionId("roleDefinitionId")
            .scope("scope")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleDefinition = new azure_native.authorization.RoleDefinition("roleDefinition", {
    roleDefinitionId: "roleDefinitionId",
    scope: "scope",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_definition = azure_native.authorization.RoleDefinition("roleDefinition",
    role_definition_id="roleDefinitionId",
    scope="scope")

```

```yaml
resources:
  roleDefinition:
    type: azure-native:authorization:RoleDefinition
    properties:
      roleDefinitionId: roleDefinitionId
      scope: scope

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:RoleDefinition roleDefinitionId /subscriptions/subID/providers/Microsoft.Authorization/roleDefinitions/roleDefinitionId 
```
