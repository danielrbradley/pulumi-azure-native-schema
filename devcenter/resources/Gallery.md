Represents a gallery.
API Version: 2022-11-11-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Galleries_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gallery = new AzureNative.DevCenter.Gallery("gallery", new()
    {
        DevCenterName = "Contoso",
        GalleryName = "StandardGallery",
        GalleryResourceId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.Compute/galleries/StandardGallery",
        ResourceGroupName = "rg1",
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
		_, err := devcenter.NewGallery(ctx, "gallery", &devcenter.GalleryArgs{
			DevCenterName:     pulumi.String("Contoso"),
			GalleryName:       pulumi.String("StandardGallery"),
			GalleryResourceId: pulumi.String("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.Compute/galleries/StandardGallery"),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.devcenter.Gallery;
import com.pulumi.azurenative.devcenter.GalleryArgs;
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
        var gallery = new Gallery("gallery", GalleryArgs.builder()        
            .devCenterName("Contoso")
            .galleryName("StandardGallery")
            .galleryResourceId("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.Compute/galleries/StandardGallery")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gallery = new azure_native.devcenter.Gallery("gallery", {
    devCenterName: "Contoso",
    galleryName: "StandardGallery",
    galleryResourceId: "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.Compute/galleries/StandardGallery",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery = azure_native.devcenter.Gallery("gallery",
    dev_center_name="Contoso",
    gallery_name="StandardGallery",
    gallery_resource_id="/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.Compute/galleries/StandardGallery",
    resource_group_name="rg1")

```

```yaml
resources:
  gallery:
    type: azure-native:devcenter:Gallery
    properties:
      devCenterName: Contoso
      galleryName: StandardGallery
      galleryResourceId: /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.Compute/galleries/StandardGallery
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devcenter:Gallery StandardGallery /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/devcenters/Contoso/galleries/StandardGallery 
```
