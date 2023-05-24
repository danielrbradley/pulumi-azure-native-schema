The resource definition of this association.
API Version: 2018-09-01-preview.
Previous API Version: 2018-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an association
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var association = new AzureNative.CustomProviders.Association("association", new()
    {
        AssociationName = "associationName",
        Scope = "scope",
        TargetResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/appRG/providers/Microsoft.Solutions/applications/applicationName",
    });

});


```

```go
package main

import (
	customproviders "github.com/pulumi/pulumi-azure-native-sdk/customproviders"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := customproviders.NewAssociation(ctx, "association", &customproviders.AssociationArgs{
			AssociationName:  pulumi.String("associationName"),
			Scope:            pulumi.String("scope"),
			TargetResourceId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/appRG/providers/Microsoft.Solutions/applications/applicationName"),
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
import com.pulumi.azurenative.customproviders.Association;
import com.pulumi.azurenative.customproviders.AssociationArgs;
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
        var association = new Association("association", AssociationArgs.builder()        
            .associationName("associationName")
            .scope("scope")
            .targetResourceId("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/appRG/providers/Microsoft.Solutions/applications/applicationName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const association = new azure_native.customproviders.Association("association", {
    associationName: "associationName",
    scope: "scope",
    targetResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/appRG/providers/Microsoft.Solutions/applications/applicationName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

association = azure_native.customproviders.Association("association",
    association_name="associationName",
    scope="scope",
    target_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/appRG/providers/Microsoft.Solutions/applications/applicationName")

```

```yaml
resources:
  association:
    type: azure-native:customproviders:Association
    properties:
      associationName: associationName
      scope: scope
      targetResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/appRG/providers/Microsoft.Solutions/applications/applicationName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customproviders:Association associationName /scope/providers/Microsoft.CustomProviders/associations/associationName 
```
