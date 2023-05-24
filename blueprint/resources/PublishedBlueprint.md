Represents a published blueprint.
API Version: 2018-11-01-preview.
Previous API Version: 2018-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PublishedManagementGroupBlueprint_Publish
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var publishedBlueprint = new AzureNative.Blueprint.PublishedBlueprint("publishedBlueprint", new()
    {
        BlueprintName = "simpleBlueprint",
        ResourceScope = "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
        VersionId = "v2",
    });

});


```

```go
package main

import (
	blueprint "github.com/pulumi/pulumi-azure-native-sdk/blueprint"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := blueprint.NewPublishedBlueprint(ctx, "publishedBlueprint", &blueprint.PublishedBlueprintArgs{
			BlueprintName: pulumi.String("simpleBlueprint"),
			ResourceScope: pulumi.String("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup"),
			VersionId:     pulumi.String("v2"),
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
import com.pulumi.azurenative.blueprint.PublishedBlueprint;
import com.pulumi.azurenative.blueprint.PublishedBlueprintArgs;
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
        var publishedBlueprint = new PublishedBlueprint("publishedBlueprint", PublishedBlueprintArgs.builder()        
            .blueprintName("simpleBlueprint")
            .resourceScope("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")
            .versionId("v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const publishedBlueprint = new azure_native.blueprint.PublishedBlueprint("publishedBlueprint", {
    blueprintName: "simpleBlueprint",
    resourceScope: "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
    versionId: "v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

published_blueprint = azure_native.blueprint.PublishedBlueprint("publishedBlueprint",
    blueprint_name="simpleBlueprint",
    resource_scope="providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
    version_id="v2")

```

```yaml
resources:
  publishedBlueprint:
    type: azure-native:blueprint:PublishedBlueprint
    properties:
      blueprintName: simpleBlueprint
      resourceScope: providers/Microsoft.Management/managementGroups/ContosoOnlineGroup
      versionId: v2

```

{{% /example %}}
{{% example %}}
### PublishedSubscriptionBlueprint_Publish
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var publishedBlueprint = new AzureNative.Blueprint.PublishedBlueprint("publishedBlueprint", new()
    {
        BlueprintName = "simpleBlueprint",
        ResourceScope = "subscriptions/00000000-0000-0000-0000-000000000000",
        VersionId = "v2",
    });

});


```

```go
package main

import (
	blueprint "github.com/pulumi/pulumi-azure-native-sdk/blueprint"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := blueprint.NewPublishedBlueprint(ctx, "publishedBlueprint", &blueprint.PublishedBlueprintArgs{
			BlueprintName: pulumi.String("simpleBlueprint"),
			ResourceScope: pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000"),
			VersionId:     pulumi.String("v2"),
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
import com.pulumi.azurenative.blueprint.PublishedBlueprint;
import com.pulumi.azurenative.blueprint.PublishedBlueprintArgs;
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
        var publishedBlueprint = new PublishedBlueprint("publishedBlueprint", PublishedBlueprintArgs.builder()        
            .blueprintName("simpleBlueprint")
            .resourceScope("subscriptions/00000000-0000-0000-0000-000000000000")
            .versionId("v2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const publishedBlueprint = new azure_native.blueprint.PublishedBlueprint("publishedBlueprint", {
    blueprintName: "simpleBlueprint",
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
    versionId: "v2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

published_blueprint = azure_native.blueprint.PublishedBlueprint("publishedBlueprint",
    blueprint_name="simpleBlueprint",
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000",
    version_id="v2")

```

```yaml
resources:
  publishedBlueprint:
    type: azure-native:blueprint:PublishedBlueprint
    properties:
      blueprintName: simpleBlueprint
      resourceScope: subscriptions/00000000-0000-0000-0000-000000000000
      versionId: v2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:blueprint:PublishedBlueprint v2 /subscriptions/00000000-0000-0000-0000-000000000000/providers/Microsoft.Blueprint/blueprints/simpleBlueprint 
```
