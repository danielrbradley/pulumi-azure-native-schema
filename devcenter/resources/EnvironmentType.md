Represents an environment type.
API Version: 2022-11-11-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### EnvironmentTypes_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var environmentType = new AzureNative.DevCenter.EnvironmentType("environmentType", new()
    {
        DevCenterName = "Contoso",
        EnvironmentTypeName = "DevTest",
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "Owner", "superuser" },
        },
    });

});


```

```go
package main

import (
	devcenter "github.com/pulumi/pulumi-azure-native-sdk/devcenter"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devcenter.NewEnvironmentType(ctx, "environmentType", &devcenter.EnvironmentTypeArgs{
			DevCenterName:       pulumi.String("Contoso"),
			EnvironmentTypeName: pulumi.String("DevTest"),
			ResourceGroupName:   pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"Owner": pulumi.String("superuser"),
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
import com.pulumi.azurenative.devcenter.EnvironmentType;
import com.pulumi.azurenative.devcenter.EnvironmentTypeArgs;
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
        var environmentType = new EnvironmentType("environmentType", EnvironmentTypeArgs.builder()        
            .devCenterName("Contoso")
            .environmentTypeName("DevTest")
            .resourceGroupName("rg1")
            .tags(Map.of("Owner", "superuser"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const environmentType = new azure_native.devcenter.EnvironmentType("environmentType", {
    devCenterName: "Contoso",
    environmentTypeName: "DevTest",
    resourceGroupName: "rg1",
    tags: {
        Owner: "superuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

environment_type = azure_native.devcenter.EnvironmentType("environmentType",
    dev_center_name="Contoso",
    environment_type_name="DevTest",
    resource_group_name="rg1",
    tags={
        "Owner": "superuser",
    })

```

```yaml
resources:
  environmentType:
    type: azure-native:devcenter:EnvironmentType
    properties:
      devCenterName: Contoso
      environmentTypeName: DevTest
      resourceGroupName: rg1
      tags:
        Owner: superuser

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devcenter:EnvironmentType DevTest /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso/environmentTypes/DevTest 
```
