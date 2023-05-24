Information about managed application definition.
API Version: 2021-07-01.
Previous API Version: 2019-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update managed application definition
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var applicationDefinition = new AzureNative.Solutions.ApplicationDefinition("applicationDefinition", new()
    {
        ApplicationDefinitionName = "myManagedApplicationDef",
        Authorizations = new[]
        {
            new AzureNative.Solutions.Inputs.ApplicationAuthorizationArgs
            {
                PrincipalId = "validprincipalguid",
                RoleDefinitionId = "validroleguid",
            },
        },
        Description = "myManagedApplicationDef description",
        DisplayName = "myManagedApplicationDef",
        LockLevel = AzureNative.Solutions.ApplicationLockLevel.None,
        PackageFileUri = "https://path/to/packagezipfile",
        ResourceGroupName = "rg",
    });

});


```

```go
package main

import (
	solutions "github.com/pulumi/pulumi-azure-native-sdk/solutions"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := solutions.NewApplicationDefinition(ctx, "applicationDefinition", &solutions.ApplicationDefinitionArgs{
			ApplicationDefinitionName: pulumi.String("myManagedApplicationDef"),
			Authorizations: []solutions.ApplicationAuthorizationArgs{
				{
					PrincipalId:      pulumi.String("validprincipalguid"),
					RoleDefinitionId: pulumi.String("validroleguid"),
				},
			},
			Description:       pulumi.String("myManagedApplicationDef description"),
			DisplayName:       pulumi.String("myManagedApplicationDef"),
			LockLevel:         solutions.ApplicationLockLevelNone,
			PackageFileUri:    pulumi.String("https://path/to/packagezipfile"),
			ResourceGroupName: pulumi.String("rg"),
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
import com.pulumi.azurenative.solutions.ApplicationDefinition;
import com.pulumi.azurenative.solutions.ApplicationDefinitionArgs;
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
        var applicationDefinition = new ApplicationDefinition("applicationDefinition", ApplicationDefinitionArgs.builder()        
            .applicationDefinitionName("myManagedApplicationDef")
            .authorizations(Map.ofEntries(
                Map.entry("principalId", "validprincipalguid"),
                Map.entry("roleDefinitionId", "validroleguid")
            ))
            .description("myManagedApplicationDef description")
            .displayName("myManagedApplicationDef")
            .lockLevel("None")
            .packageFileUri("https://path/to/packagezipfile")
            .resourceGroupName("rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const applicationDefinition = new azure_native.solutions.ApplicationDefinition("applicationDefinition", {
    applicationDefinitionName: "myManagedApplicationDef",
    authorizations: [{
        principalId: "validprincipalguid",
        roleDefinitionId: "validroleguid",
    }],
    description: "myManagedApplicationDef description",
    displayName: "myManagedApplicationDef",
    lockLevel: azure_native.solutions.ApplicationLockLevel.None,
    packageFileUri: "https://path/to/packagezipfile",
    resourceGroupName: "rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application_definition = azure_native.solutions.ApplicationDefinition("applicationDefinition",
    application_definition_name="myManagedApplicationDef",
    authorizations=[azure_native.solutions.ApplicationAuthorizationArgs(
        principal_id="validprincipalguid",
        role_definition_id="validroleguid",
    )],
    description="myManagedApplicationDef description",
    display_name="myManagedApplicationDef",
    lock_level=azure_native.solutions.ApplicationLockLevel.NONE,
    package_file_uri="https://path/to/packagezipfile",
    resource_group_name="rg")

```

```yaml
resources:
  applicationDefinition:
    type: azure-native:solutions:ApplicationDefinition
    properties:
      applicationDefinitionName: myManagedApplicationDef
      authorizations:
        - principalId: validprincipalguid
          roleDefinitionId: validroleguid
      description: myManagedApplicationDef description
      displayName: myManagedApplicationDef
      lockLevel: None
      packageFileUri: https://path/to/packagezipfile
      resourceGroupName: rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:solutions:ApplicationDefinition myManagedApplicationDef /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Solutions/applicationDefinitions/myManagedApplicationDef 
```
