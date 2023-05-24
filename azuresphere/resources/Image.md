An image resource belonging to a catalog resource.
API Version: 2022-09-01-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Image_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var image = new AzureNative.AzureSphere.Image("image", new()
    {
        CatalogName = "MyCatalog1",
        Image = "bXliYXNlNjRzdHJpbmc=",
        ImageName = "default",
        ResourceGroupName = "MyResourceGroup1",
    });

});


```

```go
package main

import (
	azuresphere "github.com/pulumi/pulumi-azure-native-sdk/azuresphere"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azuresphere.NewImage(ctx, "image", &azuresphere.ImageArgs{
			CatalogName:       pulumi.String("MyCatalog1"),
			Image:             pulumi.String("bXliYXNlNjRzdHJpbmc="),
			ImageName:         pulumi.String("default"),
			ResourceGroupName: pulumi.String("MyResourceGroup1"),
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
import com.pulumi.azurenative.azuresphere.Image;
import com.pulumi.azurenative.azuresphere.ImageArgs;
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
        var image = new Image("image", ImageArgs.builder()        
            .catalogName("MyCatalog1")
            .image("bXliYXNlNjRzdHJpbmc=")
            .imageName("default")
            .resourceGroupName("MyResourceGroup1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const image = new azure_native.azuresphere.Image("image", {
    catalogName: "MyCatalog1",
    image: "bXliYXNlNjRzdHJpbmc=",
    imageName: "default",
    resourceGroupName: "MyResourceGroup1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

image = azure_native.azuresphere.Image("image",
    catalog_name="MyCatalog1",
    image="bXliYXNlNjRzdHJpbmc=",
    image_name="default",
    resource_group_name="MyResourceGroup1")

```

```yaml
resources:
  image:
    type: azure-native:azuresphere:Image
    properties:
      catalogName: MyCatalog1
      image: bXliYXNlNjRzdHJpbmc=
      imageName: default
      resourceGroupName: MyResourceGroup1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azuresphere:Image MyProduct1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MyResourceGroup1/providers/Microsoft.AzureSphere/catalogs/MyCatalog1/images/default 
```
