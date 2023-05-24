Specifies information about the gallery image definition that you want to create or update.
API Version: 2022-03-03.
Previous API Version: 2020-09-30. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a simple gallery image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var galleryImage = new AzureNative.Compute.GalleryImage("galleryImage", new()
    {
        GalleryImageName = "myGalleryImageName",
        GalleryName = "myGalleryName",
        HyperVGeneration = "V1",
        Identifier = new AzureNative.Compute.Inputs.GalleryImageIdentifierArgs
        {
            Offer = "myOfferName",
            Publisher = "myPublisherName",
            Sku = "mySkuName",
        },
        Location = "West US",
        OsState = AzureNative.Compute.OperatingSystemStateTypes.Generalized,
        OsType = AzureNative.Compute.OperatingSystemTypes.Windows,
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewGalleryImage(ctx, "galleryImage", &compute.GalleryImageArgs{
			GalleryImageName: pulumi.String("myGalleryImageName"),
			GalleryName:      pulumi.String("myGalleryName"),
			HyperVGeneration: pulumi.String("V1"),
			Identifier: &compute.GalleryImageIdentifierArgs{
				Offer:     pulumi.String("myOfferName"),
				Publisher: pulumi.String("myPublisherName"),
				Sku:       pulumi.String("mySkuName"),
			},
			Location:          pulumi.String("West US"),
			OsState:           compute.OperatingSystemStateTypesGeneralized,
			OsType:            compute.OperatingSystemTypesWindows,
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.GalleryImage;
import com.pulumi.azurenative.compute.GalleryImageArgs;
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
        var galleryImage = new GalleryImage("galleryImage", GalleryImageArgs.builder()        
            .galleryImageName("myGalleryImageName")
            .galleryName("myGalleryName")
            .hyperVGeneration("V1")
            .identifier(Map.ofEntries(
                Map.entry("offer", "myOfferName"),
                Map.entry("publisher", "myPublisherName"),
                Map.entry("sku", "mySkuName")
            ))
            .location("West US")
            .osState("Generalized")
            .osType("Windows")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const galleryImage = new azure_native.compute.GalleryImage("galleryImage", {
    galleryImageName: "myGalleryImageName",
    galleryName: "myGalleryName",
    hyperVGeneration: "V1",
    identifier: {
        offer: "myOfferName",
        publisher: "myPublisherName",
        sku: "mySkuName",
    },
    location: "West US",
    osState: azure_native.compute.OperatingSystemStateTypes.Generalized,
    osType: azure_native.compute.OperatingSystemTypes.Windows,
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gallery_image = azure_native.compute.GalleryImage("galleryImage",
    gallery_image_name="myGalleryImageName",
    gallery_name="myGalleryName",
    hyper_v_generation="V1",
    identifier=azure_native.compute.GalleryImageIdentifierArgs(
        offer="myOfferName",
        publisher="myPublisherName",
        sku="mySkuName",
    ),
    location="West US",
    os_state=azure_native.compute.OperatingSystemStateTypes.GENERALIZED,
    os_type=azure_native.compute.OperatingSystemTypes.WINDOWS,
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  galleryImage:
    type: azure-native:compute:GalleryImage
    properties:
      galleryImageName: myGalleryImageName
      galleryName: myGalleryName
      hyperVGeneration: V1
      identifier:
        offer: myOfferName
        publisher: myPublisherName
        sku: mySkuName
      location: West US
      osState: Generalized
      osType: Windows
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:GalleryImage myGalleryImageName /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/galleries/{galleryName}/images/{galleryImageName} 
```
