Represents a definition for a Developer Machine.
API Version: 2022-11-11-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DevBoxDefinitions_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var devBoxDefinition = new AzureNative.DevCenter.DevBoxDefinition("devBoxDefinition", new()
    {
        DevBoxDefinitionName = "WebDevBox",
        DevCenterName = "Contoso",
        HibernateSupport = "Enabled",
        ImageReference = new AzureNative.DevCenter.Inputs.ImageReferenceArgs
        {
            Id = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.DevCenter/devcenters/Contoso/galleries/contosogallery/images/exampleImage/version/1.0.0",
        },
        Location = "centralus",
        OsStorageType = "SSD_1024",
        ResourceGroupName = "rg1",
        Sku = new AzureNative.DevCenter.Inputs.SkuArgs
        {
            Name = "Preview",
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
		_, err := devcenter.NewDevBoxDefinition(ctx, "devBoxDefinition", &devcenter.DevBoxDefinitionArgs{
			DevBoxDefinitionName: pulumi.String("WebDevBox"),
			DevCenterName:        pulumi.String("Contoso"),
			HibernateSupport:     pulumi.String("Enabled"),
			ImageReference: &devcenter.ImageReferenceArgs{
				Id: pulumi.String("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.DevCenter/devcenters/Contoso/galleries/contosogallery/images/exampleImage/version/1.0.0"),
			},
			Location:          pulumi.String("centralus"),
			OsStorageType:     pulumi.String("SSD_1024"),
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &devcenter.SkuArgs{
				Name: pulumi.String("Preview"),
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
import com.pulumi.azurenative.devcenter.DevBoxDefinition;
import com.pulumi.azurenative.devcenter.DevBoxDefinitionArgs;
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
        var devBoxDefinition = new DevBoxDefinition("devBoxDefinition", DevBoxDefinitionArgs.builder()        
            .devBoxDefinitionName("WebDevBox")
            .devCenterName("Contoso")
            .hibernateSupport("Enabled")
            .imageReference(Map.of("id", "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.DevCenter/devcenters/Contoso/galleries/contosogallery/images/exampleImage/version/1.0.0"))
            .location("centralus")
            .osStorageType("SSD_1024")
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Preview"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const devBoxDefinition = new azure_native.devcenter.DevBoxDefinition("devBoxDefinition", {
    devBoxDefinitionName: "WebDevBox",
    devCenterName: "Contoso",
    hibernateSupport: "Enabled",
    imageReference: {
        id: "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.DevCenter/devcenters/Contoso/galleries/contosogallery/images/exampleImage/version/1.0.0",
    },
    location: "centralus",
    osStorageType: "SSD_1024",
    resourceGroupName: "rg1",
    sku: {
        name: "Preview",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dev_box_definition = azure_native.devcenter.DevBoxDefinition("devBoxDefinition",
    dev_box_definition_name="WebDevBox",
    dev_center_name="Contoso",
    hibernate_support="Enabled",
    image_reference=azure_native.devcenter.ImageReferenceArgs(
        id="/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.DevCenter/devcenters/Contoso/galleries/contosogallery/images/exampleImage/version/1.0.0",
    ),
    location="centralus",
    os_storage_type="SSD_1024",
    resource_group_name="rg1",
    sku=azure_native.devcenter.SkuArgs(
        name="Preview",
    ))

```

```yaml
resources:
  devBoxDefinition:
    type: azure-native:devcenter:DevBoxDefinition
    properties:
      devBoxDefinitionName: WebDevBox
      devCenterName: Contoso
      hibernateSupport: Enabled
      imageReference:
        id: /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.DevCenter/devcenters/Contoso/galleries/contosogallery/images/exampleImage/version/1.0.0
      location: centralus
      osStorageType: SSD_1024
      resourceGroupName: rg1
      sku:
        name: Preview

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devcenter:DevBoxDefinition WebDevBox /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso/devboxdefinitions/devBoxDefinitionName 
```
